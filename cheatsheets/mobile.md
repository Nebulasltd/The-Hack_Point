# Mobile Vulnerability Assessment Cheat Sheet

Scope note: only test apps/devices you own or are authorized to assess. Dynamic instrumentation generally needs a rooted Android device/emulator or a jailbroken iOS device (or a non-jailbroken setup via objection's patching for basic cases).

## Recon: get the APK / IPA

```
adb shell pm list packages | grep <keyword>          # find the package name on device
adb shell pm path <package.name>                       # locate the APK path on device
adb pull <path/to/base.apk> ./app.apk                   # pull it off the device

# From an iOS device (jailbroken) or extracted IPA, unzip the .ipa like a zip file
```

## Static analysis

```
# MobSF (run as a local web service, then upload the APK/IPA via the UI or API)
docker run -it -p 8000:8000 opensecurity/mobile-security-framework-mobsf:latest

# Decompile for reading Java-ish source
jadx -d out_dir app.apk

# Unpack for reading smali / resources / manifest
apktool d app.apk -o app_decoded

# Quick manifest checks worth doing by hand
grep -A2 "android:exported" app_decoded/AndroidManifest.xml
grep "android:debuggable\|android:allowBackup" app_decoded/AndroidManifest.xml
```

Things to check in the manifest: `android:debuggable="true"` (should never ship), `android:allowBackup="true"` (data may be extractable via adb backup), exported activities/services/receivers/providers without permission checks, cleartext traffic settings (`android:usesCleartextTraffic`), and broad `intent-filter` exposure.

## Dynamic analysis (Frida / objection)

```
frida-ps -Uai                                    # list installed apps on connected device
objection -g <package.name> explore                # attach and drop into an interactive shell

# Inside objection:
android sslpinning disable            # bypass common SSL pinning implementations
android root disable                  # bypass common root-detection checks
android hooking list classes          # enumerate loaded classes
android hooking watch class_method <Class.method>   # trace calls, args, return values
memory dump all                        # dump process memory for string/secret hunting
```

For custom pinning implementations Frida bypasses don't catch, write a small hook script and load it with `frida -U -f <package.name> -l bypass.js`.

## IPC / attack surface (Drozer, Android)

```
adb forward tcp:31415 tcp:31415
drozer console connect

# Inside drozer:
run app.package.attacksurface <package.name>        # exported components summary
run app.activity.info -a <package.name>               # exported activities
run app.provider.info -a <package.name>                # content providers
run app.provider.query content://<provider_uri>         # query an exposed provider
run scanner.provider.injection -a <package.name>        # SQL injection in providers
```

## Traffic interception

```
# Point the device's Wi-Fi proxy at your Burp/mitmproxy/Charles host:port,
# then install the proxy's CA cert on the device.

# Android 7+ ignores user-installed CAs by default unless the app opts in via
# network_security_config.xml — for testing, repackage with a config that trusts
# user certs, or use objection's sslpinning disable / a Frida universal unpinning script.
```

## Local storage / data-at-rest checks

```
adb shell run-as <package.name> ls -la /data/data/<package.name>/
adb shell run-as <package.name> cat /data/data/<package.name>/shared_prefs/*.xml
adb backup -f backup.ab <package.name>            # if allowBackup=true, data may be extractable

# SQLite databases found under /data/data/<pkg>/databases/ — pull and inspect with any sqlite3 client
```

## Reference

- [OWASP MASTG](https://mas.owasp.org/MASTG/) — full testing methodology this sheet summarizes
- [OWASP Mobile Top 10](https://owasp.org/www-project-mobile-top-10/) — current top risk categories
- [MobSF documentation](https://mobsf.github.io/docs/) 
- [Frida CodeShare](https://codeshare.frida.re/) — community hook/bypass scripts

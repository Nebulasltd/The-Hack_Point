# Nmap Cheat Sheet

## Host discovery

```
nmap -sn 10.10.10.0/24            # ping sweep, no port scan
nmap -PR 10.10.10.0/24            # ARP scan (local network only)
```

## Port scanning

```
nmap -p- --min-rate 5000 -T4 <target>       # all TCP ports, fast
nmap -sU --top-ports 100 <target>           # top 100 UDP ports
nmap -sS -p <ports> <target>                 # SYN scan of specific ports
```

## Service/version + default scripts

```
nmap -sC -sV -p<ports> -oA scan_results <target>
```

`-oA` writes `.nmap`, `.gnmap`, and `.xml` output together — always capture output on a real engagement.

## Common flags

| Flag | Meaning |
|---|---|
| `-sS` | SYN (stealth) scan, needs root |
| `-sT` | full TCP connect scan |
| `-sU` | UDP scan |
| `-sC` | run default NSE scripts |
| `-sV` | version detection |
| `-O` | OS detection |
| `-A` | OS + version + scripts + traceroute |
| `-T4` | faster timing template |
| `--script vuln` | run vulnerability-category NSE scripts |
| `-Pn` | skip host discovery (treat host as up) |

## Useful NSE script categories

```
nmap --script vuln <target>
nmap --script "smb-enum-*" -p445 <target>
nmap --script "http-enum" -p80,443 <target>
```

## Output parsing

```
grep -oP '\d+/open' scan_results.nmap        # list open ports
xsltproc scan_results.xml -o scan_results.html  # convert XML to HTML report
```

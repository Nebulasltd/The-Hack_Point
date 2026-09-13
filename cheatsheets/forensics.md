# Digital Forensics Cheat Sheet

Chain of custody first: hash everything before and after you touch it, and work from a copy — never the original.

## Imaging & hashing

```
# Disk image with hashing (Linux)
dc3dd if=/dev/sdb of=evidence.img hash=sha256 log=dc3dd.log

# Verify integrity
sha256sum evidence.img > evidence.img.sha256
sha256sum -c evidence.img.sha256

# Memory acquisition (Linux, requires LiME kernel module)
insmod lime.ko "path=mem.lime format=lime"
```

On Windows, use **FTK Imager** (GUI, free) for disk/memory acquisition, or `KAPE` for fast targeted triage collection instead of a full image.

## Memory analysis (Volatility 3)

```
python3 vol.py -f mem.dmp windows.info                 # identify profile/OS
python3 vol.py -f mem.dmp windows.pslist                # running processes
python3 vol.py -f mem.dmp windows.pstree                # process tree
python3 vol.py -f mem.dmp windows.netscan                # network connections
python3 vol.py -f mem.dmp windows.cmdline                # process command lines
python3 vol.py -f mem.dmp windows.malfind                # injected/suspicious code regions
python3 vol.py -f mem.dmp windows.dumpfiles --pid <PID>  # dump files held by a process
```

## Disk / filesystem triage (The Sleuth Kit)

```
mmls evidence.img                       # partition table
fls -r -o <offset> evidence.img          # recursive file listing (incl. deleted)
icat -o <offset> evidence.img <inode> > out_file   # extract a file by inode
fsstat -o <offset> evidence.img          # filesystem details
```

## Windows artifacts (Eric Zimmerman's tools)

```
MFTECmd.exe -f "$MFT" --csv out\                 # parse Master File Table
RegistryExplorer / RECmd.exe --bn BatchExamples\Kroll_Batch.reb -d C:\path\to\hive --csv out\
EvtxECmd.exe -f Security.evtx --csv out\          # parse Windows Event Logs
PECmd.exe -f SomeApp.pf --csv out\                # parse Prefetch
```

Common artifact locations worth pulling with KAPE or manually:

| Artifact | Path | Tells you |
|---|---|---|
| Prefetch | `C:\Windows\Prefetch\*.pf` | Program execution history |
| Amcache | `C:\Windows\AppCompat\Programs\Amcache.hve` | Executed program metadata |
| ShimCache | `SYSTEM` hive | Historical file execution evidence |
| UserAssist | `NTUSER.DAT` | GUI program execution (encoded) |
| $MFT / $LogFile / $UsnJrnl | NTFS metadata files | File creation/modification/deletion timeline |
| Event Logs | `C:\Windows\System32\winevt\Logs\*.evtx` | Logons, process creation (4688), services |

## Timeline creation (Plaso)

```
log2timeline.py timeline.plaso /path/to/evidence
psort.py -o l2tcsv -w timeline.csv timeline.plaso
```

## File carving & identification

```
binwalk -e suspicious.bin           # extract embedded files/firmware
foremost -i evidence.img -o out/     # carve known file types from raw image
file suspicious_file                 # identify file type by magic bytes
exiftool image.jpg                   # metadata extraction
```

## Malware/pattern matching

```
yara -r rules.yar suspicious_file
yara -r rules.yar -r malware_dir/
```

## Network forensics

```
tshark -r capture.pcap -Y "http.request"           # filter HTTP requests
tshark -r capture.pcap --export-objects http,out/    # extract transferred files
```

Or load the pcap into **NetworkMiner** / **Wireshark** for GUI-driven analysis.

## Reference

- [SANS DFIR poster / cheat sheets](https://www.sans.org/posters/) — printable quick references for most of the above
- [Volatility 3 command reference](https://volatility3.readthedocs.io/) 
- [KAPE documentation](https://ericzimmerman.github.io/KapeDocs/)

# ORDER 66 — DFIR Traige tool

ORDER 66 is a Python-based forensic triage tool built for rapid inspection of suspicious storage devices and forensic images. It features a user friendly GUI and supports USB drives, mounted folders or disks, E01/Ex01 forensic images, and raw disk images — all from a single interface.

---

## Features

**Forensic Imaging**
- Full image hashing (MD5 / SHA1 / SHA256) with progress tracking
- E01/Ex01 forensic image support
- Raw disk image support
- Partition table detection and per-partition filesystem traversal (NTFS, FAT12/16/32, exFAT, EXT2/3/4)

**File Analysis**
- Shannon entropy calculation for packed/encrypted file detection
- MIME type detection
- PE header analysis: compile timestamp, import hash, suspicious sections, import table 
- `.lnk` shortcut parsing and target extraction
- Document metadata extraction from PDF, Office, and OLE files
- Image EXIF metadata extraction including GPS coordinates
- Autorun and autostart file detection
- Double-extension and randomized filename heuristics

**Threat Intelligence**
- VirusTotal reputation lookup with SQLite-backed local cache
- YARA rule scanning with custom rule support
- Risk scoring (0–100) per file and per scan
- IOC extraction from file strings (URLs, IPs, registry keys, email addresses)

**Archive Inspection**
- ZIP and RAR archive scanning with nested archive support (up to 2 levels deep)
- Encrypted/password-protected archive detection
- Per-member entropy, hashing, and VT reputation lookup

**Windows Artifact Detection**
- Registry autorun keys
- Startup folders and scheduled tasks
- Windows services
- Prefetch files
- Browser artifacts
- Recent documents and Recycle Bin entries
- USB connection history
- Windows Event Log (EVTX) files
- Alternate Data Streams (ADS)

**Deleted File Recovery**
- Unallocated inode enumeration 
- Risk scoring and suspicious reason tagging on deleted files

**Timeline**
- Chronological event timeline across all findings

**Reporting**
- HTML report with full scan results and risk summary
- CSV IOC export
- Structured verdict output (CLEAN / LOW / MEDIUM / HIGH RISK)
- Risk pie chart visualization in the GUI

**Scan Profiles**
- **Fast Scan** — lightweight triage: entropy only, no VT/YARA/PE, minimal I/O
- **Deep Scan** — full analysis: all modules enabled, up to 1 GB file read limit, 64 MB entropy sampling

---

## Requirements

- Python 3.10+
- [`pytsk3`](https://github.com/py4n6/pytsk) 
- [`customtkinter`](https://github.com/TomSchimansky/CustomTkinter)
- `pyewf` 
- `python-magic` 
- `pefile`
- `yara-python` 
- `LnkParse3` 
- `PyPDF2` 
- `olefile` 
- `rarfile`
  
## Install:

> Download **Order66_Setup_v2.0.exe** and follow the install instructions.

---

## Usage

> Start the Order66.exe from where you installed it or if you have created a desktop shorcut then from there. 

1. Select a scan target: USB drive, folder or mounted disk, E01 image, or raw disk image
2. Enter your VirusTotal API key (optional — required for VT reputation lookups) **RECOMMENDED**
3. Load YARA rules if present
4. Choose a scan profile (Fast / Deep) or configure modules individually
5. Hit **Execute Order 66** and monitor progress in real time
6. Review results across the tabbed GUI: Verdict, Summary, EXEs, Suspicious Files, YARA, Archives, Deleted Files, Timeline, and more
7. Open the generated HTML report or export IOCs as CSV

---

## Output

Each scan produces a timestamped output folder containing:

| File | Contents |
|------|----------|
| `report.html` | Full interactive HTML report |
| `iocs.csv` | Extracted IOCs (URLs, IPs, registry keys, emails) |

---

## Disclaimer

ORDER 66 is intended for lawful forensic triage and incident response purposes only. Always ensure you have proper authorization before scanning any device or image. The author **Koppany Bartha** is not responsible for misuse.

---

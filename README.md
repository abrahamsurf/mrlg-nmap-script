# mrlg-nmap-script
# 🔍 MRLG Vulnerability Detector (CVE-2014-3931)

This Nmap NSE script detects vulnerable instances of **Multi-Router Looking Glass (MRLG)** affected by [CVE-2014-3931](https://nvd.nist.gov/vuln/detail/CVE-2014-3931). It parses version strings from public MRLG web interfaces and flags known exploitable versions (≤ 5.4.1), including suffix-labeled releases like `5.4.1+ad1 Beta`. Few days ago
CISA just added Multi-Router Looking Glass (MRLG) Buffer Overflow Vulnerability to its KEV List (Known Exploited Vulnerabilities Catalog). 

## 🚀 Features

- ✅ Supports detection of legacy versions: `4.3.0`, `5.0.0`, `5.1.0`, `5.4.1+`, etc.
- ✅ Handles flexible banners and suffixes (e.g. `+ad1`, `-beta`, `_rc`)
- ✅ Detects vulnerable deployments on HTTP/HTTPS endpoints
- ✅ Compatible with Nmap's script engine and standard scan options

## 🛡️ Vulnerable Versions
Known affected versions include:
- 4.3.0
- 5.0.0, 5.1.0, 5.2, 5.3
- 5.4.0, 5.4.1 (+ad1, beta, rc1)
- Patched in: 5.5.0 and later

## 📜 License
Distributed under the same license as Nmap: https://nmap.org/book/man-legal.html

## Legal Disclaimer
This tool is intended for authorized security testing and educational purposes only. Users are responsible for ensuring they have proper authorization before scanning any systems. The author is not responsible for any misuse of this tool and use this at your own risk!


## 📦 Installation

1. Copy the script to your local Nmap scripts directory
2. Update the NSE script database:
```bash
nmap --script-updatedb

🔧 **Usage**

nmap -p80,443 --script mrlg-vuln <target>
** Example Output:**

Vulnerable version:
PORT   STATE SERVICE
80/tcp open  http
| mrlg-vuln:
|   Vulnerable to CVE-2014-3931
|   Detected version: 5.4.1+ad1 Beta

Patched version:
PORT   STATE SERVICE
80/tcp open  http
|_mrlg-vuln: MRLG not detected: unexpected HTTP status 404



# NCSA SQC Part 3 – Memory Forensics Investigation

## Overview

This repository documents my investigation of a Windows memory image completed as part of the NCSA Skills Qualification Check (SQC). Using forensic analysis techniques and the Volatility Framework, I analyzed volatile memory to identify running processes, active network connections, browser activity, suspicious search terms, and evidence of potentially malicious tools.

This project demonstrates the documentation and investigative process used during a memory forensic examination.

---

## Objectives

- Analyze a Windows memory dump
- Enumerate active processes
- Identify active network connections
- Extract Google Chrome browsing history
- Identify suspicious search terms
- Locate evidence of hacking tools
- Document findings and indicators of compromise (IOCs)

---

## Skills Demonstrated

- Memory Forensics
- Digital Forensics
- Incident Response
- Threat Hunting
- Process Analysis
- Network Analysis
- Volatility Framework
- Kali Linux
- Evidence Collection
- Technical Documentation

---

## Tools Used

| Tool | Purpose |
|------|---------|
| Volatility 2/3 | Memory analysis |
| Kali Linux | Investigation platform |
| Linux Terminal | Command-line analysis |
| Strings/Grep | Artifact searching |

---

## Investigation Workflow

1. Acquire the memory image
2. Identify the operating system profile
3. Enumerate running processes
4. Analyze active network connections
5. Recover browser history
6. Identify suspicious user activity
7. Search for evidence of hacking tools
8. Document findings

---

## Repository Structure

```text
report/
investigation/
evidence/
tools/
docs/
```

---

## Key Findings

- Process enumeration completed
- Active network connections identified
- Browser history successfully recovered
- Suspicious search activity documented
- Evidence collected for forensic reporting

*(Detailed findings are documented in the report directory.)*

---

## Lessons Learned

This investigation reinforced the importance of memory forensics during incident response. Volatile memory contains valuable evidence that may not exist on disk, making memory analysis an essential component of modern digital forensic investigations.

---

## Author

**Anthony Faircloth**

Aspiring Cybersecurity Analyst

- GitHub: https://github.com/AF-Cyberlabs
- LinkedIn: https://www.linkedin.com/in/anthony-faircloth-a2746649

## Chrome Browser History Analysis

### Artifact

* **File:** ChromeHistory.db
* **Location:** Recovered from NCSA-SQC disk image
* **Analysis Tool:** SQLite3

### Evidence Recovered

Browser history analysis identified multiple entries of interest:

| Timestamp | Activity                                     | URL/Source                  |
| --------- | -------------------------------------------- | --------------------------- |
| N/A       | Tor Browser download page accessed           | tor-browser.en.softonic.com |
| N/A       | Search for "hacking tutorials"               | Google Search               |
| N/A       | Hacking tutorial website accessed            | hackingtutorials.org        |
| N/A       | Nmap security scanner download page accessed | nmap.org                    |
| N/A       | FileZilla Client download page accessed      | filezilla-project.org       |
| N/A       | Search for "NCSA Evidence{NCSA 2022}"        | Google Search               |

### Findings

The recovered Chrome history shows activity related to cybersecurity tools, including Nmap and FileZilla, as well as searches related to hacking tutorials. A search query referencing "NCSA Evidence{NCSA 2022}" was also identified, which directly correlates with the forensic investigation scenario.

These artifacts were preserved and correlated with additional evidence sources including:

* Memory dump analysis
* Disk image analysis
* Network capture analysis

### Analyst Notes

Browser artifacts alone do not prove malicious intent. Findings were documented as indicators requiring correlation with additional forensic evidence.


## Chrome Download Artifact Analysis

### Artifact

* **Database:** ChromeHistory.db
* **Table Analyzed:** downloads
* **Tool:** SQLite3

### Recovered Downloads

| File                             | Source URL            | Analysis Notes                                          |
| -------------------------------- | --------------------- | ------------------------------------------------------- |
| hashcat-6.2.5 (1).7z             | hashcat.net           | Password recovery/cracking utility downloaded           |
| nmap-7.92-setup (1).exe          | nmap.org              | Network scanning/security assessment utility downloaded |
| FileZilla_3.60.2_win32-setup.exe | filezilla-project.org | File transfer client downloaded                         |
| MOCK_DATA.csv                    | mockaroo.com          | Test data file downloaded                               |

### Findings

The Chrome download database confirmed that multiple security-related tools were downloaded to the user profile:

* Hashcat
* Nmap
* FileZilla

These artifacts were correlated with previously recovered browser history entries showing searches and visits related to hacking tutorials and security tools.

The presence of security tools alone does not establish malicious activity. Additional correlation with memory artifacts, file system artifacts, and network evidence is required to determine user intent.


## Command History Analysis

### Artifact

* **Source:** Memory image (`NCSA-SQC-MEMDUMP-01.raw`)
* **Tool:** Volatility 2.6.1 (`cmdscan` plugin)

### Recovered Commands

| Command                | Description                                               |
| ---------------------- | --------------------------------------------------------- |
| `nmap -sU 192.168.0.1` | UDP scan targeting a local network device.                |
| `ipconfig`             | Display Windows network configuration.                    |
| `ifconfig`             | Network interface command recovered from command history. |
| `nmap -sU 172.16.0.5`  | UDP scan targeting a private network host.                |

### Analysis

Recovered command history indicates that Nmap was used to perform UDP scans against private IP addresses within local network ranges. This finding correlates with browser artifacts showing that the Nmap installer was downloaded.

The recovered commands provide evidence of network reconnaissance activity within the lab environment.


## Command Execution Analysis

### Artifact

* **Source:** `NCSA-SQC-MEMDUMP-01.raw`
* **Tool:** Volatility 2.6.1 (`consoles` plugin)

### Recovered Console Activity

Recovered console history showed the following commands:

```text
nmap -sU 192.168.0.1
ifconfig
ipconfig
nmap -sU 172.16.0.5
```

### Console Output

The recovered console output showed:

* An attempted UDP scan against `192.168.0.1` that failed because no valid route was available.
* An unsuccessful attempt to execute `ifconfig`, which is not a native Windows command.
* Successful execution of `ipconfig`, revealing:

  * IPv4 Address: `172.16.0.5`
  * Default Gateway: `172.16.0.1`
* A second UDP scan targeting `172.16.0.5`, which terminated with an error before completing.

### Correlated Evidence

This activity was corroborated by:

* Chrome browser history showing visits to the Nmap download page.
* Chrome download records confirming retrieval of the Nmap installer.
* Active `chrome.exe` and `cmd.exe` processes recovered from memory.

### Conclusion

Multiple independent forensic artifacts demonstrate that Nmap was downloaded and subsequently executed. The recovered console output indicates attempted UDP network reconnaissance within a private network; however, the recovered output shows that the scans did not complete successfully.


## Network Traffic Analysis

### Artifact

* **File:** `suspicious_activity.pcapng`
* **Tool:** Wireshark

### Findings

Analysis of the packet capture identified TCP communications between `10.0.2.19` and `10.0.2.20` over **TCP port 21 (FTP)**.

This network activity correlates with browser artifacts showing the download of the FileZilla FTP client. While the packet capture confirms communication with an FTP service, it does not by itself identify the specific client application used.

### Correlated Evidence

* Browser history contained visits to the FileZilla download page.
* Browser download history confirmed retrieval of the FileZilla installer.
* Packet capture showed FTP communication over TCP port 21.

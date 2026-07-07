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

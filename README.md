# NCSA SQC Part 3 – Memory Forensics Investigation

## Project Overview

This repository documents my analysis of a Windows memory dump completed as part of the NCSA Skills Qualification Check (SQC). The objective of this investigation was to recover volatile system artifacts, identify suspicious activity, and document forensic findings using industry-standard memory analysis techniques.

The investigation focused on identifying running processes, active network connections, browser activity, suspicious search terms, and evidence of potential hacking tools.

---

## Objectives

- Analyze a captured memory image
- Enumerate active processes
- Identify network connections
- Recover Google Chrome browsing history
- Identify suspicious search activity
- Locate evidence of hacking tools
- Document findings in a forensic investigation report

---

# Skills Demonstrated

- Memory Forensics
- Digital Forensics
- Incident Response
- Threat Hunting
- Process Analysis
- Network Analysis
- Artifact Recovery
- Linux
- Kali Linux
- Volatility Framework
- Documentation
- Evidence Collection

---

# Lab Environment

| Component | Description |
|-----------|-------------|
| Operating System | Kali Linux |
| Memory Analysis | Volatility Framework |
| Shell | Bash |
| Evidence | Windows Memory Dump |

---

# Investigation Workflow

1. Identify the memory image profile
2. Enumerate running processes
3. Analyze active network connections
4. Recover browser artifacts
5. Identify suspicious search terms
6. Locate evidence of hacking tools
7. Document Indicators of Compromise (IOCs)

---

# Repository Structure

```
.
├── report/
├── investigation/
├── evidence/
│   ├── screenshots/
│   ├── recovered-artifacts/
│   └── logs/
├── tools/
└── docs/
```

---

# Evidence

Evidence collected during the investigation includes:

- Volatility command output
- Process listings
- Network connection analysis
- Browser history artifacts
- Screenshots
- Recovered files

---

# Lessons Learned

This investigation reinforced the importance of volatile memory analysis during incident response. Memory artifacts can reveal active processes, network communications, and user activity that may no longer exist on disk.

---

# References

- Volatility Framework
- NCSA Skills Qualification Check

---

## Author

Anthony Faircloth

Cybersecurity Portfolio

GitHub: https://github.com/AF-Cyberlabs

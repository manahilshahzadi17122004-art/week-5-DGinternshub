# Week 5 - Phishing, Malware Triage, Threat Intelligence and Incident Response
**DG Interns Hub | Cybersecurity Internship**

## 1. Goal of This Week
To investigate email-borne and endpoint threats like a Tier 1 / Tier 2 SOC Analyst and write a proper incident report.

In this week I learned:
- Email header analysis
- IOC extraction
- Hash and URL reputation checking
- Safe sandbox use
- MITRE ATT&CK mapping
- Cyber Kill Chain
- Incident Response Lifecycle

## 2. Folder Structure
DG Interns Hub / Week 5-- Notes Folder-- Writeups Folder-- Findings Folder-- Incident Report Folder-- Cheat Sheet Folder-- PDF Report of Weekly Work-- Presentation Report of Weekly Work-- README File

## 3. Theoretical Part - Notes Folder
All 8 questions are answered in separate files in my own words:
1. Incident Response Lifecycle - NIST SP 800-61 Four-Phase Model
2. Phishing Types - Phishing, Spear Phishing, Whaling, Smishing, Vishing, BEC
3. SPF, DKIM and DMARC - With Pass and Fail examples
4. How to Read an Email Header - Received, Return-Path, Reply-To, Message-ID, Authentication-Results
5. IOC vs IOA and Pyramid of Pain - Hashes to TTPs
6. MITRE ATT&CK vs Cyber Kill Chain - Mapping of 5 attacks from Weeks 2-4
7. Static vs Dynamic Malware Analysis and Sandbox Safety Rules
8. Incident Report Structure, Severity Levels and Escalation

## 4. Labs / Writeups Folder
Writeups are prepared separately for each lab:

**TryHackMe Core Rooms:**
- Cyber Kill Chain
- MITRE
- Pyramid of Pain
- Phishing Analysis Fundamentals / Phishing Emails 1
- Intro to Cyber Threat Intel

**Optional:**
- Threat Intelligence Tools
- YARA

**Other Challenges:**
- Malware-Traffic-Analysis.net exercise - PCAP opened only inside Kali VM, no extracted files were executed
- One free phishing / malware challenge on CyberDefenders / Blue Team Labs Online

## 5. Hands-On Tasks - Findings Folder

### 5.1 Phishing Analysis
Analyzed 3 public phishing samples. For each sample documented:
- Sender, Recipient, Subject, Date
- Authentication-Results - SPF, DKIM, DMARC
- URL and Domain Reputation - urlscan.io, VirusTotal, AlienVault OTX
- Attachment Hashes and Reputation - VirusTotal
- Verdict - Benign / Suspicious / Malicious with justification
- Red Flags Identified

**Main Case Investigated:**
- Claimed Sender: Home Depot
- Actual Sender: support@teckbe.com
- X-Originating-IP (Defanged): 103[.]234[.]236[.]83
- Mail Server: atlas102.free.mail.gq1.yahoo.com
- Verdict: Malicious - Sender domain mismatch + suspicious IP

### 5.2 Safe Malware Triage
- No live malware was downloaded or executed.
- EICAR test file was used on Windows VM to check Antivirus and Sysmon detection.
- 2 public Any.Run / Hybrid Analysis reports were analyzed for process tree, network IOCs and ATT&CK techniques.
- Screenshots are saved in Findings Folder.

### 5.3 ATT&CK Map - MITRE ATT&CK Navigator
Built a layer in ATT&CK Navigator for techniques seen in Weeks 2-5.
Screenshot and JSON are saved in Findings Folder.

| Technique ID | Technique | Tactic |
| --- | --- | --- |
| T1566 | Phishing | Initial Access |
| T1016 | Network Service Discovery | Discovery |
| T1110 | Brute Force | Credential Access |
| T1059.001 | PowerShell | Execution |
| T1136.001 | Create Account: Local Account | Persistence |

### 5.4 Atomic Red Team Tests
Windows VM snapshot was taken first, then 3 atomics were run:
- T1059.001 - PowerShell
- T1136.001 - Create Local Account
- T1053.005 - Scheduled Task

For each atomic, Sysmon Event ID, key fields, SIEM search, detection result and detection gap are documented. Screenshots are in Findings Folder.

## 6. Incident Report Folder
A 2-3 page Incident Report is prepared on the phishing email case. It includes:
- Summary
- Timeline of Events
- IOCs
- ATT&CK Mapping
- Severity with Justification - Medium / High: Credential theft risk, no data loss as email was identified early
- Containment Actions - Email blocked, sender reported, no link clicked
- Recommendations - Header checking training, DMARC enforcement, detection rule improvement

## 7. Cheat Sheet Folder
1. **IOC Table:** IOC Type - Where to Find It - Tool to Check It - 12 entries
2. **Phishing Red-Flag Checklist:** One-page checklist

## 8. Tools Used - All Free
VirusTotal, urlscan.io, AbuseIPDB, AlienVault OTX, CyberChef, MXToolbox Email Header Analyzer, Any.Run Community Plan, MITRE ATT&CK Navigator, Sysmon, VirtualBox / Kali VM

## 9. Safety Rules Followed
- No live malware downloaded or executed
- Only EICAR or public sandbox reports used
- PCAPs opened only inside isolated lab VM
- Extracted files were never run
- IOCs shared in defanged form

## 10. LinkedIn Activity
- **Concept Post:** How to spot a phishing email using headers - 5 points
- **Weekly Post:** Incident Report summary + ATT&CK Navigator screenshot, tagging DG Interns Hub
- link:https://lnkd.in/p/dwNv9SAg
- link: https://lnkd.in/p/d8YcKrxq


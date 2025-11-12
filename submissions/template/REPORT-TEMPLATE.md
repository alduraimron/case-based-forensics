# Digital Forensics - Report Template

## Case Information

**Case Number:** [AUTO-GENERATED]  
**Case Title:** [Case Name]  
**Investigator:** [Your Name]  
**Date:** [Investigation Date]  
**Classification:** [Confidential/Internal]

---

## Executive Summary

### Overview
[Provide a brief, non-technical summary of the incident, suitable for management. Include what happened, when, and the overall impact.]

### Key Findings
1. [Finding 1]
2. [Finding 2]
3. [Finding 3]

### Impact Assessment
- **Severity:** [Low/Medium/High/Critical]
- **Affected Systems:** [Number/List]
- **Data Compromise:** [Yes/No - Brief description]
- **Estimated Impact:** [Financial/Operational/Reputational]

### Immediate Recommendations
1. [Critical action 1]
2. [Critical action 2]
3. [Critical action 3]

---

## 1. Case Background

### 1.1 Incident Details
- **Date of Incident:** [Date/Time]
- **Date of Discovery:** [Date/Time]
- **Reported By:** [Name/Department]
- **Incident Type:** [Network Intrusion/Malware/Data Breach/etc.]

### 1.2 Initial Indicators
[Describe what first indicated there was a problem]
- Alert/notification received
- Unusual system behavior
- User report
- Automated detection

### 1.3 Scope of Investigation
[Define what was investigated and what was not]
- **In Scope:**
  - [System/Network/Data 1]
  - [System/Network/Data 2]
- **Out of Scope:**
  - [System/Network/Data 1]
  - [System/Network/Data 2]

---

## 2. Methodology

### 2.1 Investigation Approach
[Describe the overall approach and methodology used]
- Evidence collection procedures
- Analysis techniques
- Tools and technologies used

### 2.2 Tools Used

| Tool Name | Version | Purpose |
|-----------|---------|---------|
| Wireshark | 4.0.x | Network traffic analysis |
| [Tool 2] | [Ver] | [Purpose] |
| [Tool 3] | [Ver] | [Purpose] |

### 2.3 Chain of Custody
[Document evidence handling]

| Evidence ID | Description | Collected By | Date/Time | Hash |
|-------------|-------------|--------------|-----------|------|
| [ID] | [Desc] | [Name] | [DateTime] | [Hash] |

---

## 3. Technical Analysis

### 3.1 Evidence Collection

#### 3.1.1 Network Evidence
[For network intrusion cases]
- PCAP files analyzed
- Time ranges
- Source/Destination analysis

#### 3.1.2 Malware Evidence
[For malware cases]
- Sample information
- Hash values
- File locations

#### 3.1.3 Log Evidence
[For log analysis cases]
- Log sources
- Time ranges
- Key log entries

### 3.2 Detailed Findings

#### Finding 1: [Title]
**Severity:** [Critical/High/Medium/Low]

**Description:**
[Detailed technical description]

**Evidence:**
- Evidence item 1
- Evidence item 2
- Screenshot/Reference

**Analysis:**
[Your analysis of this finding]

**Impact:**
[Impact of this specific finding]

---

#### Finding 2: [Title]
**Severity:** [Critical/High/Medium/Low]

[Same structure as Finding 1]

---

### 3.3 Attack Timeline

| Time (UTC) | Event | Evidence Source | Description |
|------------|-------|-----------------|-------------|
| 2025-XX-XX HH:MM | Initial Access | [Source] | [Description] |
| 2025-XX-XX HH:MM | Reconnaissance | [Source] | [Description] |
| 2025-XX-XX HH:MM | Privilege Escalation | [Source] | [Description] |
| 2025-XX-XX HH:MM | Lateral Movement | [Source] | [Description] |
| 2025-XX-XX HH:MM | Exfiltration | [Source] | [Description] |

**Visual Timeline:**
[Insert timeline graphic]

---

## 4. Indicators of Compromise (IoC)

### 4.1 Network Indicators

#### IP Addresses
```
[Malicious IP 1] - [Description/Purpose]
[Malicious IP 2] - [Description/Purpose]
```

#### Domain Names
```
malicious-domain1.com - [C2 Server]
suspicious-site.net - [Phishing]
```

#### URLs
```
http://malicious.com/payload.exe
https://c2-server.com/beacon
```

### 4.2 Host Indicators

#### File Hashes
```
MD5:    [hash] - [filename]
SHA1:   [hash] - [filename]
SHA256: [hash] - [filename]
```

#### File Paths
```
C:\Windows\Temp\malware.exe
/tmp/.hidden_backdoor
```

#### Registry Keys
```
HKLM\Software\Microsoft\Windows\CurrentVersion\Run\Malware
```

#### Mutex Names
```
{UNIQUE-MALWARE-MUTEX-001}
```

### 4.3 Account Indicators
```
compromised_user1 - [Description]
backdoor_admin - [Description]
```

### 4.4 Attack Patterns
- [Pattern 1: Description]
- [Pattern 2: Description]

---

## 5. MITRE ATT&CK Mapping

### Tactics & Techniques Used

| Tactic | Technique | TID | Evidence |
|--------|-----------|-----|----------|
| Initial Access | Phishing | T1566 | [Evidence ref] |
| Execution | Command-Line Interface | T1059 | [Evidence ref] |
| Persistence | Registry Run Keys | T1547.001 | [Evidence ref] |
| Privilege Escalation | Sudo/Su | T1548.003 | [Evidence ref] |
| Defense Evasion | Obfuscated Files | T1027 | [Evidence ref] |
| Credential Access | Brute Force | T1110 | [Evidence ref] |
| Discovery | Network Service Scanning | T1046 | [Evidence ref] |
| Lateral Movement | Remote Services | T1021 | [Evidence ref] |
| Collection | Data from Local System | T1005 | [Evidence ref] |
| Exfiltration | Exfil Over C2 Channel | T1041 | [Evidence ref] |

**ATT&CK Navigator:**
[Insert ATT&CK Navigator screenshot or link]

---

## 6. Impact Assessment

### 6.1 Technical Impact
- **Systems Affected:** [Number/List]
- **Data Accessed:** [Type/Volume]
- **Services Disrupted:** [List]
- **Duration of Compromise:** [Timeframe]

### 6.2 Business Impact
- **Operational Impact:** [Description]
- **Financial Impact:** [Estimated cost]
- **Reputational Impact:** [Risk level]
- **Regulatory Impact:** [Compliance implications]

### 6.3 Data Classification
| Data Type | Classification | Volume | Status |
|-----------|----------------|--------|--------|
| Customer PII | Confidential | [Volume] | Compromised/Safe |
| Financial Records | Restricted | [Volume] | Compromised/Safe |
| [Type] | [Level] | [Volume] | [Status] |

---

## 7. Root Cause Analysis

### 7.1 Primary Cause
[What was the main vulnerability or weakness that allowed the incident?]

### 7.2 Contributing Factors
1. [Factor 1]
2. [Factor 2]
3. [Factor 3]

### 7.3 Existing Controls
**What worked:**
- [Control 1]
- [Control 2]

**What failed:**
- [Control 1]
- [Control 2]

---

## 8. Containment & Response Actions

### 8.1 Immediate Actions Taken
| Date/Time | Action | Performed By | Result |
|-----------|--------|--------------|--------|
| [DateTime] | [Action] | [Name] | [Result] |

### 8.2 Containment Measures
- [Measure 1: e.g., Isolated affected systems]
- [Measure 2: e.g., Blocked malicious IPs]
- [Measure 3: e.g., Disabled compromised accounts]

### 8.3 Eradication Steps
- [Step 1: e.g., Removed malware from systems]
- [Step 2: e.g., Patched vulnerabilities]
- [Step 3: e.g., Updated firewall rules]

### 8.4 Recovery Actions
- [Action 1: e.g., Restored systems from backup]
- [Action 2: e.g., Reset all passwords]
- [Action 3: e.g., Verified system integrity]

---

## 9. Detection & Prevention

### 9.1 YARA Rules
```yara
rule Detect_Case_Malware {
    meta:
        description = "[Description]"
        author = "[Your Name]"
        date = "[Date]"
    
    strings:
        $s1 = "[String]" ascii wide
        $hex1 = { [Hex Pattern] }
    
    condition:
        uint16(0) == 0x5A4D and
        all of them
}
```

### 9.2 SIEM Detection Rules
```
# Rule 1: Brute Force Detection
[Rule syntax]

# Rule 2: Data Exfiltration
[Rule syntax]
```

### 9.3 Network Detection (Snort/Suricata)
```
alert tcp any any -> any any (msg:"[Alert Message]"; \
    content:"[Pattern]"; sid:100001; rev:1;)
```

### 9.4 Host-Based Detection
- File Integrity Monitoring rules
- Registry monitoring
- Process monitoring

---

## 10. Recommendations

### 10.1 Immediate Actions (0-7 days)
**Priority: Critical**

1. **[Action 1]**
   - Description: [Details]
   - Owner: [Department/Person]
   - Estimated Effort: [Hours/Days]
   
2. **[Action 2]**
   - Description: [Details]
   - Owner: [Department/Person]
   - Estimated Effort: [Hours/Days]

### 10.2 Short-Term Actions (1-3 months)
**Priority: High**

1. **[Action 1]**
   - Description: [Details]
   - Owner: [Department/Person]
   - Estimated Cost: [Amount]

### 10.3 Long-Term Actions (3-12 months)
**Priority: Medium**

1. **[Action 1]**
   - Description: [Details]
   - Owner: [Department/Person]
   - Estimated Cost: [Amount]

### 10.4 Security Control Improvements

#### Technical Controls
- [ ] Implement [Control]
- [ ] Update [System]
- [ ] Deploy [Technology]

#### Administrative Controls
- [ ] Update [Policy]
- [ ] Create [Procedure]
- [ ] Conduct [Training]

#### Physical Controls
- [ ] Improve [Access Control]
- [ ] Install [Security Measure]

---

## 11. Lessons Learned

### 11.1 What Went Well
- [Success 1]
- [Success 2]
- [Success 3]

### 11.2 What Could Be Improved
- [Improvement 1]
- [Improvement 2]
- [Improvement 3]

### 11.3 Action Items
| Item | Owner | Due Date | Priority |
|------|-------|----------|----------|
| [Action] | [Name] | [Date] | [H/M/L] |

---

## 12. Appendices

### Appendix A: Evidence Screenshots
[Include numbered screenshots with captions]

### Appendix B: Raw Data
[Include relevant raw data, command outputs, etc.]

### Appendix C: Tool Outputs
[Include complete tool reports if relevant]

### Appendix D: Scripts Used
[Include analysis scripts]

### Appendix E: References
1. [Reference 1]
2. [Reference 2]
3. [Reference 3]

---

## Document Control

**Version History:**

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | [Date] | [Name] | Initial report |
| 1.1 | [Date] | [Name] | [Changes] |

**Distribution List:**
- [Name/Role]
- [Name/Role]

**Classification:** [Confidential/Internal Use Only]

**Retention Period:** [Years]

---

**Report Prepared By:**  
Name: [Your Name]  
Title: Digital Forensics Analyst  
Date: [Date]  
Signature: ___________________

**Report Reviewed By:**  
Name: [Reviewer Name]  
Title: [Title]  
Date: [Date]  
Signature: ___________________

---

*End of Report*


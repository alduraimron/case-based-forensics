# Case 3: Log Analysis & Incident Response

## 🎯 Objectives
Menganalisis log files dari berbagai sumber untuk mendeteksi, menginvestigasi, dan merespons insiden keamanan yang terjadi pada infrastruktur IT.

## 📖 Scenario

**Tanggal Insiden:** 20 Oktober 2025  
**Organisasi:** DataCore Enterprise  
**Pelapor:** Security Operations Center (SOC)

### Background
DataCore Enterprise adalah perusahaan yang mengelola data center untuk berbagai klien. Pada tanggal 20 Oktober 2025 pukul 02:30 AM, sistem monitoring mendeteksi aktivitas login yang tidak biasa pada beberapa server critical.

Alert yang diterima:
- Multiple failed SSH login attempts
- Successful login dari IP address yang tidak dikenal
- Unusual data transfer activity
- Unauthorized privilege escalation
- Possible data exfiltration

Sebagai Digital Forensics Analyst, Anda ditugaskan untuk:
1. Menganalisis log files untuk mengidentifikasi security breach
2. Menentukan timeline serangan
3. Mengidentifikasi user accounts yang terkompromisi
4. Menentukan data yang mungkin telah dicuri
5. Memberikan rekomendasi untuk containment dan recovery
6. Membuat Incident Response report

## 📊 Data Source

### Dataset yang Digunakan

#### Option 1: SecRepo Security Datasets
- **URL:** https://www.secrepo.com/
- **Type:** Apache logs, SSH logs, System logs
- **Format:** Text files, CSV

#### Option 2: Log Hub - Cyber Security Dataset
- **URL:** https://github.com/logpai/loghub
- **Type:** Various system and application logs
- **Format:** Log files

#### Option 3: LANL Cyber Security Dataset
- **URL:** https://csr.lanl.gov/data/cyber1/
- **Type:** Authentication, Process, Network flow logs
- **Format:** CSV, JSON

### Sample Log Files untuk Case Ini

Untuk pembelajaran, kita akan menggunakan kombinasi dari:

```
logs/
├── auth.log          # SSH/authentication logs
├── apache_access.log # Web server access logs
├── apache_error.log  # Web server error logs
├── syslog           # System logs
├── firewall.log     # Firewall logs
└── database.log     # Database query logs
```

## 🔍 Investigation Tasks

### Task 1: Initial Triage & Timeline (20 points)

**Objectives:**
1. Identify the time window of the incident
2. Determine affected systems
3. Create initial timeline of events
4. Identify critical log sources

**Analysis Focus:**
- First suspicious activity
- Last known good state
- Duration of incident
- Affected services

**Deliverables:**
- Timeline of key events
- List of affected systems
- Summary of log sources analyzed

### Task 2: Authentication Analysis (25 points)

**Objectives:**
1. Identify brute force attempts
2. Find successful unauthorized logins
3. Identify compromised accounts
4. Trace login sources (IP addresses, locations)
5. Analyze login patterns

**Key Questions:**
- Which accounts were targeted?
- How many failed login attempts?
- Which logins were successful?
- From which IP addresses?
- What time did successful breaches occur?

**Deliverables:**
- Failed login statistics
- Successful unauthorized login details
- Compromised account list
- Geographic analysis of login sources

### Task 3: Privilege Escalation Detection (20 points)

**Objectives:**
1. Identify sudo/privilege escalation attempts
2. Track command execution by compromised accounts
3. Identify unauthorized administrative actions
4. Detect lateral movement

**Analysis Focus:**
- `sudo` command usage
- User privilege changes
- Administrative command execution
- Account creation/modification

**Deliverables:**
- List of privilege escalation events
- Commands executed with elevated privileges
- Timeline of administrative actions

### Task 4: Data Access & Exfiltration (20 points)

**Objectives:**
1. Identify accessed files and directories
2. Detect large data transfers
3. Analyze database access patterns
4. Identify potential data exfiltration

**Analysis Focus:**
- File access logs
- Network transfer logs
- Database queries
- Unusual data patterns

**Deliverables:**
- List of accessed sensitive files
- Data transfer volumes and destinations
- Database queries executed
- Potential exfiltrated data assessment

### Task 5: IoC & Recommendations (15 points)

**Objectives:**
1. Compile Indicators of Compromise (IoCs)
2. Create detection rules
3. Provide remediation steps
4. Recommend security improvements

**Deliverables:**
- Complete IoC list
- SIEM detection rules
- Incident Response playbook
- Security hardening recommendations

## 🛠️ Tools Required

### Log Analysis Tools

#### 1. Command Line Tools
```bash
# Basic tools (Linux/macOS)
grep      # Pattern matching
awk       # Text processing
sed       # Stream editing
cut       # Column extraction
sort      # Sorting
uniq      # Remove duplicates
wc        # Count lines/words

# Advanced tools
jq        # JSON processing
xmlstarlet # XML processing
```

#### 2. Python Libraries
```bash
pip install pandas numpy matplotlib seaborn
pip install python-dateutil pytz
pip install regex
pip install colorama  # Colored output
```

#### 3. Log Analysis Scripts
- Custom Python scripts (provided in this case)
- Shell scripts for automation

#### 4. Visualization Tools
- **Kibana** (with Elasticsearch)
- **Grafana**
- Python matplotlib/seaborn
- **Splunk** (optional, if available)

### Optional Professional Tools

#### SIEM Platforms (for learning)
1. **ELK Stack** (Elasticsearch, Logstash, Kibana)
   - Free and open source
   - Installation: https://www.elastic.co/elk-stack

2. **Splunk Free**
   - 500MB/day limit
   - Download: https://www.splunk.com/

3. **Graylog**
   - Open source
   - Installation: https://www.graylog.org/

## 📝 Analysis Guide

### Phase 1: Log Collection & Preparation

```bash
# 1. Organize log files
mkdir -p case3-logs/{auth,web,system,network,database}

# 2. Check log formats
head -n 20 auth.log
head -n 20 apache_access.log

# 3. Count total log entries
wc -l *.log

# 4. Check date ranges
head -n 1 auth.log
tail -n 1 auth.log
```

### Phase 2: Authentication Log Analysis

#### Analyze SSH Brute Force Attempts

```bash
# Failed SSH login attempts
grep "Failed password" auth.log | wc -l

# Unique IPs attempting failed logins
grep "Failed password" auth.log | \
  awk '{print $(NF-3)}' | sort | uniq -c | sort -rn

# Top 10 attacked users
grep "Failed password" auth.log | \
  awk '{print $9}' | sort | uniq -c | sort -rn | head -10

# Successful SSH logins
grep "Accepted password" auth.log

# Successful logins from specific IP
grep "Accepted password" auth.log | grep "192.168.1.100"
```

#### Timeline of Login Events

```bash
# Extract login timeline
grep -E "(Failed|Accepted)" auth.log | \
  awk '{print $1, $2, $3, $9, $(NF-3), $11}'
```

### Phase 3: Web Access Log Analysis

#### Apache Log Analysis

```bash
# Top 10 IP addresses
awk '{print $1}' apache_access.log | sort | uniq -c | sort -rn | head -10

# 404 errors (reconnaissance)
awk '$9 == 404 {print $7}' apache_access.log | sort | uniq -c | sort -rn

# SQL injection attempts
grep -i "select\|union\|insert\|update\|delete" apache_access.log

# XSS attempts
grep -i "script\|javascript\|onerror" apache_access.log

# Admin panel access
grep "/admin\|/wp-admin\|/phpmyadmin" apache_access.log

# Large POST requests (data exfiltration/upload)
awk '$6 == "\"POST" && $10 > 10000 {print $0}' apache_access.log
```

### Phase 4: System Log Analysis

```bash
# User account changes
grep -E "useradd|userdel|usermod" syslog

# Sudo usage
grep "sudo:" syslog

# Service starts/stops
grep -E "systemd.*Start|systemd.*Stop" syslog

# Kernel messages
grep "kernel:" syslog
```

### Phase 5: Pattern Detection

#### Detect Port Scanning
```bash
# Multiple connection attempts to different ports
awk '{print $1, $2, $3, $5}' firewall.log | \
  grep -E "SYN|Connection" | \
  sort | uniq -c | sort -rn
```

#### Detect Data Exfiltration
```bash
# Large outbound transfers
awk '$7 ~ /OUT/ && $NF > 100000 {print $0}' network.log
```

## 📋 Analysis Scripts

### Python Log Analyzer

```python
#!/usr/bin/env python3
"""
See: log_analyzer.py in this directory
"""
```

### Quick Analysis Commands

```bash
# Create analysis script
cat > quick_analysis.sh << 'EOF'
#!/bin/bash

echo "=== Failed Login Analysis ==="
echo "Total failed attempts:"
grep "Failed password" auth.log | wc -l

echo -e "\nTop 10 attacking IPs:"
grep "Failed password" auth.log | \
  awk '{print $(NF-3)}' | sort | uniq -c | sort -rn | head -10

echo -e "\n=== Successful Logins ==="
grep "Accepted password" auth.log | \
  awk '{print $1, $2, $3, "User:", $9, "From:", $(NF-3)}'

echo -e "\n=== Privilege Escalation ==="
grep "sudo:" syslog | \
  awk '{print $1, $2, $3, $5, $6, $7, $8, $9}'

echo -e "\n=== Account Modifications ==="
grep -E "useradd|usermod|userdel" syslog
EOF

chmod +x quick_analysis.sh
./quick_analysis.sh
```

## 📊 Report Template

### 1. Executive Summary (1 page)
- Incident overview
- Impact assessment
- Key findings
- Immediate actions taken
- Recommendations summary

### 2. Incident Details (2-3 pages)
- Initial detection
- Scope of compromise
- Attack vector
- Timeline of events
- Systems affected

### 3. Technical Analysis (5-8 pages)

#### 3.1 Authentication Analysis
- Failed login statistics
- Successful unauthorized access
- Compromised accounts
- Source IP analysis

#### 3.2 Privilege Escalation
- Sudo command usage
- Administrative actions
- Account modifications
- Lateral movement

#### 3.3 Data Access
- Files accessed
- Database queries
- Data transfers
- Exfiltration evidence

### 4. Timeline (1-2 pages)
- Chronological event sequence
- Visual timeline
- Key milestones

### 5. Indicators of Compromise (1-2 pages)
- IP addresses
- User accounts
- File hashes
- URLs/domains
- Attack patterns

### 6. Impact Assessment (1 page)
- Affected systems
- Compromised data
- Business impact
- Regulatory implications

### 7. Containment & Recovery (2-3 pages)
- Immediate actions
- Containment measures
- Eradication steps
- Recovery procedures

### 8. Recommendations (2-3 pages)
- Short-term fixes
- Long-term improvements
- Security controls
- Monitoring enhancements

### 9. Lessons Learned (1 page)
- What went well
- What needs improvement
- Action items

## 🎓 Learning Outcomes

Setelah menyelesaikan case ini:
- ✅ Mampu menganalisis berbagai jenis log files
- ✅ Mengidentifikasi security incidents dari log data
- ✅ Membuat timeline serangan dari log entries
- ✅ Menggunakan command-line tools untuk log analysis
- ✅ Membuat detection rules dan IoCs
- ✅ Menulis Incident Response report

## 💡 Analysis Tips

### General Tips
1. **Start with timeline** - Understand "when" before "what"
2. **Correlate multiple sources** - Cross-reference different logs
3. **Look for patterns** - Automated attacks have patterns
4. **Focus on anomalies** - What's unusual?
5. **Document everything** - Keep notes as you analyze

### Authentication Logs
- High volume of failed logins = brute force
- Success after many failures = potential breach
- Logins at unusual times = suspicious
- Logins from unusual locations = investigate

### Web Logs
- 404 errors in sequence = reconnaissance
- SQL keywords in URLs = SQL injection
- Script tags in parameters = XSS attempts
- Multiple admin panel access = targeted attack

### System Logs
- Unexpected user additions = backdoor account
- Unusual sudo usage = privilege escalation
- Service modifications = persistence mechanism
- Unusual processes = malware execution

## ⚠️ Common Pitfalls

- ❌ Analyzing logs in isolation (need correlation)
- ❌ Ignoring timezone differences
- ❌ Not considering false positives
- ❌ Missing low-and-slow attacks
- ❌ Incomplete timeline
- ❌ Not documenting analysis steps

## 📚 Additional Resources

### Log Analysis References
- **SANS Log Analysis Guide**
- **NIST SP 800-92** - Guide to Computer Security Log Management
- **MITRE ATT&CK** - Attack patterns and techniques

### Regular Expressions for Log Analysis
```regex
# IP Address
\b(?:[0-9]{1,3}\.){3}[0-9]{1,3}\b

# Email
\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b

# URL
https?://[^\s]+

# Date (YYYY-MM-DD)
\d{4}-\d{2}-\d{2}

# Time (HH:MM:SS)
\d{2}:\d{2}:\d{2}
```

### SIEM Detection Rules Examples

```yaml
# Brute Force Detection
name: SSH Brute Force Attack
condition: failed_logins > 10 within 5 minutes
action: alert, block_ip

# Privilege Escalation
name: Unusual Sudo Usage
condition: sudo commands from non-admin account
action: alert, investigate

# Data Exfiltration
name: Large Data Transfer
condition: outbound_transfer > 100MB to external IP
action: alert, log_connection
```

## 📤 Submission

Structure:
```
case-3-submission/
├── report/
│   ├── incident-report.pdf
│   ├── executive-summary.pdf
│   └── technical-appendix.pdf
├── evidence/
│   ├── screenshots/
│   ├── log-samples/
│   └── analysis-outputs/
├── ioc/
│   ├── ioc-list.csv
│   ├── siem-rules/
│   └── detection-signatures/
├── timeline/
│   └── incident-timeline.xlsx
└── scripts/
    └── analysis-scripts/
```

**Deadline:** 3 minggu dari pemberian tugas  
**Format:** ZIP file dengan nama: `Case3_NamaAnda_NIM.zip`

---

**Good hunting! 🔍 Remember: The devil is in the details (and the logs)!**


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


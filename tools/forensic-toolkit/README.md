# Forensic Toolkit - Command Line Tools & Resources

## Overview
Collection of command-line tools dan resources untuk membantu analisis digital forensics.

## Recommended Tools

### 1. Hash Calculation
```bash
# MD5
md5sum file.exe
md5 file.exe  # macOS

# SHA256
sha256sum file.exe
shasum -a 256 file.exe  # macOS

# Multiple files
find . -type f -exec md5sum {} \; > hashes.txt
```

### 2. String Extraction
```bash
# Extract ASCII strings
strings file.exe > strings.txt

# Extract unicode strings
strings -el file.exe > unicode_strings.txt

# Minimum length 10
strings -n 10 file.exe > strings_min10.txt
```

### 3. Network Analysis
```bash
# Using tcpdump
sudo tcpdump -r capture.pcap

# Using tshark
tshark -r capture.pcap

# Statistics
capinfos capture.pcap
```

### 4. Log Analysis
```bash
# Search patterns
grep "Failed password" auth.log

# Count occurrences
grep -c "Failed password" auth.log

# Extract IPs
grep "Failed password" auth.log | awk '{print $(NF-3)}' | sort | uniq -c

# Time range
awk '/10:00:00/,/11:00:00/' logfile.log
```

## External Tools (Download Separately)

### Network Forensics
- **Wireshark** - https://www.wireshark.org/
- **NetworkMiner** - https://www.netresec.com/
- **Zeek (Bro)** - https://zeek.org/

### Malware Analysis
- **PEStudio** - https://www.winitor.com/
- **PE-bear** - https://github.com/hasherezade/pe-bear
- **Detect It Easy** - https://github.com/horsicq/Detect-It-Easy
- **Ghidra** - https://ghidra-sre.org/

### Log Analysis
- **Splunk Free** - https://www.splunk.com/
- **ELK Stack** - https://www.elastic.co/elk-stack
- **Graylog** - https://www.graylog.org/

## Useful Command Combinations

### File Analysis
```bash
# File type
file suspicious_file

# File metadata
stat suspicious_file

# File permissions
ls -la suspicious_file
```

### Timeline Creation
```bash
# Sort by timestamp
sort -k1,2 events.log > timeline.txt

# Merge multiple logs by time
sort -m -k1,2 log1.txt log2.txt > combined_timeline.txt
```

## Development

Students are encouraged to create their own analysis scripts using:
- Bash scripting
- Python
- PowerShell
- Any language they're comfortable with

Document any custom tools in your report!

## License
Educational use only.


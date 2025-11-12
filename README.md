# Digital Forensics Case-Based Project

## 📋 Deskripsi
Repository ini berisi kumpulan case-based project untuk pembelajaran Digital Forensics menggunakan data real dari public datasets. Setiap case dirancang untuk mensimulasikan skenario investigasi digital yang nyata.

**⏱️ Durasi Total:** 3 minggu  
**👥 Mode:** Kelompok (3-4 orang)  
**📊 Format:** Setiap kelompok mengerjakan 1 case yang berbeda secara paralel

## 🎯 Tujuan Pembelajaran
Setelah menyelesaikan project ini, mahasiswa diharapkan dapat:
1. Melakukan analisis forensik pada berbagai jenis data digital
2. Mengidentifikasi dan menganalisis bukti digital (digital evidence)
3. Membuat laporan investigasi forensik yang terstruktur
4. Menggunakan tools forensik standar industri
5. Memahami chain of custody dan best practices dalam digital forensics

## 📁 Struktur Repository
```
case-forensics/
├── cases/
│   ├── case-1-network-intrusion/    # Analisis serangan jaringan
│   ├── case-2-malware-analysis/     # Analisis malware
│   └── case-3-log-analysis/         # Analisis log & incident response
├── tools/
│   └── forensic-toolkit/            # Script dan tools bantuan
├── submissions/
│   └── template/                    # Template laporan
└── README.md
```

## 🔍 Daftar Case

**⚠️ CATATAN PENTING:**
- **Setiap kelompok mengerjakan SATU case yang berbeda**
- **Durasi pengerjaan: 3 minggu untuk semua case**
- **Kelompok akan ditugaskan case oleh instruktur**
- **Semua kelompok bekerja secara paralel**

### Case 1: Network Intrusion Analysis
**Tingkat Kesulitan:** Medium  
**Durasi:** 3 minggu  
**Mode:** Kelompok (3-4 orang)  
**Dataset:** PCAP files dari public datasets (CICIDS2017, UNSW-NB15)

**Skenario:**
Sebuah perusahaan mengalami insiden keamanan. Kelompok Anda ditugaskan untuk menganalisis network traffic capture untuk mengidentifikasi:
- Jenis serangan yang terjadi
- Source dan destination dari serangan
- Timeline serangan
- Dampak yang ditimbulkan

### Case 2: Malware Analysis
**Tingkat Kesulitan:** Hard  
**Durasi:** 3 minggu  
**Mode:** Kelompok (3-4 orang)  
**Dataset:** Malware samples dari VirusTotal/MalwareBazaar

**Skenario:**
Sistem terinfeksi malware yang tidak terdeteksi. Kelompok Anda melakukan analisis untuk:
- Static analysis (tanpa eksekusi)
- Dynamic analysis (behavior analysis)
- Network indicators of compromise (IoC)
- Rekomendasi mitigasi

### Case 3: Log Analysis & Incident Response
**Tingkat Kesulitan:** Medium  
**Durasi:** 3 minggu  
**Mode:** Kelompok (3-4 orang)  
**Dataset:** Security logs dari public datasets

**Skenario:**
Terdapat aktivitas mencurigakan pada server. Kelompok Anda menganalisis log files untuk:
- Identifikasi unauthorized access
- Timeline aktivitas
- User accounts yang terlibat
- Rekomendasi security measures

## 🛠️ Tools yang Dibutuhkan

### Network Analysis
- Wireshark
- tcpdump
- NetworkMiner
- Zeek (Bro)

### Malware Analysis
- VirusTotal
- PEiD / pestudio
- Process Monitor
- IDA Free / Ghidra
- Cuckoo Sandbox (optional)

### Log Analysis
- Python (pandas, matplotlib)
- ELK Stack (optional)
- Splunk (optional)
- grep, awk, sed

## 📝 Format Laporan

Setiap case harus diserahkan dengan laporan yang berisi:

1. **Executive Summary**
   - Ringkasan kasus dan temuan utama

2. **Case Details**
   - Background
   - Scope investigasi
   - Tools yang digunakan

3. **Methodology**
   - Langkah-langkah investigasi
   - Teknik analisis yang digunakan

4. **Findings & Analysis**
   - Evidence yang ditemukan
   - Analisis detail
   - Screenshots dan visualisasi

5. **Timeline**
   - Kronologi kejadian

6. **Indicators of Compromise (IoC)**
   - IP addresses
   - File hashes
   - Domain names
   - dll

7. **Conclusions & Recommendations**
   - Kesimpulan
   - Rekomendasi tindakan

8. **References**

## 📊 Rubrik Penilaian

| Aspek | Bobot | Kriteria |
|-------|-------|----------|
| Metodologi | 20% | Penggunaan metodologi forensik yang tepat, kolaborasi kelompok |
| Analisis Teknis | 30% | Kedalaman dan akurasi analisis |
| Evidence Collection | 20% | Identifikasi dan dokumentasi bukti |
| Laporan | 20% | Struktur, kejelasan, dan profesionalitas |
| Presentasi | 10% | Penyampaian hasil dan Q&A |

**Total: 100%**

### Penilaian Kelompok:
- **Nilai Kelompok (80%):** Berdasarkan hasil kerja kelompok
- **Nilai Individu (20%):** Berdasarkan kontribusi dan pemahaman individu

### Kriteria Penilaian Detail:
- **A (85-100):** Excellent - Analisis komprehensif dengan metodologi yang tepat, kolaborasi solid
- **B (70-84):** Good - Analisis baik dengan beberapa area improvement
- **C (60-69):** Satisfactory - Analisis memadai namun kurang mendalam
- **D (<60):** Needs Improvement - Analisis tidak lengkap atau tidak akurat

## 🚀 Cara Memulai

1. Clone repository ini
2. Pilih case yang akan dikerjakan
3. Baca scenario dan requirements dengan teliti
4. Download dataset yang diperlukan (link ada di folder masing-masing case)
5. Setup tools yang dibutuhkan
6. Mulai investigasi
7. Dokumentasikan setiap langkah
8. Buat laporan menggunakan template yang disediakan
9. Submit melalui folder submissions

## ⚠️ Disclaimer

- Semua data yang digunakan adalah public datasets untuk tujuan edukasi
- Jangan gunakan tools dan teknik forensik untuk aktivitas ilegal
- Selalu patuhi hukum dan etika dalam cybersecurity
- Malware samples harus ditangani dengan hati-hati dalam isolated environment

## 📚 Resources Tambahan

### Public Datasets
- [CICIDS2017](https://www.unb.ca/cic/datasets/ids-2017.html)
- [UNSW-NB15](https://research.unsw.edu.au/projects/unsw-nb15-dataset)
- [MalwareBazaar](https://bazaar.abuse.ch/)
- [SecRepo](https://www.secrepo.com/)
- [Malware Traffic Analysis](https://www.malware-traffic-analysis.net/)

### Learning Resources
- SANS Digital Forensics & Incident Response
- NIST Computer Forensics Tool Testing
- OWASP Testing Guide
- The Art of Memory Forensics

## 👥 Kontribusi
Untuk pertanyaan atau diskusi, silakan buat issue atau hubungi instruktur.

## 📄 License
Educational purposes only.

---
**Update Terakhir:** November 2025


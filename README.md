# 🏁 Tugas Akhir (TA) - Final Project

**Nama Mahasiswa**: Java Kanaya Prada  
**NRP**: 5025211112  
**Judul TA**: Rekonstruksi Forensik pada Sistem Operasi Linux Berbasis Serialisasi Data YAML  
**Dosen Pembimbing**: Hudan Studiawan, S.Kom., M.Kom.,Ph.D.  
**Dosen Ko-pembimbing**: Dr. Baskoro Adi Pratomo., S.Kom., M.Kom.

---

## 📺 Demo Aplikasi  

[![Demo Aplikasi](https://i.ytimg.com/vi/zIfRMTxRaIs/maxresdefault.jpg)](https://www.youtube.com/watch?v=VIDEO_ID)  
*Klik gambar di atas untuk menonton demo*

---

## 🛠 Panduan Instalasi & Menjalankan Software

### Prasyarat

- Anaconda atau Miniconda
- Git

### Langkah-langkah

1. **Buat dan Aktifkan Environment**

   ```bash
   conda create --name sigmadft python=3.12
   conda activate sigmadft
   ```

2. **Clone dan Instalasi Proyek**

   ```bash
   git clone https://github.com/yourusername/sigmadft.git
   cd sigmadft
   pip install .
   ```

   Untuk mode pengembangan (editable):

   ```bash
   pip install -e .
   ```

3. **Verifikasi Instalasi**

   ```bash
   pip list | grep sigmadft
   sigmadft -h
   ```

4. **Menjalankan Aplikasi**

   ```bash
   sigmadft -i timeline.csv -o results.json
   ```

5. **Contoh Perintah Tambahan**

   ```bash
   sigmadft -i timeline.csv -o results.json -t google-search
   sigmadft -i timeline.csv -o results.json -t all-linux-security
   ```

---

## 📄 Dokumentasi Teknis

### Input Format

SigmaDFT menerima file CSV dengan format Plaso, dan kolom berikut:

- `datetime`: Timestamp kejadian  
- `timestamp_desc`: Deskripsi waktu  
- `source`: Sumber event  
- `source_long`: Informasi sumber yang lebih detail  
- `message`: Pesan / evidence event  
- `parser`: Parser yang digunakan  
- `display_name`: Path atau nama file  
- `tag`: Tag event  

### Output Format

Hasil analisis diekspor dalam format JSON berisi:

- Metadata event  
- High-level events hasil rekonstruksi  
- Bukti pendukung (supporting evidence)  
- Informasi kecocokan rule  
- Kategori event  

### Rule Structure

Contoh struktur aturan berbasis YAML:

```yaml
title: "Example Detection Rule"
id: "example-001"
description: "Detects example activities"
category: "example"
detection:
  keywords:
    - "example_keyword"
    - "another_keyword"
  condition: "keywords"
high_level_event:
  type: "Example Activity"
  description: "User performed {example_key}"
  keys:
    - name: "example_key"
      source: "extract_example_data"
```

### Available Event Types

| Tipe | Deskripsi |
|------|-----------|
| `google-search` | Aktivitas pencarian Google |
| `bing-search` | Aktivitas pencarian Bing |
| `web-visits` | Kunjungan web umum |
| `youtube-watch` | Aktivitas menonton YouTube |
| `all-web-activity` | Semua aktivitas web |
| `user-add` | Pembuatan akun baru |
| `user-mod` | Modifikasi akun |
| `account-management-activity` | Semua aktivitas akun |
| `auth-failure` | Kegagalan autentikasi |
| `session-opened` | Login sesi |
| `authentication-activity` | Semua aktivitas autentikasi |
| `web-shell` | Deteksi web shell |
| `security-tools` | Tools yang menonaktifkan syslog |
| `suspicious-dns` | Aktivitas DNS mencurigakan |
| `crontab-modification` | Modifikasi crontab |
| `ftp-errors` | Error mencurigakan dari VSFTPD |
| `suspicious-logs` | Log shell mencurigakan |
| `all-linux-security` | Semua event keamanan Linux |
| `all` | Semua rule tersedia |

### Example Analysis

```bash
# Analisis aktivitas web
sigmadft -i plaso_timeline.csv -o web_analysis.json -t all-web-activity

# Deteksi masalah autentikasi
sigmadft -i auth_logs.csv -o auth_analysis.json -t authentication-activity

# Analisis keamanan menyeluruh
sigmadft -i full_timeline.csv -o security_analysis.json -t all-linux-security
```

---

## ⁉️ Pertanyaan?

Hubungi:

- Penulis: [javakanaya@outlook.com](mailto:javakanaya@outlook.com)  
- Pembimbing Utama: [hudan@its.ac.id](mailto:hudan@its.ac.id)

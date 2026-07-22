# Submit SISKA Activity

Agent Skill untuk menambahkan dan memverifikasi data **Aktivitas dan Prestasi** mahasiswa pada STT-NF SISKA melalui sesi Chrome yang sudah terautentikasi. Skill memakai format `SKILL.md` agar dapat digunakan oleh OpenAI Codex, Claude Code, dan agent lain yang mendukung standar Agent Skills.

**Author:** Muhamad Aldi Ramdani

## Kompatibilitas Agent

Folder `submit-siska-activity` mengikuti [spesifikasi terbuka Agent Skills](https://agentskills.io/specification): sebuah direktori skill dengan `SKILL.md`, YAML frontmatter, dan instruksi Markdown. Agent yang mendukung standar ini dapat memakai workflow yang sama.

- **OpenAI Codex:** memakai `SKILL.md` sebagai instruksi dan `agents/openai.yaml` sebagai metadata antarmuka Codex.
- **Claude Code:** membaca `SKILL.md` dari direktori skill personal atau proyek. Lihat [dokumentasi Skills Claude Code](https://code.claude.com/docs/en/skills).
- **Claude Agent SDK:** dapat memuat skill dari sumber konfigurasi user atau project.
- **Agent lain:** dapat memakai folder ini jika implementasinya mendukung standar Agent Skills atau dapat membaca instruksi Markdown dari `SKILL.md`.

Otomatisasi membutuhkan integrasi browser, computer-use, atau tool GUI yang dapat memakai sesi Chrome lokal dan mengunggah file. Agent tanpa tool tersebut dapat mengikuti skill sebagai panduan interaktif.

## Fitur

- Membuka halaman Aktivitas dan Prestasi SISKA.
- Memeriksa kemungkinan data duplikat sebelum membuat entri baru.
- Memilih periode akademik serta Jenis & Kelompok Aktivitas.
- Mengisi nama aktivitas Indonesia dan Inggris, tingkat prestasi, jenis kegiatan, penyelenggara, dan tanggal.
- Mengunggah sertifikat atau dokumen pendukung.
- Meminta konfirmasi sebelum penyimpanan final.
- Memverifikasi hasil pada periode akademik yang benar setelah data disimpan.
- Menghentikan proses dengan aman jika login, file, tanggal, atau validasi SISKA bermasalah.

## Persyaratan

- Agent yang dapat membaca `SKILL.md` atau mendukung standar Agent Skills.
- Integrasi browser atau computer-use dengan akses ke sesi Chrome lokal.
- Google Chrome dengan akun SISKA yang sudah login.
- Hak akses untuk menambahkan Aktivitas dan Prestasi pada SISKA.
- File pendukung berformat JPG, JPEG, atau PDF sesuai batas ukuran yang ditampilkan SISKA.

Skill tidak menyimpan username, password, kode OTP, atau data login SISKA.

## Instalasi

### Clone repository

```bash
git clone https://github.com/aldiramdhan/submit-siska-activity.git
cd submit-siska-activity
```

### OpenAI Codex

Salin folder skill ke direktori skill personal Codex:

```bash
mkdir -p ~/.codex/skills
cp -R submit-siska-activity ~/.codex/skills/submit-siska-activity
```

Pastikan file utama tersedia:

```bash
test -f ~/.codex/skills/submit-siska-activity/SKILL.md && echo "Skill terpasang"
```

Mulai task Codex baru agar daftar skill dimuat ulang.

### Claude Code

Pasang sebagai skill personal agar tersedia di semua proyek:

```bash
mkdir -p ~/.claude/skills
cp -R submit-siska-activity ~/.claude/skills/submit-siska-activity
```

Untuk membatasi skill pada satu proyek, salin ke direktori proyek:

```bash
mkdir -p .claude/skills
cp -R submit-siska-activity .claude/skills/submit-siska-activity
```

Claude Code dapat mendeteksi perubahan pada direktori skill yang sudah dipantau. Restart Claude Code jika direktori `~/.claude/skills` baru dibuat setelah sesi dimulai.

### Agent lain

Salin seluruh folder `submit-siska-activity` ke direktori skill yang ditentukan oleh agent Anda. Pertahankan nama folder dan file `SKILL.md`. File `agents/openai.yaml` khusus untuk antarmuka Codex; agent lain dapat mengabaikannya.

Jika agent belum mendukung Agent Skills, berikan isi `SKILL.md` sebagai instruksi sistem atau workflow, lalu sediakan tool browser yang dibutuhkan.

## Cara Menggunakan

| Agent | Cara memanggil |
|---|---|
| OpenAI Codex | `Use $submit-siska-activity to add and verify an activity or achievement entry in SISKA.` |
| Claude Code | `/submit-siska-activity` atau permintaan natural yang cocok dengan deskripsi skill |
| Agent lain | Gunakan mekanisme pemanggilan skill milik platform atau minta agent menjalankan `submit-siska-activity` |

Contoh untuk Codex:

```text
Use $submit-siska-activity to add and verify an activity or achievement entry in SISKA.
```

Contoh permintaan natural untuk agent:

```text
Tambahkan sertifikasi saya ke Aktivitas dan Prestasi SISKA menggunakan skill submit-siska-activity.
```

Agent akan meminta data yang masih kurang sebelum mengisi formulir. Siapkan:

- periode akademik;
- pilihan tepat untuk Jenis & Kelompok Aktivitas;
- nama aktivitas dalam bahasa Indonesia;
- nama aktivitas dalam bahasa Inggris, jika tersedia;
- tingkat prestasi dan peringkat, jika relevan;
- jenis kegiatan: Akademik atau Non Akademik;
- jabatan, lokasi, dan penyelenggara, jika ada;
- tanggal mulai dan akhir dalam format `DD-MM-YYYY`;
- jenis dokumen pendukung;
- path file JPG, JPEG, atau PDF yang akan diunggah;
- nomor dan tanggal SK atau tautan pendukung, jika relevan.

## Alur Kerja

1. Membuka daftar Aktivitas dan Prestasi pada sesi Chrome yang sudah login.
2. Memilih periode akademik dan mencari data dengan nama serta tanggal yang sama.
3. Membuka formulir `Tambah`.
4. Memilih Jenis & Kelompok Aktivitas yang tepat dan memeriksa poinnya.
5. Mengisi seluruh data aktivitas dan tanggal.
6. Memilih jenis dokumen lalu mengunggah file pendukung.
7. Meninjau data dan meminta konfirmasi pengguna.
8. Menyimpan melalui dialog `Ya, Yakin`.
9. Kembali ke daftar, memilih ulang periode akademik, dan memverifikasi entri.

Skill tidak akan membuat entri kedua secara otomatis jika hasil pertama belum ditemukan.

## Keamanan dan Privasi

- Lakukan login langsung melalui halaman SISKA; jangan kirim kredensial melalui chat.
- Tinjau data dan nama file sebelum menyetujui penyimpanan.
- Jangan unggah dokumen yang tidak diperlukan atau mengandung data sensitif berlebih.
- Skill tidak menghapus atau menimpa entri Aktivitas dan Prestasi lainnya.
- Repository ini tidak memuat data rekaman pengguna, NIM, kredensial, sertifikat, maupun nilai contoh pribadi.

## Troubleshooting

### Skill tidak terdeteksi

Periksa path instalasi sesuai agent yang digunakan:

```text
~/.codex/skills/submit-siska-activity/SKILL.md
~/.claude/skills/submit-siska-activity/SKILL.md
.claude/skills/submit-siska-activity/SKILL.md
```

Metadata antarmuka Codex berada di:

```text
~/.codex/skills/submit-siska-activity/agents/openai.yaml
```

Restart agent jika direktori skill baru dibuat setelah sesi berjalan.

### SISKA meminta login

Login sendiri melalui Chrome, kemudian minta agent melanjutkan proses. Jangan berikan password atau OTP kepada skill.

### File gagal diunggah

Gunakan JPG, JPEG, atau PDF dan pastikan ukurannya tidak melebihi batas yang terlihat pada formulir SISKA. Rekaman awal menampilkan batas sekitar 2,1 MB, tetapi selalu ikuti batas terbaru pada halaman.

### Data tidak terlihat setelah disimpan

Pilih kembali periode akademik yang digunakan, refresh halaman, dan cari berdasarkan nama aktivitas. Jangan membuat entri baru sebelum memastikan entri sebelumnya benar-benar gagal tersimpan.

## Struktur Repository

```text
.
├── README.md
└── submit-siska-activity
    ├── SKILL.md
    └── agents
        └── openai.yaml
```

## Author

Created by **Muhamad Aldi Ramdani**.

## Lisensi

Belum ada lisensi penggunaan yang ditetapkan. Repository publik tidak otomatis memberikan izin untuk menyalin, memodifikasi, atau mendistribusikan ulang karya.

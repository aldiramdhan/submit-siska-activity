# Submit SISKA Activity

Skill Codex untuk menambahkan dan memverifikasi data **Aktivitas dan Prestasi** mahasiswa pada STT-NF SISKA melalui sesi Chrome yang sudah terautentikasi.

**Author:** Muhamad Aldi Ramdani

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

- Codex Desktop yang mendukung custom skills.
- Google Chrome dengan akun SISKA yang sudah login.
- Hak akses untuk menambahkan Aktivitas dan Prestasi pada SISKA.
- File pendukung berformat JPG, JPEG, atau PDF sesuai batas ukuran yang ditampilkan SISKA.

Skill tidak menyimpan username, password, kode OTP, atau data login SISKA.

## Instalasi

1. Clone repository:

   ```bash
   git clone https://github.com/aldiramdhan/submit-siska-activity.git
   cd submit-siska-activity
   ```

2. Salin folder skill ke direktori skill Codex:

   ```bash
   mkdir -p ~/.codex/skills
   cp -R submit-siska-activity ~/.codex/skills/submit-siska-activity
   ```

3. Pastikan file utama tersedia:

   ```bash
   test -f ~/.codex/skills/submit-siska-activity/SKILL.md && echo "Skill terpasang"
   ```

4. Mulai task baru di Codex agar daftar skill dimuat ulang.

## Cara Menggunakan

Panggil skill secara eksplisit:

```text
Use $submit-siska-activity to add and verify an activity or achievement entry in SISKA.
```

Contoh dalam bahasa Indonesia:

```text
Gunakan $submit-siska-activity untuk menambahkan sertifikasi saya ke Aktivitas dan Prestasi SISKA.
```

Codex akan meminta data yang masih kurang sebelum mengisi formulir. Siapkan:

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

Pastikan struktur instalasi berikut tersedia, lalu mulai task Codex baru:

```text
~/.codex/skills/submit-siska-activity/SKILL.md
~/.codex/skills/submit-siska-activity/agents/openai.yaml
```

### SISKA meminta login

Login sendiri melalui Chrome, kemudian minta Codex melanjutkan proses. Jangan berikan password atau OTP kepada skill.

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

---
name: submit-siska-activity
description: Add and verify student activity or achievement records in STT-NF SISKA through an authenticated browser session. Use when the user asks Codex to submit, upload, or register an Aktivitas dan Prestasi entry, including its academic period, activity category, bilingual name, achievement details, dates, organizer, and supporting certificate or document.
---

# Submit SISKA Activity

Create one activity or achievement entry in SISKA and verify that it appears in the intended academic period. Use the user's existing authenticated Chrome session; never request, expose, or store SISKA credentials.

## Collect the entry

Obtain these values before editing the form:

- Academic period.
- Exact `Jenis & Kelompok Aktivitas` choice.
- Indonesian activity name and, when available, English activity name.
- Achievement level and optional ranking.
- Activity type: `Akademik` or `Non Akademik`.
- Optional position, location, organizer, decree number/date, and supporting link.
- Start date and end date in `DD-MM-YYYY` format.
- Supporting-document type and local JPG, JPEG, or PDF file.

Ask only for required values that are missing. Infer names or translations only when the user explicitly permits it. Confirm that the start date is not after the end date and that the supporting file is no larger than the limit shown by SISKA (approximately 2.1 MB in the recorded workflow).

## Submit the entry

1. Open `https://siska.nurulfikri.ac.id/siakad/list_aktivitasmhs` in the user's authenticated Chrome session. If SISKA requires sign-in, pause and ask the user to sign in directly.
2. Select the intended academic period and search for an existing row with the same activity name and date. If a likely duplicate exists, stop and ask whether to continue.
3. Click `Tambah` to open the detail form.
4. In `Jenis & Kelompok Aktivitas`, click the search button, locate the exact requested row, verify its activity type and points, then click that row's `Pilih` checkmark.
5. Set `Periode Akademik` to the requested period. Do not rely on the default value.
6. Fill `Nama Aktivitas` and `Nama Aktivitas (En)` without copying example values from prior records.
7. Select `Tingkat Prestasi`. Set `Peringkat` only when it applies. Select `Jenis Kegiatan`, then fill any provided position, location, and organizer values.
8. Fill `Tanggal Mulai Aktivitas` and `Tanggal Akhir Aktivitas`. Re-read both fields after date-picker or keyboard entry to catch date-format changes.
9. Select `Jenis Dokumen Pendukung`, fill conditional decree fields when applicable, and upload the supplied file. Confirm that the chosen filename appears in the form.
10. Review the category, period, names, achievement details, dates, organizer, and filename. Ask for final confirmation unless the user already explicitly authorized immediate submission of these exact values.
11. Click `Simpan`, then click `Ya, Yakin` in the SISKA confirmation dialog. Wait for the save to finish; do not click the button repeatedly.

## Verify the result

1. Confirm that SISKA displays the saved detail state or assigns a detail URL.
2. Click `Kembali ke Daftar`.
3. Select the entry's academic period again, because the list may reset to a different period.
4. Search or refresh until the row appears. Verify the activity name, date, points, and validation status.
5. Report the saved result and current status. If the row is not found, report the mismatch and do not create a second entry automatically.

## Handle failures

- Pause for user authentication instead of handling passwords or one-time codes.
- Correct missing required fields or rejected date formats before resubmitting.
- Ask for a smaller or supported file when upload validation fails.
- Preserve the form and report the visible message when SISKA rejects the save.
- Never delete or overwrite another activity while completing this workflow.

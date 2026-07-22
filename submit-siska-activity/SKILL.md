---
name: submit-siska-activity
description: Inspect certificates and supporting files, plan, submit, and verify one or more STT-NF SISKA student activity or achievement records through the user's authenticated Chrome session. Use for SISKA Aktivitas dan Prestasi work involving document-derived dates, Indonesian and English activity names, academic-period inference, activity-category and point selection, PDF preparation or upload, duplicate checks, batch submission, and post-save verification.
---

# Submit SISKA Activity

Submit SISKA activities through the user's existing authenticated Chrome session. Never request, expose, or store credentials. Treat every save as a production write: preflight it, save it once, and verify it before continuing.

## Load the relevant references

- Read [references/activity-catalog.md](references/activity-catalog.md) when selecting an academic period, dropdown value, activity category, or point value.
- Read [references/chrome-workflow.md](references/chrome-workflow.md) before controlling the SISKA form; it records stable selectors and UI failure modes discovered in a successful workflow.
- Read [references/batch-submission.md](references/batch-submission.md) for two or more entries, document conversions, previews, and final audits.

## Build the submission record

Inspect the supporting document before opening the form. Record:

- Absolute file path and exact filename.
- Start and end dates in `DD-MM-YYYY`. If the document shows one activity date, set both dates to that value.
- Academic period derived from the start date and verified against the period reference. Do not guess in July/August overlap cases.
- Indonesian `Nama Aktivitas` that accurately matches the certificate or activity.
- Natural English `Nama Aktivitas (En)`. Translate when the user permits inference; preserve product, company, program, and credential names.
- Exact activity category and expected points.
- Achievement level, optional rank, `Akademik` or `Non Akademik`, organizer, and any supplied position, location, decree, link, or responsible person.
- Supporting-document type.

Ask only for material values that cannot be established from the document, the supplied knowledge base, or explicit user instructions. Reject a start date later than the end date.

## Prepare supporting files

Accept only formats shown by SISKA: JPG, JPEG, or PDF. Prefer PDF for certificates when the user requests it.

- Keep every source file unchanged.
- Create converted or compressed copies with descriptive filenames.
- Keep each upload at or below the current form limit; the verified workflow displayed `2.097152 MB` (2,097,152 bytes).
- Render and visually inspect every generated PDF for cropping, blur, missing pages, or rotation errors.
- Confirm the final absolute path, basename, format, and byte size before browser automation.

Use the `pdf` skill when PDF conversion, compression, rendering, or visual verification is required.

## Preflight SISKA

1. Open `https://siska.nurulfikri.ac.id/siakad/list_aktivitasmhs` in the active authenticated Chrome session.
2. If redirected to sign-in, pause and ask the user to sign in directly.
3. Select the intended period explicitly; the page default is not authoritative.
4. Search for a row matching period, activity name, and start date. Stop on a likely duplicate unless the user explicitly authorizes another entry.
5. For a batch, preflight all involved periods and present one complete preview before the first save, unless the user already approved those exact entries.

## Fill and review the form

1. Click `Tambah` and wait for the form to finish loading.
2. Select the exact `Jenis & Kelompok Aktivitas` row. Verify its label and points after the modal closes.
3. Select `Periode Akademik`; never rely on its default.
4. Fill both activity-name fields, achievement level, optional rank, activity type, and supplied optional fields.
5. Select start and end dates with the SISKA datepicker. Re-read both rendered values after selection. For a single-day activity, independently select the same date in both fields.
6. Select the supporting-document type before uploading; `Choose File` can remain disabled until this is set.
7. Upload the absolute local path through the file chooser and verify the selected basename.
8. Compare every populated field with the submission record. Leave unspecified optional fields blank.
9. Ask for final confirmation unless the user already authorized saving these exact values.

Follow the locator and control guidance in [references/chrome-workflow.md](references/chrome-workflow.md). If a date or category widget enters an inconsistent state, abandon the unsaved form, reopen a clean form, and refill it rather than forcing a questionable value.

## Save and verify

1. Click `Simpan` once, then `Ya, Yakin` once.
2. Wait for `Penambahan data Aktivitas Mahasiswa berhasil` or the saved detail state.
3. Verify the detail view: category and points, period, both names, level, rank, activity type, organizer/location, both dates, document type, exact filename, and validation status.
4. Click `Kembali ke Daftar` and reselect the intended period because SISKA may reset it.
5. Verify exactly one row with the expected name, displayed start date, points, and `Belum Divalidasi` status.
6. If any detail or list check fails, stop. Do not create a replacement or the next batch entry automatically.

For a batch, process entries sequentially and perform the full detail-and-list verification after each save. Run the cross-period audit in [references/batch-submission.md](references/batch-submission.md) when all entries finish.

## Handle failures

- Preserve visible SISKA error messages and report the field or stage that failed.
- Pause for authentication; never handle passwords or one-time codes.
- Reopen a clean unsaved form when a modal or datepicker becomes stale.
- Recreate an unsupported, oversized, cropped, or blurry document copy without modifying its source.
- Never delete, overwrite, or edit an unrelated activity.
- Never retry a save when its outcome is uncertain; inspect the list first.

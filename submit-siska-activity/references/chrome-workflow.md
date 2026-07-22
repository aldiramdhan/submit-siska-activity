# Chrome Workflow Reference

Use the `chrome:control-chrome` skill and its persistent browser client. Keep one claimed tab for the workflow so authentication and page state remain stable.

## Stable pages and controls

| Purpose | URL or selector |
|---|---|
| Activity list | `https://siska.nurulfikri.ac.id/siakad/list_aktivitasmhs` |
| New/detail form | `/siakad/data_aktivitasmhs` |
| Period | `#periode` |
| Category stored value | `#idkelompokaktivitas` |
| Category display/search | `#idkelompokaktivitas_label` and its sibling button |
| Indonesian name | `#nama` |
| English name | `#namaen` |
| Achievement level | `#idtingkatprestasi` |
| Rank | `#idperingkat` |
| Academic radio | `#isaktivitasakademik_1` |
| Position / location / organizer | `#jabatan`, `#tempat`, `#penyelenggara` |
| Start / end date | `#tgl`, `#tglakhir` |
| Document type | `#idjenisdokumen` |
| File input | `input[name="file"]` |
| Supporting link | `#linkdokumen` |
| Save | `button.btn.btn-success.btn-sm` |

Treat these as observed selectors, not a contract. Reinspect the rendered page when a selector is absent or non-unique.

## Category modal

1. Click the search button next to `#idkelompokaktivitas_label` and allow the option table to load.
2. Locate the exact row text and points. Known option buttons used `data-target` containing `idkelompokaktivitas::<ID>`.
3. The page can retain hidden copies of the modal. A matching locator may therefore return multiple nodes and the first node can be hidden.
4. Inspect visibility and click the one visible matching option. Do not force-click a hidden copy.
5. If no copy is visible after the first load, reopen the search once, wait, and scan visible matches again.
6. Verify the display field contains the expected complete label and point value after selection.

## Datepicker

Prefer the visual Bootstrap datepicker over keyboard entry. A typed end date was observed to disappear on blur even when it initially rendered correctly.

1. Click the date input only when no datepicker is visible; clicking an already-open input can toggle it closed.
2. Click the days-view switch, then the months-view switch to reach years.
3. Select the exact year, exact three-letter month, and then the day.
4. In the day grid use `.datepicker-days td.day:not(.old):not(.new)` so adjacent-month dates are excluded.
5. Compare trimmed cell text exactly. Substring matching for day `1` also matches `10` through `19`.
6. Select the start and end fields independently. For one-day activity, choose the same day twice.
7. Re-read both rendered values in `DD-MM-YYYY` after all other controls are filled.

If the picker becomes stale or stops opening, return to the list without saving and open a clean form. Do not mutate a questionable date through hidden DOM state.

## File chooser

1. Select the document type first; confirm `Choose File` is enabled.
2. Start waiting for `filechooser` before clicking `Choose File`.
3. Pass the absolute local path to the chooser's `setFiles` operation.
4. Verify the file input basename. Browsers normally expose `C:\\fakepath\\<filename>`; compare only `<filename>`.
5. The accessible snapshot may omit the chosen filename. The detail view after save must show the exact document link.

## Save verification

- Click `Simpan`, verify exactly one `Ya, Yakin` button, and click it once.
- Navigation can make immediate selector evaluation time out. Wait briefly and inspect the new snapshot instead of clicking again.
- Require the success text `Penambahan data Aktivitas Mahasiswa berhasil` and verify all detail fields.
- Return to the list, reselect `#periode`, and inspect `table tbody tr`.
- Accept success only when exactly one row contains the expected activity name, localized displayed start date, point value, and `Belum Divalidasi`.

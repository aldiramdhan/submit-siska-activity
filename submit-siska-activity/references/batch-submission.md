# Batch Submission Reference

Use this reference whenever the user supplies two or more activities.

## Submission manifest

Build one immutable record per entry before the first save:

| Field | Requirement |
|---|---|
| Sequence | Stable number used in progress and failure reports |
| Indonesian and English names | Exact final strings |
| Start and end dates | `DD-MM-YYYY`; repeat a single date |
| Period | Exact SISKA label or verified option value |
| Category and points | Exact visible category label and expected points |
| Level, rank, activity type | Explicit dropdown/radio choices |
| Optional fields | Organizer, location, position, decree, link, responsible person |
| Document | Absolute path, exact basename, format, and byte size |

Present the complete manifest as a preview. One explicit approval covers the manifest exactly as shown; ask again only when a material value changes.

## Document preparation

- Create converted or compressed derivatives before opening SISKA.
- Preserve originals and save derivatives beside the source when the user requests that location.
- Prefer deterministic descriptive filenames.
- Keep each file at or below 2,097,152 bytes unless the live form shows a different limit.
- Render and visually inspect every derivative before it enters the manifest.

## Execution contract

1. Scan every involved period for duplicates before opening the first form.
2. Process sequentially; do not parallelize writes to SISKA.
3. Precheck every rendered field and selected filename against the manifest.
4. Save once.
5. Verify the saved detail and then the period-filtered list.
6. Do not open the next form until the current row appears exactly once.
7. Stop the entire batch on upload failure, save rejection, uncertain navigation, field mismatch, missing row, or duplicate row.

## Final audit

After the last entry:

1. Group the manifest by academic period.
2. Select each period once and read its table rows.
3. For every manifest entry, require exactly one row containing its name, localized start date, expected points, and validation status.
4. Report verified entry count, any failures, involved periods, and the expected total points.
5. Do not claim completion when any audit failure remains.

The list shows the start date, not necessarily the end date or filename. Those must already have been verified on the detail page immediately after each save.

## [v5.5] - 2026-02-23

### Fixed
- Resolved "No valid POs found to transform" error for multi-record-type EDI formats
- Added PO number forward-fill pre-processing so detail (D) rows inherit the PO number from their parent header (H) row before grouping
- No impact on existing vendor formats — forward-fill is inert when PO number is already populated on every row

### Added
- Support for Princess Auto EDI format (H/D/S multi-record-type structure)

### Notes
- Princess Auto CSV ships with a one-column offset in ship-to fields starting at `Ship To Name` — the actual company name lands in `Ship To Address 1`, address in `Ship to address 2`, and so on. Map accordingly when saving the format.
- `Record Type` column (values H/D/S) recommended as the content identifier when saving the Princess Auto format to distinguish it from any future formats with identical column structures.
- `Payment Terms` may be split across `Payment Terms Desc` and `Contact Phone` columns due to a comma in the source data causing a CSV parse split — treat `Contact Phone` as payment terms overflow if needed.

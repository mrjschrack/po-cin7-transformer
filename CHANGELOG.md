# Changelog

## [v5.7] - 2026-02-25

### Changes
- Academy ship date range parsing
- Format export/import in JSON
- Improved content identifier disambiguation
- Fixed `createFingerprint()` to filter out empty column names before generating fingerprints — trailing commas in SPS CSV exports were producing a leading `|` artifact that caused format mismatches
- Updated all 7 stored format fingerprints to match the corrected logic (Zoro, Tractor Supply, Princess Auto, Fastenal, Academy Sports, Bass Pro, Scheels)
- Tractor Supply fingerprint updated to reflect new columns added by TSC to their SPS export: additional address 1/2/city/state/country/name and catalog price

## [v5.6] - 2026-02-23

### Changes
- Global ship date resolution logic: never-in-the-past rule with 7-business-day fallback from order entry date

## [v5.4] - 2025-02-19

### Current Features
- Smart format recognition via file fingerprinting with fallback to manual column mapping
- Company name matching using Cin7 contact exports, with city/state as tiebreaker for multiple locations
- Company name aliases for resolving recurring vendor naming inconsistencies
- Delivery instruction and internal comments templates with placeholder support
- Batch processing that groups by PO number and combines into a single import file
- Similarity threshold set to >=0.65 to accommodate store number suffixes
- Format management system for saving, editing, and deleting custom configurations
- Dark theme interface with Space Mono font and card-based layout
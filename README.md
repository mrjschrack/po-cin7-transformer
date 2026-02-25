# PO Transformer Tool

A standalone browser-based tool that converts retail purchase orders from various vendor formats into Cin7-ready import files. Built to streamline warehouse operations by eliminating manual data entry.

## Features

- Automatic vendor format recognition via fingerprinting
- Smart company name matching using Cin7 contact exports
- Company name alias system for handling vendor-specific naming inconsistencies
- Delivery instruction templates with dynamic placeholders
- Internal comments templates
- Batch processing of multiple POs into a single Cin7 import file
- Save, edit, and delete custom format configurations

## Supported Vendors

- Scheels
- Brownells
- Academy Sports
- Tractor Supply
- Zoro
- Fastenal
- Bass Pro
- Princess Auto *(see format notes below)*

## Usage

Open `po-transformer.html` in any modern browser. No installation or server required.

1. (Optional) Load a Cin7 contact export for smart company matching
2. Drag and drop one or more PO files onto the tool
3. Map columns if prompted for an unrecognized format
4. Export the Cin7-ready CSV

---

### Vendor Format Notes

#### Princess Auto
Princess Auto uses a multi-record-type EDI structure where each PO is spread across multiple row types:

| Record Type | Contains |
|---|---|
| `H` | PO number, company, ship-to address, dates, carrier, payment terms |
| `D` | Line items — SKU, qty, price, description |
| `S` | Summary row (line item count) — ignored during transform |

**Column mapping quirks:**
- `Ship To Name` column is empty — the actual company name is one column to the right in `Ship To Address 1`
- All subsequent ship-to fields are similarly offset by one column
- `Payment Terms` may be split across `Payment Terms Desc` and `Contact Phone` due to a comma in the source data

**Recommended mapping:**

| Cin7 Field | Map To |
|---|---|
| Order Ref | PO Number |
| Company | Ship To Address 1 *(contains company name)* |
| Delivery Address | Ship to address 2 *(contains street address)* |
| Delivery City | Ship To State *(contains city)* |
| Delivery State | Ship to Zip *(contains province)* |
| Delivery Zip | Ship To Country *(contains postal code)* |
| Item Code | Stock Keeping Unit Number |
| Item Qty | Qty Ordered |
| Item Price | Unit Price |

**Content identifier:** Use the `Record Type` column when saving the format to distinguish it from other formats with the same column structure.

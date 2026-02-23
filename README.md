## Supported Vendors

- Scheels
- Brownells
- Academy Sports
- Tractor Supply
- Princess Auto *(see format notes below)*

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

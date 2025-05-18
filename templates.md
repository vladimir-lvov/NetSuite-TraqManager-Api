# ERP ↔ MES JSON **Templates Library**
Common objects  
Code blocks are **JSONC** (JSON + `//` comments).  
Field names are **camelCase**.

---

## Table of Contents
1. [Party](#1-party)  
2. [Contact](#2-contact)  
3. [Product – Reel](#3-product---reel)  
4. [Quantity](#4-quantity)  
5. [Note](#5-note)  

---

## 1 Party

```jsonc
{
  "partyIdentifiers": [                 // ≥1 IDs for this party
    { "partyIdentifierType": "Consignee",   "value": "ABC123" },
    { "partyIdentifierType": "Shipper",     "value": "5412345000018" }
  ],
  "nameAddress": {                      // legal name & postal address
    "name1":      "Company / Site name",
    "address1":   "Street line 1",
    "address2":   null,                 // optional 2nd line
    "city":       "City",
    "region":     "State / Prov",
    "postalCode": "ZIP / Postcode",
    "country":    "ISO Country"
  },
  "contacts": [                         // 0-n contacts
    { /* see Contact template */ }
  ],
  "notes": [                         // 0-n notes
    { /* see Note template */ }
  ]  
}
```

---

## 2 Contact

```jsonc
{
  "contactType": "Purchasing | Dispatch | Delivery | …",
  "contactName": "Jane Smith",          // optional friendly name
  "phone":       "+1 555-123-4567",     // optional
  "email":       "jane.smith@domain.com"
}
```

---

## 3 Product — Reel

```jsonc
{
  "sku":          "NPA59ST-1275-1150-NPLD-AA-RPP1",   // unique SKU
  "grade":        "NPA59ST",                          // mill grade code

  // width & diameter use the standard Quantity template
  "reelWidth":    { "value": 1275, "uom": "mm" },
  "reelDiameter": { "value": 1150, "uom": "mm" },

  "core":         "NPLD",                             // core type
  "wrapType":     "AA",                               // packaging style
  "reelPerPack":  1                                   // rolls per pack
}
```
*(Swap fields or extend for sheet, pallet, or finished-goods SKUs.)*

---

## 4 Quantity

```jsonc
{ "value": 50, "uom": "MetricTon" }   // `uom` must be a papiNet code
```

---

## 5 Note

```jsonc
{ "noteType": "Planner | Carrier | Safety | …", "note": "Free-text instruction." }
```

---

## Usage Guide 🚀

**Mill Order & Load** samples reference these blocks with comments like  
`/* Party – see Templates/Party */`.


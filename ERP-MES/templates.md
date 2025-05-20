# ERP ↔ MES JSON **Templates Library**
Common reusable objects for Mill Order, Shipment, and Load messages.  
Code blocks use **JSONC** (JSON + `//` comments).  
All field names are **camelCase**.

---

## Table of Contents
1. [Party](#1-party)  
2. [Contact](#2-contact)  
3. [Product – Roll](#3-product—roll)  
4. [Quantity](#4-quantity)  
5. [Note](#5-note)  

---

## 1 Party

```jsonc
{
  "partyIdentifiers": [                 // ≥1 IDs for this party
    { "partyIdentifierType": "Internal", "value": "ABC123" },
    { "partyIdentifierType": "GLN",      "value": "5412345000018" }
  ],
  "nameAddress": {                      // legal name & postal address
    "name1":      "Company / Site name",
    "name2":      null,                 // optional nickname
    "address1":   "Street line 1",
    "address2":   null,                 // optional second line
    "city":       "City",
    "region":     "State / Prov",
    "postalCode": "ZIP / Postcode",
    "country":    "ISO Country"
  },
  "contacts": [                         // 0-n contacts
    { /* see Contact template */ }
  ],
  "notes": [                            // 0-n free-form notes
    { /* see Note template */ }
  ]
}
```

---

## 2 Contact

```jsonc
{
  "contactType": "Purchasing | Dispatch | Delivery | …",
  "contactName": "Jane Smith",            // optional friendly name
  "phone":       "+1 555-123-4567",       // optional
  "email":       "jane.smith@domain.com"  // optional but recommended
}
```

---

## 3 Product — Roll

```jsonc
{
  "sku":          "NPA59ST-1275-1150-NPLD-AA-RPP1",   // unique SKU
  "grade":        "NPA59ST",                          // mill grade code

  // width & diameter use the standard Quantity template
  "rollWidth":    { "value": 1275, "uom": "mm" },
  "rollDiameter": { "value": 1150, "uom": "mm" },

  "core":         "NPLD",                             // core type
  "wrapType":     "AA",                               // packaging style
  "rollPerPack":  1                                   // rolls per pack
}
```
*(Swap fields or extend for sheet, pallet, or finished-goods SKUs.)*

---

## 4 Quantity

```jsonc
{ "value": 50, "uom": "MetricTon" }   // uom must be a valid papiNet code
```

---

## 5 Note

```jsonc
{
  // noteType must be one of the controlled codes below
  // SHIPPING | WINDER | PROD_PLANNER | CLAMP_TRUCK |
  // CARRIER | WRAPPER | CONSIGNEE | SHUNTER |
  // SHIPPING_DATE_CHANGE | READY_TIMES
  "noteType": "SHIPPING",
  "note": "Free-text instruction or comment."
}
```

---

## Usage Guide 🚀

**Mill Order & Load** samples reference these blocks with comments like  
`/* Party – see Templates/Party */`.


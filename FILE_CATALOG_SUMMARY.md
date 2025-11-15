# CSV File Catalog Summary
## Savannah Tank & Equipment Corporation - Tank Quotation System

---

## Directory Structure

```
ST-DataBase/
├── xlsx_exports_Expanded_Chris/  (30 files)
│   ├── Design Templates (3)
│   │   ├── TANK_DESIGN,_API.csv
│   │   ├── TANK_DESIGN,_ASME.csv
│   │   └── HORIZONTAL_TANK.csv
│   ├── Add-On Components (6)
│   │   ├── ADD_ON-INTERNAL_COIL.csv
│   │   ├── ADD_ON-_DIMPLE_JACKET.csv
│   │   ├── ADD_ON-_HALF_PIPE_JACKET.csv
│   │   ├── ADD_ON-_LADDER.csv
│   │   ├── ADD_ON-_HANDRAIL.csv
│   │   └── ADD_ON-_PLATFORM.csv
│   ├── Component Specs (2)
│   │   ├── MANWAY,_CS.csv
│   │   └── Cleanout.csv
│   ├── Labor Estimation (17)
│   │   ├── LABOR-_ASME_HEAD_SHELL.csv
│   │   ├── LABOR-_API_TOP_BTM_RIM_ANGLE_.csv
│   │   ├── LABOR-_NOZZLE_.csv
│   │   ├── LABOR-_SHELL_ROLL,_CS.csv
│   │   ├── LABOR-_SHELL_ROLL,_SS.csv
│   │   ├── LABOR-_BAFFLE.csv
│   │   ├── LABOR-_LEGS.csv
│   │   ├── LABOR-_LADDER.csv
│   │   ├── LABOR-_HANDRAIL.csv
│   │   ├── LABOR-_PLATFORM.csv
│   │   ├── LABOR-_RING.csv
│   │   ├── LABOR-_DIMPLE_JACKET.csv
│   │   ├── LABOR-_HALF_PIPE_JACKET.csv
│   │   ├── LABOR-_INTERNAL_COIL.csv
│   │   ├── LABOR-_POLISH.csv
│   │   ├── Labor_-_Saddles.csv
│   │   └── Labor_-_Support_lugs.csv
│   ├── Other (2)
│   │   ├── TOC.csv (Table of Contents)
│   │   └── LABOR-_SKIRT.csv
│
├── xlsx_exports_NewNew/  (11 files)
│   ├── Quote Management (2)
│   │   ├── INFORMATION.csv
│   │   └── RESULT.csv
│   ├── Component Selection (4)
│   │   ├── TOP-BTM-SHELL_DESIGN.csv
│   │   ├── SUPPORTS-RINGS.csv
│   │   ├── CONNECTIONS.csv
│   │   ├── JACKETS.csv
│   │   └── LADDER-HANDRAIL-PLATFORM.csv
│   ├── Reference Data (3)
│   │   ├── PRICE_DATABASE.csv
│   │   ├── HOUR-MATERIAL_DATABASE.csv (LARGEST - 5197 rows)
│   │   └── LISTS.csv
│   └── Other (1)
│       └── BLANK.csv (empty, unused)
```

---

## File Categorization by Tier & Purpose

### TIER 1: TRANSACTION FILES (2 files)
These are the core quote/project files where customer data and final quotes are stored.

| File | Rows | Purpose | Key Fields |
|------|------|---------|-----------|
| INFORMATION.csv | 42 | Quote/project header data | QUOTE #, CUSTOMER NAME, DUE DATE, DIAMETER, MOC |
| RESULT.csv | 343 | Final bill of materials & quote | Line items, QTY, DESCRIPTION, MOC, UNIT_PRICE |

**Relationship:** INFORMATION.quote_number → RESULT.quotation_number

---

### TIER 2: DESIGN TEMPLATES (7 files)
These files define the base Bill of Materials for different tank designs and materials.

| File | Rows | Material Variants | Purpose |
|------|------|------------------|---------|
| TANK_DESIGN,_API.csv | 173 | Carbon, 304SS, 316SS | API-standard tank BOM |
| TANK_DESIGN,_ASME.csv | 205 | Carbon, 304SS, 316SS | ASME-code tank BOM |
| HORIZONTAL_TANK.csv | 164 | Carbon, 304SS, 316SS | Horizontal tank BOM |
| TOP-BTM-SHELL_DESIGN.csv | 48 | N/A | Roof/bottom type specs |
| SUPPORTS-RINGS.csv | 53 | N/A | Support structure specs |
| JACKETS.csv | 50 | N/A | Jacket zone selections |
| LADDER-HANDRAIL-PLATFORM.csv | 22 | N/A | Access equipment config |

**Column Pattern:** ITEM, QTY, DESCRIPTION, MTRL, MOC, LABOR

**Data Quality:** Multiple material variants presented side-by-side in wide format

---

### TIER 3: COMPONENT SPECIFICATIONS (2 files)
Detailed specifications for specific tank connections and accessories.

| File | Rows | Purpose | Input Parameters |
|------|------|---------|-----------------|
| CONNECTIONS.csv | 26 | Nozzle/connection specs | SIZE, QTY, TYPE, RATING, PIPE LENGTH |
| MANWAY,_CS.csv | 69 | Manway configuration | ITEM, QTY, DESCRIPTION, MTRL |
| Cleanout.csv | 45 | Cleanout configuration | ITEM, QTY, DESCRIPTION, MTRL |

---

### TIER 4: ADD-ON COMPONENT FILES (6 files)
Bill of Materials for optional add-on components, with material costs and labor.

| File | Rows | Component | Material Type |
|------|------|-----------|---------------|
| ADD_ON-INTERNAL_COIL.csv | 36 | Internal cooling coil | Stainless pipe (SA312) |
| ADD_ON-_DIMPLE_JACKET.csv | 23 | Dimple jacket | Stainless plate (SA240) |
| ADD_ON-_HALF_PIPE_JACKET.csv | 22 | Half-pipe jacket | Stainless pipe (SA312) |
| ADD_ON-_LADDER.csv | 26 | Ladder assembly | Galvanized steel (GCST) |
| ADD_ON-_HANDRAIL.csv | 30 | Handrail assembly | Stainless angle (SA479) |
| ADD_ON-_PLATFORM.csv | 20 | Platform structure | Galvanized steel (GCST) |

**Column Pattern:** ITEM, QTY, DESCRIPTION, MTRL, MOC, LABOR

---

### TIER 5: LABOR ESTIMATION TABLES (18 files)
Lookup tables for man-hour calculations. Each parameter set has an associated labor value.

#### Structural Components (5 files)
| File | Rows | Lookup Parameters |
|------|------|-------------------|
| LABOR-_SHELL_ROLL,_CS.csv | 591 | Tank DIA, Thickness (CS) |
| LABOR-_SHELL_ROLL,_SS.csv | 590 | Tank DIA, Thickness (SS) |
| LABOR-_ASME_HEAD_SHELL.csv | 530 | Tank size, Thickness, FIT/WELD type |
| LABOR-_API_TOP_BTM_RIM_ANGLE_.csv | 479 | Tank size, Component type (FLAT BOTTOM/SLOPE/RIM ANGLE) |
| LABOR-_SKIRT.csv | 280 | Skirt configuration |

#### Support Components (4 files)
| File | Rows | Lookup Parameters |
|------|------|-------------------|
| LABOR-_LEGS.csv | 125 | Tank DIA, Leg Size, # of Legs, Pad/Brace/Gusset required |
| Labor_-_Saddles.csv | 98 | Tank DIA, # of Saddles |
| Labor_-_Support_lugs.csv | 67 | Tank DIA, # of Lugs |
| LABOR-_RING.csv | 103 | Tank DIA, Ring Type, Ring Thickness |

#### Connections & Accessories (6 files)
| File | Rows | Lookup Parameters |
|------|------|-------------------|
| LABOR-_NOZZLE_.csv | 254 | Size, Qty, Wall Thickness, Repad/Gusset/Tangential/Blind/Davit flags |
| LABOR-_BAFFLE.csv | 124 | Length, # of Baffles, Construction type |
| LABOR-_PLATFORM.csv | 92 | Tank DIA, Platform flag, # Nozzles, # Manways |
| LABOR-_LADDER.csv | 16 | Length, Caged flag |
| LABOR-_HANDRAIL.csv | 14 | Tank DIA, Round/Straight |
| LABOR-_POLISH.csv | 43 | Tank DIA, Shell Length, # Seams, # Nozzles, # Baffles |

#### Optional Features (3 files)
| File | Rows | Lookup Parameters |
|------|------|-------------------|
| LABOR-_INTERNAL_COIL.csv | 120 | Coil DIA, # Turns, Coil Length |
| LABOR-_DIMPLE_JACKET.csv | 51 | # Panels, # Dimples, Area |
| LABOR-_HALF_PIPE_JACKET.csv | 68 | Tank DIA, Linear FT of Pipe, # of Turns |

---

### TIER 6: MASTER REFERENCE DATA (3 files)
Core lookup tables for material specifications, pricing, and valid options.

| File | Rows | Purpose | Key Columns |
|------|------|---------|-------------|
| PRICE_DATABASE.csv | 90 | Plate pricing lookup | Material Type, Thickness, Width, Cost/Unit, Weight/Unit |
| HOUR-MATERIAL_DATABASE.csv | 5197 | Material requirements & hours | Tank Size Index → Material Quantities, Labor Hours |
| LISTS.csv | 136 | Valid dropdown options | Support Types, Material Codes, Yes/No options |

**Purpose:** Validation and calculation data used across all other tables

---

### TIER 7: METADATA FILES (2 files)

| File | Rows | Purpose |
|------|------|---------|
| TOC.csv | 31 | Table of contents - Index of all sheets |
| BLANK.csv | 1 | Empty placeholder (no data) |

---

## Column Headers by File Type

### Standard BOM Columns (Design & Add-On files)
```
ITEM            - Component name
QTY             - Quantity required
DESCRIPTION     - Detailed specification
MTRL            - Material standard code (SA36, SA240, etc.)
MOC             - Material type (Carbon, 304SS, 316SS) or unit price
LABOR           - Man-hours or labor cost
```

### Quote Columns (INFORMATION.csv)
```
QUOTE #         - Quote number (unique identifier)
DUE DATE        - Quote due date
CUSTOMER NAME   - Customer name
CONTACT NAME    - Contact person
CONTACT NUMBER  - Phone number
DESCRIPTION     - Project description
TAG #           - Inventory/asset tag
PROJECT NAME    - Project name
MOC             - Material of Construction
DESIGN TEMP     - Design temperature
DESIGN PRESSURE - Design pressure
DIAMETER        - Tank diameter
SHELL HEIGHT    - Tank height
```

### Result Columns (RESULT.csv)
```
item #          - Line item number
ITEM            - Component name
QTY             - Quantity
DESCRIPTION     - Component specification
MOC             - Material of construction
UNIT_PRICE      - Price per unit
EXTENDED_PRICE  - Quantity * Unit Price
TOTAL           - Running total
```

### Connection Columns (CONNECTIONS.csv)
```
SIZE            - Nozzle size
QTY             - Number of nozzles
TYPE            - Connection type
RATING          - Pressure rating
PIPE LENGTH     - Length required
SCH THICKNESS   - Schedule (wall thickness)
REPAD           - Reinforcement pad required
REPAD SIZE      - Repad dimensions
REPAD THICKNESS - Repad thickness
BLIND           - Blind flange
OTHER           - Additional options
MOC             - Material of construction
```

---

## Data Flow & Dependencies

```
┌─────────────────────────────────────────────────────────────────┐
│                    QUOTE CREATION PROCESS                        │
└─────────────────────────────────────────────────────────────────┘

1. INFORMATION.csv (User inputs)
   ├─ QUOTE # (key)
   ├─ CUSTOMER NAME
   ├─ DIAMETER (dimension key for lookups)
   ├─ DESIGN TYPE (API/ASME/HORIZONTAL)
   ├─ MOC (Carbon/304SS/316SS)
   └─ Other specs

         ↓ References ↓

2. Design Selection
   ├─ TANK_DESIGN,_API.csv OR
   ├─ TANK_DESIGN,_ASME.csv OR
   └─ HORIZONTAL_TANK.csv
      │
      ├─ BASE BOM items
      └─ Each item has LABOR field

         ↓ Lookup ↓

3. Labor Calculation
   ├─ LABOR-_SHELL_ROLL,_*.csv (Tank diameter → Hours)
   ├─ LABOR-_ASME_HEAD_SHELL.csv (Dimensions → Hours)
   ├─ LABOR-_API_TOP_BTM_RIM_ANGLE_.csv (Type → Hours)
   ├─ LABOR-_NOZZLE_.csv (Size, Qty, Options → Hours)
   ├─ LABOR-_LEGS.csv (Dia, Size, Qty, Pads → Hours)
   └─ Other component labor tables

         ↓ Lookup ↓

4. Costing
   ├─ PRICE_DATABASE.csv
   │  (Material, Thickness, Width → Cost)
   │
   └─ HOUR-MATERIAL_DATABASE.csv
      (Tank Size → Material Quantities)

         ↓ Select ↓

5. Optional Components
   ├─ TOP-BTM-SHELL_DESIGN.csv (Roof/bottom type)
   ├─ SUPPORTS-RINGS.csv (Support type)
   ├─ CONNECTIONS.csv (Nozzle specs)
   ├─ JACKETS.csv (Cooling jacket)
   ├─ LADDER-HANDRAIL-PLATFORM.csv (Access)
   ├─ ADD_ON-INTERNAL_COIL.csv (Coil)
   ├─ ADD_ON-_DIMPLE_JACKET.csv (Dimple jacket)
   ├─ ADD_ON-_HALF_PIPE_JACKET.csv (Half-pipe)
   ├─ ADD_ON-_LADDER.csv (Ladder)
   ├─ ADD_ON-_HANDRAIL.csv (Handrail)
   └─ ADD_ON-_PLATFORM.csv (Platform)

         ↓ Generate ↓

6. RESULT.csv (Final Quote)
   ├─ QUOTATION NO (from INFORMATION)
   ├─ DATE (from INFORMATION)
   ├─ Line items with:
   │  ├─ ITEM, QTY
   │  ├─ DESCRIPTION (from design file)
   │  ├─ MOC (from component spec)
   │  ├─ UNIT_PRICE (from pricing lookup)
   │  └─ EXTENDED_PRICE (Qty × Unit Price)
   └─ TOTAL

```

---

## Material Code Reference

| Code | Material | Standard | Uses |
|------|----------|----------|------|
| SA36 | Carbon Steel Plate | ASTM A36 | Manway, basic components |
| SA240 | Stainless Steel Plate | ASTM A240 (300 series) | Tank shell, dimple jacket |
| SA312 | Stainless Steel Pipe | ASTM A312 | Internal coil, half-pipe |
| SA479 | Stainless Steel Bar/Wire | ASTM A479 | Handrail, clips |
| GCST | Galvanized Carbon Steel Tubing | ASTM A500 | Ladder, platform |

---

## Data Statistics

| Metric | Value |
|--------|-------|
| **Total Files** | 41 |
| **Total Rows** | 10,497 |
| **Largest File** | HOUR-MATERIAL_DATABASE.csv (5,197 rows) |
| **Smallest File** | BLANK.csv (0 rows) |
| **Design Templates** | 3 |
| **Material Variants** | 3 (Carbon, 304SS, 316SS) |
| **Labor Lookup Tables** | 18 |
| **Add-On Components** | 6 |
| **Unique Material Codes** | 5+ |
| **Unique Component Types** | 50+ |

---

## Key Relationships & Foreign Keys

```
QUOTES (INFORMATION.csv)
│
├─ PK: quote_number
├─ FK: design_type → (API, ASME, HORIZONTAL)
├─ FK: material_type → (Carbon, 304SS, 316SS)
└─ One-to-Many: QUOTE_LINE_ITEMS

QUOTE_LINE_ITEMS (RESULT.csv)
│
├─ FK: quote_number → QUOTES
├─ FK: component_id → TANK_COMPONENTS
├─ FK: material_spec → MATERIAL_SPECIFICATIONS
└─ FK: support_type → SUPPORT_TYPES

TANK_COMPONENTS
│
├─ FK: design_type
├─ FK: component_type
└─ FK: material_spec → MATERIAL_SPECIFICATIONS

LABOR_ESTIMATES (LABOR-_*.csv)
│
├─ FK: component_type
├─ Lookup: tank_diameter → hours
└─ Lookup: various parameters → hours

PRICE_DATA (PRICE_DATABASE.csv)
│
├─ FK: material_type
├─ Lookup: thickness, width → price, weight
└─ Effective_date (for historical pricing)

MATERIAL_SPECIFICATIONS
│
├─ PK: spec_code (SA36, SA240, etc)
├─ FK: material_type
└─ standard_reference
```

---

## File Format Notes

**Important:** All files are exported from Excel in a non-standard CSV format:

```
Headers: sheet, row, col, address, value, formula

Example:
sheet,"TANK DESIGN, API",1,1,A1,"API TANK, CARBON",
sheet,"TANK DESIGN, API",2,1,A2,ITEM,
sheet,"TANK DESIGN, API",2,2,B2,QTY,
```

**Real data is in the "value" column.** Requires parsing to extract actual tabular data.

---

## Import Recommendations

1. **Remove metadata columns** (sheet, row, col, address, formula)
2. **Extract actual data** from value column
3. **Normalize wide spreadsheets** (separate material variants into rows)
4. **Standardize headers** (use consistent row numbers)
5. **Validate material codes** against master list
6. **Convert units** (standardize FT vs inches)
7. **Document calculation rules** for labor hour lookups
8. **Establish update process** for pricing and labor tables


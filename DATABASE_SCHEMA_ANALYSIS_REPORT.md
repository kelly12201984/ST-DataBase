# Database Schema Analysis Report
## CSV Files from Savannah Tank & Equipment Corporation

**Repository:** ST-DataBase (Tank Quotation & Manufacturing System)
**Analysis Date:** 2025-11-15
**Total Files Analyzed:** 41 CSV files
**Source Directories:**
- /home/user/ST-DataBase/xlsx_exports_Expanded_Chris (30 files)
- /home/user/ST-DataBase/xlsx_exports_NewNew (11 files)

---

## EXECUTIVE SUMMARY

This analysis reveals a comprehensive tank manufacturing quotation system with the following key components:

1. **Quote/Project Management:** Customer information, project specs, quote generation
2. **Tank Design Specifications:** API, ASME, and Horizontal tank designs
3. **Materials & Pricing:** Component materials, plate pricing, material weights
4. **Labor Estimation:** Detailed labor hours for various manufacturing processes
5. **Component Add-ons:** Jackets, ladders, platforms, internal coils, manways
6. **Manufacturing Specifications:** Connections, supports, finishes

---

## DETAILED FILE CATALOG

### A. QUOTE & PROJECT INFORMATION FILES

#### 1. INFORMATION.csv
- **Location:** /home/user/ST-DataBase/xlsx_exports_NewNew/
- **Columns (Row 7-12 headers):**
  - QUOTE #
  - DUE DATE
  - CUSTOMER NAME
  - CONTACT NAME
  - DESCRIPTION
  - CONTACT NUMBER
  - TAG #
  - PROJECT NAME
  - MOC (Material of Construction)
  - DESIGN TEMP
  - DIAMETER
  - DESIGN PRESSURE
  - SHELL HEIGHT
- **Purpose:** Stores basic project/quote metadata
- **Data Quality:** Clean header structure with paired columns

#### 2. RESULT.csv
- **Location:** /home/user/ST-DataBase/xlsx_exports_NewNew/
- **Columns (Row 4 headers):**
  - item # (sequential ID)
  - ITEM (component name)
  - QTY (quantity)
  - DESCRIPTION (detailed spec)
  - MOC (material of construction)
  - UNIT_PRICE (inferred)
  - EXTENDED_PRICE (inferred)
- **Purpose:** Final quotation/bill of materials output
- **Data Quality:** Contains formula references (=INFORMATION!B7)
- **Row Count:** 343 rows
- **Note:** Links to INFORMATION sheet for quote number and date

---

### B. TANK DESIGN FILES (PRIMARY PRODUCTS)

#### 3. TANK_DESIGN,_API.csv
- **Location:** /home/user/ST-DataBase/xlsx_exports_Expanded_Chris/
- **Sheet Variants:** 3 material variants per design
  - Carbon Steel (Col A-G)
  - 304 Stainless Steel (Col H-N)
  - 316 Stainless Steel (Col O-U)
- **Column Headers (Row 2):**
  - ITEM
  - QTY
  - DESCRIPTION
  - MTRL (Material specification like SA36)
  - MOC (Material type: Carbon, SS304, SS316)
  - LABOR (hours required)
- **Sample Items:** Various tank components with material specs
- **Data Quality Issues:**
  - Wide spreadsheet (multiple variants side-by-side increases columns)
  - Material abbreviations (SA36, SA240-304/304L, SA479-304/304L)

#### 4. TANK_DESIGN,_ASME.csv
- **Location:** /home/user/ST-DataBase/xlsx_exports_Expanded_Chris/
- **Structure:** Identical to API design file
- **Column Headers:** ITEM, QTY, DESCRIPTION, MTRL, MOC, LABOR
- **Purpose:** ASME code-compliant tank design alternative
- **Key Difference:** ASME vs API standards affect component specs

#### 5. HORIZONTAL_TANK.csv
- **Location:** /home/user/ST-DataBase/xlsx_exports_Expanded_Chris/
- **Row Count:** 164 rows
- **Column Headers:** Same as API/ASME (ITEM, QTY, DESCRIPTION, MTRL, MOC, LABOR)
- **Purpose:** Horizontal tank orientation specifications
- **Data Organization:** 3 material variants (Carbon, SS304, SS316)

---

### C. TANK COMPONENT FILES (DESIGN SPECS)

#### 6. TOP-BTM-SHELL_DESIGN.csv
- **Location:** /home/user/ST-DataBase/xlsx_exports_NewNew/
- **Columns (Row 7-8 headers):**
  - TYPE (Flat, Cone, Dished bottom/top)
  - RIM ANGLE (angle specification)
  - THICKNESS (plate thickness)
  - RIM ANGLE SIZE
  - STIFFENERS (yes/no)
  - # OF STIFFENERS
  - HEAD PRICE
  - MIN THICKNESS
  - GUSSET HEIGHT
- **Purpose:** Specifications for tank roof and bottom designs

#### 7. SUPPORTS-RINGS.csv
- **Location:** /home/user/ST-DataBase/xlsx_exports_NewNew/
- **Columns (Row 7-9 headers):**
  - TYPE (Saddles, Angle Legs, Pipe Legs, Beam Legs, Support Lugs, Skirt)
  - NUMBER OF SUPPORTS
  - SUPPORT MOC
  - TOP PLATE WIDTH
  - TOP PLATE LENGTH
  - TOP PLATE THICKNESS
  - REPAD REQUIRED
  - GUSSET HEIGHT
- **Purpose:** Support structure specifications

#### 8. CONNECTIONS.csv
- **Location:** /home/user/ST-DataBase/xlsx_exports_NewNew/
- **Columns (Row 7 headers):**
  - SIZE
  - QTY
  - TYPE
  - RATING
  - PIPE LENGTH
  - SCH THICKNESS (Schedule)
  - REPAD
  - REPAD SIZE
  - REPAD THICKNESS
  - BLIND
  - OTHER
  - MOC
- **Purpose:** Nozzle connection specifications
- **Data Quality:** Comprehensive attribute tracking

---

### D. ADD-ON COMPONENT FILES (MATERIAL + LABOR ESTIMATES)

All ADD-ON files follow similar structure with headers at Row 4:
- ITEM
- QTY
- DESCRIPTION
- MTRL (Material standard like SA312, SA240)
- MOC (Material type, often quoted price)
- LABOR (man-hours)

#### 9. ADD_ON-INTERNAL_COIL.csv
- **Row Count:** 36 rows
- **Sample Items:** Internal coil piping with elbows, specifications (3" SCH 40)
- **Material:** Stainless steel (SA312-316/316L WLD)

#### 10. ADD_ON-_DIMPLE_JACKET.csv
- **Row Count:** 23 rows
- **Component:** Dimple jacket shell and bottom cone
- **Specs:** 14 GA, 3" space, 0.5" hole spacing
- **Material:** SA240-304/304L (stainless plates)

#### 11. ADD_ON-_HALF_PIPE_JACKET.csv
- **Row Count:** 22 rows
- **Components:** Shell and head coils with specified pitch
- **Material:** SCH10 piping specifications

#### 12. ADD_ON-_LADDER.csv
- **Row Count:** 26 rows
- **Items:** Ladder, fall protection cable lifeline
- **Materials:** GCST (assumed: galvanized carbon steel tubing)

#### 13. ADD_ON-_HANDRAIL.csv
- **Row Count:** 30 rows
- **Items:** Tank clips (angle iron), handrails
- **Materials:** SA479-304/304L (stainless angle)

#### 14. ADD_ON-_PLATFORM.csv
- **Row Count:** 20 rows
- **Items:** Structural shapes (C6 X 8.2#), hot rolled bar
- **Materials:** GCST (galvanized carbon steel)

#### 15. MANWAY,_CS.csv
- **Location:** /home/user/ST-DataBase/xlsx_exports_Expanded_Chris/
- **Row Count:** 69 rows
- **Columns:** ITEM, QTY, DESCRIPTION, MTRL, MOC, LABOR
- **Components:** Manway neck, flange, cover (20" size)
- **Material:** SA36 (carbon steel)

#### 16. Cleanout.csv
- **Location:** /home/user/ST-DataBase/xlsx_exports_Expanded_Chris/
- **Row Count:** 45 rows
- **Components:** Cleanout bottom, top, flange
- **Columns:** ITEM, QTY, DESCRIPTION, MTRL, MOC, LABOR
- **Material:** SA240-304/304L (stainless plate)

---

### E. LABOR ESTIMATION FILES (MANUFACTURING HOURS)

All labor files contain detailed man-hour (M/H) calculations based on tank dimensions, component specs, and manufacturing processes.

#### 17. LABOR-_ASME_HEAD_SHELL.csv
- **Row Count:** 530 rows
- **Structure:** Hours by shell thickness (3/16" to 3/4"+)
- **Categories:** FIT + WELD hours by thickness
- **Columns:** Tank dimensions, labor breakdown by operation

#### 18. LABOR-_API_TOP_BTM_RIM_ANGLE_.csv
- **Row Count:** 479 rows
- **Categories:**
  - FLAT BOTTOM (CUT, MAKE, FIT, WELD)
  - SLOPED BOTTOM (similar breakdown)
  - RIM ANGLE (ROLL, FIT, WELD)
  - TOP (CUT, FLAT variants)
- **Basis:** Labor hours lookup tables

#### 19. LABOR-_NOZZLE_.csv
- **Row Count:** 254 rows
- **Input Parameters:**
  - Nozzle Size (variable by size)
  - # of Nozzles
  - Tank Wall Thickness
  - Repad? (yes/no)
  - Gussets? (yes/no)
  - Tangential? (yes/no)
  - Blind? (yes/no)
  - Davit/Hinge? (yes/no)
- **Output:** Total M/H for nozzles

#### 20. LABOR-_SHELL_ROLL,_CS.csv & LABOR-_SHELL_ROLL,_SS.csv
- **Row Count:** ~590 rows each
- **Columns:**
  - TANK DIA ID/OD IN FT
  - TANK ID/OD IN INCH
  - PLATES per SHELL COURSE
  - LENGTH of EACH PLATE
  - Material/weld/roll hours by thickness (3/16" to 3/4")
- **Purpose:** Shell fabrication labor estimation
- **Note:** Separate files for Carbon Steel vs Stainless Steel

#### 21. LABOR-_BAFFLE.csv
- **Row Count:** 124 rows
- **Input Parameters:**
  - Baffle Length (Up to 5', 5'-10', etc.)
  - # of Baffles
  - Baffle Construction, Supports, Installation specs
- **Output:** Total M/H, M/H per Baffle

#### 22. LABOR-_LEGS.csv
- **Row Count:** 125 rows
- **Input Parameters:**
  - Tank Diameter
  - Leg Size (2"x2", 3"x3", etc.)
  - # of Legs
  - Poison Pad Req'd?
  - Bracing Req'd?
  - Gusseting Req'd?
- **Output:** Total M/H per leg configuration

#### 23. LABOR-_LADDER.csv
- **Row Count:** 16 rows
- **Input Parameters:**
  - Length of Ladder (ft)
  - Caged? (yes/no)
  - M/H per 10 FT
- **Output:** Total M/H for Ladder

#### 24. LABOR-_HANDRAIL.csv
- **Row Count:** 14 rows
- **Input Parameters:**
  - Diameter of Tank (FT)
  - Round or Straight
- **Output:** Total M/H for Handrails

#### 25. LABOR-_PLATFORM.csv
- **Row Count:** 92 rows
- **Input Parameters:**
  - Tank Diameter
  - Platform? (yes/no)
  - # of Nozzles
  - # of Manways
- **Output:** SQ FT of Platform, M/H per Sq Ft, M/H Nozzle Banding, etc.

#### 26. LABOR-_RING.csv
- **Row Count:** 103 rows
- **Categories:**
  - INSULATION RINGS (Tank diameter-based)
  - INTERNAL SUPPORT / TRAY RINGS (includes ring thickness)
- **Output:** M/H per ring configuration

#### 27. LABOR-_DIMPLE_JACKET.csv
- **Row Count:** 51 rows
- **Categories:** Shell and Head dimple jackets
- **Parameters:**
  - # of Panels
  - # of Dimples
  - M/H breakdown: Fit & Tack, Dimples, Seams, Repair

#### 28. LABOR-_HALF_PIPE_JACKET.csv
- **Row Count:** 68 rows
- **Categories:** Shell and head jacket sections
- **Parameters:**
  - Tank Diameter (ft)
  - Linear FT of Pipe
  - # of Turns
  - M/H breakdown: Fit & Tack, Weld, Repair

#### 29. LABOR-_INTERNAL_COIL.csv
- **Row Count:** 120 rows
- **Parameters:**
  - Coil Diameter (Up to 2', 2'-4', etc.)
  - # of Turns
  - Length of Coil (FT)
  - # of Joints / # of Elbows
- **Output:** Circ of Coil, M/H Turns, M/H Welded Joints

#### 30. LABOR-_POLISH.csv
- **Row Count:** 43 rows
- **Parameters:**
  - Diameter of Tank (FT)
  - Shell Length (FT)
  - # of Girth Seams
  - # of Long Seams
  - # of <14" Nozzles
  - # of 14"+ Nozzles
  - # of Baffles
- **Output:** M/H breakdown by seam type

#### 31. LABOR-_SKIRT.csv
- **Row Count:** 280 rows
- **Categories:**
  - SKIRT SHELL ROLLING
  - BASE RING
  - ASSEMBLY & SEAM WELD
- **Output:** Labor estimates with instructions for calculation

#### 32. Labor_-_Saddles.csv
- **Row Count:** 98 rows
- **Parameters:**
  - Tank Diameter
  - # of Saddles
  - M/H breakdown: Belly Band, Saddle Construction, Installation

#### 33. Labor_-_Support_lugs.csv
- **Row Count:** 67 rows
- **Parameters:**
  - Tank Diameter
  - # of Rings Required
  - # of Lugs
  - M/H breakdown: Rings, Hold Down Lugs

---

### F. REFERENCE/LOOKUP DATABASE FILES

#### 34. HOUR-MATERIAL_DATABASE.csv
- **Row Count:** 5197 rows (LARGEST FILE)
- **Purpose:** Master lookup table for material requirements and labor hours
- **Primary Sections (Row 1-3 headers):**
  - **FLAT & CONE TOP AND BOTTOM MATERIAL & HOURS** (Cols A-V)
    - Row 2: Column numbers (1-20)
    - Row 3: Categories:
      - SS Plate #1, SS Plate #2
      - CST Plate #1, CST Plate #2
      - Flat top hrs, Cone top hrs, Bottom hours, Rim angle hr, Sloped btm hrs
      - Plate dimensions (width, length) for SS and CST
  - **WELD SEAMS & HEAD HOURS** (Cols W+)
    - Plate thicknesses: 0.1875", 0.25", 0.3125", 0.375", 0.5", 0.625", 0.75", 0.875"
- **Data Organization:**
  - Row 4 onwards: Actual data for different tank sizes
  - Tank size indexed by row number (1-~100+)
  - Material quantities and labor hours for each tank configuration

#### 35. PRICE_DATABASE.csv
- **Row Count:** 90 rows
- **Purpose:** Plate pricing lookup
- **Column Headers (Row 2-3):**
  - Plate Width Categories: 48 OR 60 WIDE, 72 WIDE, 96 WIDE, 120 WIDE
  - Stainless Variants: 304, 316
  - Carbon Variant: 36
  - Pricing by thickness and width
  - Plate Weight section (Cols L+)
    - SS (304, 316) and CARBON weight pricing
- **Thickness Rows (Col A):**
  - 0.1875", 0.25", 0.3125", 0.375", 0.5", 0.625", 0.75", 0.875", etc.
- **Data Quality:** Structured pricing matrix
- **Sample Values:** 
  - 0.1875" thick, 304 SS, 48-60" wide: $1.49/lb
  - Prices appear to be per pound or per unit area

---

### G. REFERENCE/LOOKUP & CONFIGURATION FILES

#### 36. LISTS.csv
- **Location:** /home/user/ST-DataBase/xlsx_exports_NewNew/
- **Row Count:** 136 rows
- **Purpose:** Lookup lists and dropdown options
- **Content (Row 2-4, 6+):**
  - Support types: ANCHOR CHAIRS, ANGLE LEGS, PIPE LEGS, BEAM LEGS, SUPPORT LUGS, SKIRT, SADDLES, NO SUPPORTS
  - Yes/No options
  - Material codes: SA36, SA240-304/304L, SA240-316/316L, SA312-304, SA312-316, SA479-304
  - Other standard selections (appears to be form options)

#### 37. JACKETS.csv
- **Location:** /home/user/ST-DataBase/xlsx_exports_NewNew/
- **Columns (Row 7-9 headers):**
  - TOP HEAD JACKET
  - BTM HEAD JACKET
  - JACKET MOC
  - SHELL #1 JACKET
  - SHELL #2 JACKET
  - SHELL #3 JACKET
- **Purpose:** Jacket configuration for different tank areas

#### 38. LADDER-HANDRAIL-PLATFORM.csv
- **Location:** /home/user/ST-DataBase/xlsx_exports_NewNew/
- **Columns (Row 7-10 headers):**
  - **LADDERS Section:**
    - LADDER 1 CAGED
    - LADDER 1 LENGTH
    - LADDER 1 COATING
    - LADDER 2 CAGED, etc.
  - **PLATFORM Section:**
    - TOP PLATFORM
    - SHAPE
    - CUTOUTS
    - REST PLATFORM
- **Purpose:** Configuration selections for access equipment

---

### H. METADATA/HOUSEKEEPING FILES

#### 39. TOC.csv
- **Location:** /home/user/ST-DataBase/xlsx_exports_Expanded_Chris/
- **Row Count:** 31 rows
- **Content:** Table of contents listing all sheets
- **Purpose:** Index/navigation for Excel workbook

#### 40. BLANK.csv
- **Location:** /home/user/ST-DataBase/xlsx_exports_NewNew/
- **Row Count:** 1 row (empty)
- **Purpose:** Placeholder or unused sheet

---

## COMMON FIELDS & RELATIONSHIPS

### Field Analysis Across Files

#### 1. Tank Dimension Fields (Foreign Key Candidates)
- **Tank Diameter** (appears in: LABOR-_LEGS, LABOR-_RING, LABOR-_PLATFORM, LABOR-_HANDRAIL, Labor_-_Saddles, Labor_-_Support_lugs, LABOR-_POLISH, TOP-BTM-SHELL_DESIGN)
- **Tank Height/Shell Height** (INFORMATION, LABOR-_POLISH, various labor files)
- **Tank ID/OD** (LABOR-_SHELL_ROLL files)
- **Relationship:** All specs keyed to tank dimensions -> Central TANK_DIMENSIONS table

#### 2. Material Codes (Foreign Key Candidates)
- **Material Standards:** SA36, SA240, SA312, SA479 (appear consistently)
  - SA36 = Carbon steel plate
  - SA240 = Stainless steel (300 series) plate
  - SA312 = Stainless steel pipe
  - SA479 = Stainless steel wire/shape
- **Material Type (MOC):** Carbon, 304 Stainless, 316 Stainless
- **Relationship:** Link to MATERIALS/SPECIFICATIONS table

#### 3. Labor/Hours (Calculation Keys)
- **LABOR column** in design files = lookup from labor tables
- **M/H** (Man-Hours) = calculated from labor tables based on parameters
- **Relationship:** Dependent on multiple parameters (diameter, thickness, count, type)

#### 4. Quote Linking
- **QUOTE #** (INFORMATION -> RESULT)
- **DUE DATE** (INFORMATION -> RESULT)
- **Customer info** (INFORMATION.csv)
- **Relationship:** One quote has multiple items/components

#### 5. Component Type/Category
- **Design Type:** API, ASME, HORIZONTAL
- **Add-on Type:** INTERNAL_COIL, DIMPLE_JACKET, HALF_PIPE_JACKET, LADDER, HANDRAIL, PLATFORM
- **Support Type:** SADDLES, ANGLE LEGS, PIPE LEGS, etc.
- **Relationship:** Hierarchical component categorization

---

## DATA QUALITY ISSUES & OBSERVATIONS

### 1. Format Issues
- **Excel Export Format:** All files use non-standard CSV (sheet, row, col, address, value, formula columns)
  - Requires parsing to extract actual data
  - Makes direct database import challenging
  - **Recommendation:** Convert to standard row-column format

- **Wide Spreadsheets:** Design files (TANK_DESIGN,_API.csv) have 3 material variants side-by-side
  - Creates 18+ columns instead of normalized structure
  - **Recommendation:** Normalize into material variants

### 2. Data Consistency Issues
- **Material Code Variations:**
  - SA240-304/304L, SA240-304, SA240-304L (inconsistent separators/variants)
  - SA312-316/316L vs SA312-316
  - **Recommendation:** Standardize to single format with version field

- **Unit Inconsistencies:**
  - Tank diameter in FT, inches vary by file
  - Plate dimensions: some in inches, some in feet
  - **Recommendation:** Normalize units across system

- **Missing Values:**
  - LABOR field often empty or "-"
  - MOC field sometimes contains prices instead of material type
  - **Recommendation:** Define NOT NULL constraints, separate concerns

### 3. Structure Issues
- **Row Number Variations:**
  - Headers at different row numbers across files (Row 2, Row 4, Row 6-7)
  - Makes automated parsing difficult
  - **Recommendation:** Standardize header row numbers

- **Sparse Data:**
  - Labor files have many 0 values
  - Lookup tables contain gaps
  - **Recommendation:** Clarify whether 0 means "not applicable" or "no effort"

- **Mixed Purposes:**
  - LABOR-_POLISH.csv contains narrative instructions in data rows
  - Makes data/metadata separation unclear
  - **Recommendation:** Separate configuration from lookup data

### 4. Content Issues
- **Incomplete Descriptions:**
  - Many truncated specifications
  - Manufacturing notes embedded in descriptions
  - **Example:** "DIMPLE JACKET SHELL - 96" ID X 1/4" THICK" should be normalized fields

- **Calculation Dependencies:**
  - Labor hours depend on multiple parameters (size, type, options)
  - No clear lookup logic documented
  - **Recommendation:** Document calculation rules/formulas

- **Blank File:**
  - BLANK.csv in NewNew directory serves no purpose
  - **Recommendation:** Remove or archive

---

## PROPOSED DATABASE SCHEMA STRUCTURE

### Core Tables (from analysis)

#### 1. QUOTES (from INFORMATION.csv)
```
quote_id (PK)
quote_number (UNIQUE)
customer_id (FK)
due_date
description
tag_number
project_name
created_date
```

#### 2. QUOTE_SPECIFICATION (from INFORMATION.csv design params)
```
spec_id (PK)
quote_id (FK)
material_of_construction (MOC)
design_temperature
design_pressure
diameter_inches
shell_height_inches
```

#### 3. TANK_DESIGNS (from TANK_DESIGN files)
```
design_id (PK)
design_type (API/ASME/HORIZONTAL) (FK)
material_type (Carbon/304SS/316SS) (FK)
item_name
quantity
description
material_spec_code (FK)
labor_hours
unit_price
```

#### 4. TANK_COMPONENTS (from ADD_ON files)
```
component_id (PK)
component_type (LADDER/HANDRAIL/JACKET/etc) (FK)
item_name
quantity
description
material_spec_code (FK)
material_of_construction
unit_price
labor_hours
```

#### 5. MATERIAL_SPECIFICATIONS
```
spec_code (PK)
spec_name (SA36, SA240-304/304L, etc)
material_type (FK)
applicable_uses
standard_reference
```

#### 6. LABOR_ESTIMATES (from all LABOR files)
```
estimate_id (PK)
component_type (FK)
tank_diameter_ft
tank_height_ft
shell_thickness
wall_thickness
parameter_1 (varies by component)
parameter_2
...
total_hours
hours_breakdown (JSON or multiple cols)
effective_date
```

#### 7. PRICE_DATA (from PRICE_DATABASE.csv)
```
price_id (PK)
material_type (FK)
plate_width
plate_thickness
cost_per_unit
weight_per_unit
effective_date
```

#### 8. QUOTE_ITEMS (from RESULT.csv)
```
item_id (PK)
quote_id (FK)
line_item_number
component_id (FK)
quantity
unit_price
extended_price
material_of_construction (FK)
```

#### 9. SUPPORT_TYPES (from SUPPORTS-RINGS.csv, LISTS.csv)
```
support_id (PK)
support_type_name
top_plate_width
top_plate_length
top_plate_thickness
requires_repad
requires_gusset
```

#### 10. NOZZLE_SPECIFICATIONS (from CONNECTIONS.csv)
```
nozzle_id (PK)
nozzle_size
quantity
nozzle_type
rating
pipe_length
sch_thickness
requires_repad
repad_size
repad_thickness
is_blind
material_of_construction (FK)
```

---

## FILE CATEGORIZATION BY PURPOSE

### Tier 1: Master Data Files (Reference)
- LISTS.csv - Configuration options
- PRICE_DATABASE.csv - Pricing lookup
- HOUR-MATERIAL_DATABASE.csv - Material & labor lookup

### Tier 2: Design Files (Template/Configuration)
- TANK_DESIGN,_API.csv
- TANK_DESIGN,_ASME.csv
- HORIZONTAL_TANK.csv
- TOP-BTM-SHELL_DESIGN.csv
- SUPPORTS-RINGS.csv
- JACKETS.csv
- LADDER-HANDRAIL-PLATFORM.csv

### Tier 3: Lookup/Calculation Files (Labor)
- LABOR-_ASME_HEAD_SHELL.csv
- LABOR-_API_TOP_BTM_RIM_ANGLE_.csv
- LABOR-_NOZZLE_.csv
- LABOR-_SHELL_ROLL,_CS.csv
- LABOR-_SHELL_ROLL,_SS.csv
- LABOR-_BAFFLE.csv
- LABOR-_LEGS.csv
- LABOR-_LADDER.csv
- LABOR-_HANDRAIL.csv
- LABOR-_PLATFORM.csv
- LABOR-_RING.csv
- LABOR-_DIMPLE_JACKET.csv
- LABOR-_HALF_PIPE_JACKET.csv
- LABOR-_INTERNAL_COIL.csv
- LABOR-_POLISH.csv
- LABOR-_SKIRT.csv
- Labor_-_Saddles.csv
- Labor_-_Support_lugs.csv

### Tier 4: Component BOM Files
- ADD_ON-INTERNAL_COIL.csv
- ADD_ON-_DIMPLE_JACKET.csv
- ADD_ON-_HALF_PIPE_JACKET.csv
- ADD_ON-_LADDER.csv
- ADD_ON-_HANDRAIL.csv
- ADD_ON-_PLATFORM.csv
- MANWAY,_CS.csv
- Cleanout.csv
- CONNECTIONS.csv

### Tier 5: Transaction Files (Quote/Result)
- INFORMATION.csv - Project/quote header
- RESULT.csv - Quote output/BOM
- TOC.csv - Metadata

---

## FOREIGN KEY RELATIONSHIPS IDENTIFIED

1. **Quote Header → Items:**
   - INFORMATION.quote_number → RESULT.quotation_no
   - INFORMATION.due_date → RESULT.date

2. **Design Selection → Labor:**
   - Tank diameter (from INFORMATION) → matches all LABOR-_*.csv files
   - Material type → differentiates labor tables (CS vs SS)
   - Design type → determines which design file (API, ASME, HORIZONTAL)

3. **Materials → Specifications:**
   - MOC field → MATERIAL_SPECIFICATIONS.spec_code
   - Material type → pricing tables

4. **Components → Labor:**
   - Component type → relevant LABOR file
   - Component parameters → lookup in labor tables

---

## RECOMMENDATIONS FOR DATABASE DESIGN

### 1. Normalization
- Separate material type from MOC
- Normalize labor hour calculations into functions/procedures
- Create bridge tables for multi-to-many relationships (Components to Quotes)

### 2. Data Import Strategy
- Convert Excel export format to standard CSV (remove metadata columns)
- Parse wide design files into normalized form
- Establish data validation rules

### 3. Key Identifiers
- Use quote_number as primary business key
- Create surrogate keys (ID fields) for all tables
- Establish unique constraints on business keys

### 4. Calculated Fields
- Derive labor hours from parameters + labor lookup
- Calculate extended prices from unit price × quantity
- Compute material weights from PRICE_DATABASE

### 5. Audit Fields
- Add created_date, modified_date to transactional tables
- Track quote version/revision number
- Maintain effective_date ranges for lookup tables

---

## FIELD GLOSSARY

| Field | Meaning | Source Files |
|-------|---------|--------------|
| MOC | Material of Construction (304 SS, 316 SS, Carbon) | Most design & component files |
| MTRL | Material Standard (SA36, SA240, SA312) | Design & component files |
| M/H | Man-Hours (labor estimate) | All LABOR-_*.csv |
| QTY | Quantity | Design & component files |
| SA36 | ASTM carbon steel plate | Materials files |
| SA240 | ASTM stainless steel plate | Materials files |
| SA312 | ASTM stainless steel tube/pipe | Materials files |
| SA479 | ASTM stainless steel wire/bar | Materials files |
| SCH | Schedule (pipe wall thickness) | Piping specifications |
| BWG | Birmingham Wire Gauge | (if used) |
| ID | Inside Diameter | Labor files |
| OD | Outside Diameter | Labor files |
| FT | Feet | Dimensions |
| M & C | Material and Cut | LABOR-_SHELL_ROLL files |
| WLD | Weld | Labor files |
| Repad | Reinforcement pad | Nozzle files |
| Gusset | Reinforcement bracket | Multiple files |

---

## SUMMARY STATISTICS

| Metric | Value |
|--------|-------|
| Total CSV Files | 41 |
| Total Rows Across All Files | 10,497 |
| Largest File (HOUR-MATERIAL_DATABASE) | 5,197 rows |
| Design Template Files | 2 (API, ASME) + variants |
| Labor Lookup Tables | 18 files |
| Add-on Component Files | 8 files |
| Unique Material Codes | ~8 identified (SA36, SA240-304/304L, SA312, SA479, GCST) |
| Unique Tank Diameter Ranges | ~30 ranges (from "Up to 1'" to "40'"+) |
| Components Tracked | 50+ item types |
| Quote Fields Captured | 11 main fields |


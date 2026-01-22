**Role:** Lead Data Analyst  
**Objective:** Map the structural and conceptual landscape using Hybrid Extraction protocols.

---

## CRITICAL: This stage has THREE MANDATORY SUB-STEPS executed in order.

### STEP 2A: UNIVERSAL FILE EXTRACTION (HYBRID PROTOCOL)

**Purpose:** Extract content from ALL files in `01_inputs/`.
**Constraint:** Must successfully read "Flat" PDFs (Images) using OCR fallback.

**Script:** Create `02_scripts/stage_2A_extraction.py`

**Requirements:**
1. **Load Config:** Read `04_documentation/project_config.json` to get `high_value_keywords`.
2. **Hybrid Logic:**
   - **Tier 1 (Text):** Attempt standard extraction (e.g., `pdfplumber`).
   - **Tier 2 (Quality Check):** IF text length < 50 chars OR < 30% valid dictionary words -> Trigger Tier 3.
   - **Tier 3 (OCR):** Use `pytesseract` to scan the images.
3. **The "High-Value" Trap:** - Check failed files against the `high_value_keywords` list.
   - If ANY High-Value file fails extraction, create `03_outputs/extraction_errors.md`.
4. **Manifest:** Generate `03_outputs/extraction_manifest.json`.

**Exit Condition:**
- If `extraction_errors.md` exists and contains High-Value targets, **STOP**. Report: "Critical Evidence Blocked."
- Else: Proceed to 2B.

---

### STEP 2B: REFERENCE DOCUMENT PROCESSING

**Purpose:** Build unified code dictionary from the successful extracts.

**Script:** Create `02_scripts/stage_2B_code_dictionary.py`

**Requirements:**
1. **Input:** Read `03_outputs/extraction_manifest.json`.
2. **Scan:** Hunt for "Code: Definition" patterns or "Column: Description" tables.
3. **Construct:** `03_outputs/code_dictionary.json`.
4. **Validation (The Bypass Protocol):**
   - **IF** dictionary is populated: Proceed.
   - **IF** dictionary is empty: 
     - Check Column Headers of data files. Are they "Self-Evident" (contain standard English words)?
     - **IF YES:** Create an "Inferred Dictionary" and Log Warning. **PROCEED.**
     - **IF NO:** (Headers are cryptic, e.g., "X_99", "VAR_1"): **STOP**. Report "Dictionary Failed" and ask for "Seed Dictionary."

---

### STEP 2C: PRIMARY DATASET ANALYSIS

**Purpose:** Analyze primary dataset schema with full code context.

**Script:** Create `02_scripts/stage_2C_schema_analysis.py`

**Requirements:**
1. **Map:** Compare Data Columns (from 2A) vs. Dictionary Definitions (from 2B).
2. **Report:** "Schema Coverage Report" (e.g., "We know what 80% of the columns mean").
3. **State:** Update `project_state.json` to **Stage 2 Complete**.

**Outputs:**
* `03_outputs/data_dictionary.json`
* `03_outputs/unique_codes_[fieldname].txt`

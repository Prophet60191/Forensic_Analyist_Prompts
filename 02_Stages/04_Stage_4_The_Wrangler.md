**Role:** Senior Data Wrangler  
**Objective:** Transform raw data into a high-integrity, "Analysis-Ready" dataset based on the Audit.

---

## ⚠️ HUMAN RATIFICATION PROTOCOL (MANDATORY)

**Before executing ANY destructive operations (drop rows, fill nulls, filter data):**

### STEP 1: GENERATE REMEDIATION PROPOSAL

**Create `03_outputs/remediation_proposal.md`** containing:
- Proposed actions (drop rows, fill nulls, type conversions)
- Row counts and percentages affected by each action
- Rationale for each proposed change
- Preview of first 5 affected records
- Total expected row delta (before vs. after)

### STEP 2: AWAIT APPROVAL

**Present proposal to user and EXPLICITLY WAIT** for approval:
- Display key metrics from proposal
- Ask: "Do you approve this remediation plan? Reply 'Approved' to proceed."
- **DO NOT EXECUTE** until user confirms

### STEP 3: CREATE IMMUTABLE BACKUP

**Before any modifications:**
- Check if `03_outputs/backup_pre_remediation.csv` exists.
- **IF EXISTS:** Do NOT overwrite. Print: "Using existing backup."
- **IF MISSING:** Save the current dataframe to that path.
- **CRITICAL:** Ensure we always possess the *original* state before *any* remediation attempts.

### STEP 4: EXECUTE WITH AUDIT TRAIL

**Only after approval and backup:**
- Execute `02_scripts/stage_4_data_cleaning.py`
- Log every action with before/after counts
- Save processed data to `03_outputs/cleaned_data/clean_data.csv`

---

## REPRODUCIBILITY TASK

**Script Requirements for `02_scripts/stage_4_data_cleaning.py`:**
1. Load data from `01_inputs/` or previous stage output
2. Execute each remediation action in sequence
3. Log "Row Delta" after each operation
4. Standardize date formats and string casing
5. Export to `03_outputs/cleaned_data/clean_data.csv`
6. Update `project_state.json` with new row count

**Validation:** Script must print:
- Initial row count
- Row delta for each operation
- Final row count
- Confirmation that backup exists

---

## MASTER JOURNAL SYNC

After cleaning complete:
1. **Read:** Access `04_documentation/Master_Project_Report.md`
2. **Format:** Create Section `## Stage 4: Data Wrangling & Processing`
3. **Append:** Use `mode='a'` to sync:
   - Remediation actions taken
   - Row Delta (Initial vs. Final)
   - Final Schema
   - Path to backup file
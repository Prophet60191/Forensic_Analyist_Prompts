**Role:** Project Manager with full file system access  

**Objective:** End the current session by serializing project state and updating logs.

---

## MANDATORY CLOSING SEQUENCE

### STEP 1: STATE SERIALIZATION (Critical)

**Update or Create `04_documentation/project_state.json`:**
```json
{
  "current_stage": <current stage number>,
  "primary_data_file": "<main data file name>",
  "row_count": <integer row count>,
  "last_script": "<path to last executed script>",
  "session_end": "<ISO timestamp>",
  "next_steps": "<brief description of pending work>"
}
```

### STEP 2: LOG ENTRY

**Update `04_documentation/project_log.md`:**

Create entry with today's date containing:

* **Completed Tasks:** Bulleted list of analysis executed
* **Scripts Executed:** Paths to all scripts run this session
* **New Artifacts:** List of new files created (CSVs, JSONs, scripts)
* **Current State:** One-sentence technical summary
* **Next Immediate Step:** Exact instruction to run next time

### STEP 3: MASTER REPORT SYNC

**Verify `04_documentation/Master_Project_Report.md`:**

* Confirm all stage findings from this session are appended
* If not, append missing entries with timestamps

---

## REPRODUCIBILITY TASK

**Script:** Create `02_scripts/session_closer.py` that:

1. Checks if `04_documentation/` exists
2. Updates or creates `project_state.json`
3. Appends to `project_log.md` (safe handling)
4. Reports confirmation

---

## OUTPUT

1. Confirmation: "`project_state.json` updated"
2. Confirmation: "`project_log.md` appended"
3. "Session saved. Safe to close."
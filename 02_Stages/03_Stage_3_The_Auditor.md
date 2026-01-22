**Role:** Forensic Data Auditor

**Objective:** Quantify data quality, identify logical paradoxes, and isolate noise.

**REPRODUCIBILITY TASK:**
1. **Scripting:** Create `02_scripts/stage_3_forensic_audit.py`. This script must:
    - Calculate null percentages per column.
    - Test for Paradoxes (e.g., Date A > Date B, impossible ranges).
    - Identify duplicate primary keys.
2. **Execution:** Run the script to generate the "Critical Quality Findings."

**MASTER JOURNAL SYNC:**
1. **Read:** Access `04_documentation/Master_Project_Report.md`.
2. **Format:** Create Section `## Stage 3: Data Audit`.
3. **Append:** Use Python (`mode='a'`) to sync the "Critical Quality Findings" and "Remediation Plan."
4. **Transparency:** Cite the script (`02_scripts/stage_3_forensic_audit.py`) for reproducibility.
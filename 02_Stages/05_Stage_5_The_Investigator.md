**Role:** Lead Data Investigator  
**Objective:** Execute targeted statistical analysis to test the Active Hypothesis, followed by a broad pattern sweep.

---

## REPRODUCIBILITY TASK

**Script:** Create `02_scripts/stage_5_statistical_analysis.py`.

### STEP 1: LOAD CONTEXT
The script must read `04_documentation/project_state.json` to check for an `"active_hypothesis"`.

### STEP 2: MODE SELECTION

**MODE A: TARGETED INQUIRY (If 'active_hypothesis' exists)**
1. **Identify Variables:** Extract `target_variables` from the state file.
2. **Type Safety Check (Critical):**
   - Check "Cardinality" (Unique Value Count) of numeric target variables.
   - **IF** Numeric Column has < 15 unique values: Treat as **Categorical/Ordinal**.
   - **ELSE:** Treat as **Continuous Numeric**.
3. **Select Test:** Automatically select the correct statistical test based on verified types:
   - **Num vs. Num:** Pearson/Spearman Correlation.
   - **Cat vs. Num:** ANOVA or T-Test.
   - **Cat vs. Cat:** Chi-Square Test.
4. **Execute:** Run the test and calculate p-values/Effect Sizes.
5. **Conclusion:** Generate a text string: "Hypothesis Supported (p < 0.05)" or "Inconclusive."

**MODE B: THE DRAGNET (Always Run)**
1. **Descriptive Stats:** Mean, median, mode, std_dev for all numeric columns.
2. **Distribution Checks:** Identify columns with high skewness (> 1.0).
3. **Outlier Detection:** Use IQR (Interquartile Range) to flag anomalies.

### STEP 3: EXPORT EVIDENCE
Save findings to `03_outputs/tables/`:
- `hypothesis_test_results.csv` (Mode A results)
- `descriptive_stats_summary.csv` (Mode B results)
- `outliers_detected.csv` (Rows flagged as anomalies)

---

## MASTER JOURNAL SYNC

1. **Read:** Access `04_documentation/Master_Project_Report.md`.
2. **Format:** Create Section `## Stage 5: Statistical Findings & Evidence`.
3. **Append:** Use Python (`mode='a'`) to write:
   - **The Verdict:** The specific result of the Active Hypothesis test (if applicable).
   - **The Discovery:** The "Top 3 Significant Insights" from the Dragnet analysis.
   - **The Evidence:** Links to the CSV tables generated.
4. **Transparency:** Cite `02_scripts/stage_5_statistical_analysis.py` for reproducibility.

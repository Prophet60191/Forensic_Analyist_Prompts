**Role:** Senior Data Reporter  
**Objective:** Synthesize evidence into visual narratives and an actionable Executive Summary.

**REPRODUCIBILITY TASK:**
1. **Scripting:** Create `02_scripts/stage_6_visualization_report.py`. This script must:
    
    **Part A: The Priority Figure (Hypothesis Verification)**
    - Read `04_documentation/project_state.json` to find `active_hypothesis`.
    - IF exists: Generate a specific chart for the `target_variables` (e.g., Scatterplot for Num/Num, Boxplot for Cat/Num).
    - Save as `03_outputs/figures/01_Primary_Finding.png`.

    **Part B: The Context Figures (General Overview)**
    - Generate distributions for key variables.
    - Generate time-series trends (if dates exist).
    - Save as `03_outputs/figures/Fig_X_[name].png`.

    **Part C: The Executive Summary**
    - Print a summary text block integrating the Stage 5 p-values and the visual trends.

2. **Execution:** Run the script to generate all artifacts.

**MASTER JOURNAL SYNC:**
1. **Read:** Access `04_documentation/Master_Project_Report.md`.
2. **Format:** Create Section `## Stage 6: Final Reporting & Executive Summary`.
3. **Append:** Use Python (`mode='a'`) to sync the Executive Summary, Recommendations, and Figure References.
4. **Seal:** Mark the Master Report as "Analysis Concluded."
5. **Transparency:** Cite `02_scripts/stage_6_visualization_report.py` so all figures can be regenerated.

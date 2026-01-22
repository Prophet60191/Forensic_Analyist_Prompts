**Role:**
You are the Lead Data Strategist.

**Objective:**
We have finished the standard reporting. Now we need to perform an advanced "Deep Dive" to uncover hidden connections, networks, or patterns.

**Context:**
The cleaned dataset is at `03_outputs/cleaned_data/clean_data.csv`.

**Task:**
1.  **Analyze the Potential:** Scan the dataset columns and identifying the *types* of advanced analysis possible.
    * *Example:* If you see "Names" and "Case IDs," we can do **Network Analysis** (Who works with whom?).
    * *Example:* If you see "Locations" or "Zip Codes," we can do **Geospatial Mapping**.
    * *Example:* If you see "Narrative Text," we can do **NLP/Sentiment Analysis**.
    * *Example:* If you see "Dates," we can do **Time-Series Decomposition** (Seasonality).

2.  **Generate The Menu:**
    * Propose **3 specific "Deep Dive Paths"** relevant to *this specific dataset*.
    * For each path, explain:
        * **The Technique:** (e.g., "Social Network Graph")
        * **The Insight:** (e.g., "Identify officer 'cliques' that co-offend frequently.")
        * **The Output:** (e.g., "A network visualization and a centrality table.")

3.  **The Interaction:**
    * Stop and ask me: *"Which Path would you like to execute? (1, 2, or 3?)"*
    * **WAIT** for my response.

4.  **Execution (Post-Selection):**
    * Once I select a path, generate the Python code to perform that *specific* analysis.
    * Save the results (Tables/Figures) to `03_outputs/deep_dive/` (create this folder if needed).

**Constraint:**
**DO NOT** execute any analysis yet.
**DO NOT** overwhelm me with code.
**Present the Menu and WAIT.**
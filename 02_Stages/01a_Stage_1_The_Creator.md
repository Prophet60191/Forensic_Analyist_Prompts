**Role:** Senior Data Engineer
**Objective:** Create a pristine analytical workspace from scratch.

**CONTEXT:** Triggered when `os.walk('.')` returns NO existing files (excluding system files).

---

## LOGIC FLOW (CRITICAL)
This protocol has TWO distinct phases separated by User Input.
1. **PHASE 1:** Triggered by "Genesis". Ends with **STOP**.
2. **PHASE 2:** Triggered by "Genesis: [Project Name]". Executes the Build.

---

## TASK 1: THE STAGING GROUND (PHASE 1)

**Trigger:** User types "Genesis" AND directory is empty.

1.  **Action:** Create directory `_TEMP_INGEST/`.
2.  **Prompt:** Pause and issue this exact request to the user:
    > "No existing project detected. I have initialized the staging area.
    > 1. Please upload your raw files into the `_TEMP_INGEST/` folder now.
    > 2. When finished, reply with: **'Genesis: [Your Project Name]'**."
3.  **TERMINATION PROTOCOL (HARD STOP):**
    * **DO NOT** generate `build_new_project.py`.
    * **DO NOT** create config files.
    * **DO NOT** proceed to Task 2.
    * **STOP EXECUTION** and await user reply.

---

## TASK 2: THE BUILDER (PHASE 2)

**Trigger:** User replies with "Genesis: [Project Name]" AND files exist in `_TEMP_INGEST`.

1.  **Create Script:** `02_scripts/genesis/build_new_project.py`.
2.  **Script Logic:**
    * **Define Target:** `Target_Root = [Project Name]/`.
    * **Default Config:** Write `[Target_Root]/04_documentation/project_config.json`:
        ```json
        {
          "project_name": "[Project Name]",
          "domain": "General",
          "high_value_keywords": ["important", "data", "readme"],
          "protected_dirs": [".git", ".venv"]
        }
        ```
    * **Architecture:** Create `01_inputs`, `02_scripts`, `03_outputs`, `04_documentation` inside `Target_Root`.
    * **Ingest:** Move ALL files from `_TEMP_INGEST/` into `[Target_Root]/01_inputs/`.
    * **State:**
        * Create `project_log.md`.
        * Create `project_state.json`: `{"current_stage": 1, "init_type": "fresh_build"}`.
    * **Cleanup:** Delete the empty `_TEMP_INGEST/` directory.
3.  **Execute:** Run script immediately.

---

## TASK 3: UNIVERSAL STACK (Post-Build)
*Run this only after Task 2 is confirmed successful.*

1.  **Create:** `[Target_Root]/requirements.txt`.
2.  **Content:**
    ```text
    pandas>=1.5.0
    numpy>=1.21.0
    openpyxl>=3.0.0
    PyPDF2>=3.0.0
    pdfplumber>=0.10.0
    pytesseract>=0.3.10
    pdf2image>=1.16.3
    Pillow>=10.0.0
    ```

**EXIT:** Report "Project [Name] Created. Data secured in 01_inputs. Ready for Stage 2."
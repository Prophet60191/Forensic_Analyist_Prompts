# Sanity Check (Agentic QA)

**User Instructions:**
Use this prompt whenever the AI gives you a number that feels "off". Fill in the **[INSERT METRIC]** section.

---

**Copy and paste the text below into your AI:**

```markdown
**Role:**
You are the Lead Quality Assurance (QA) Engineer with full execution privileges.

**Objective:**
I need to perform a "Unit Test" on a specific calculation to verify its accuracy.

**Target Metric:**
I want to verify the logic behind: **[INSERT METRIC HERE]**

**Task:**
Perform a "Trace Audit" using your internal Python environment:
1.  **Sample:** Extract 5 random rows from the dataframe used to calculate this metric.
2.  **Display:** Print a Markdown table showing the raw input columns for these 5 rows.
3.  **Manual Verification:**
    * *In the chat text*, manually calculate the math for these 5 rows.
    * Compare your manual math against the Python result.

**Constraint:**
**DO NOT** generate a script for me to run.
**EXECUTE** the sampling and calculation immediately.

**Output:**
* The Comparative Table (Raw Data vs. Processed Result).
* Your Manual Math walkthrough.
* A **PASS/FAIL** assessment.

```

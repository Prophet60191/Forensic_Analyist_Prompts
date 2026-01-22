**Role:**
You are the Lead Skeptic and External Auditor.

**Objective:**
I want you to aggressively critique the findings we have generated so far. We have established a narrative based on our analysis in Stage 5. I need you to find the holes in it.

**Context:**
Review the tables and findings from `03_outputs/tables/`.

**Task:**
Construct a "Vulnerability Assessment" that identifies the 3 strongest counter-arguments against our findings.

**Required Analysis Sections:**

1.  **Alternative Explanations:**
    * Are there other reasons for the trends we see? (e.g., Seasonality, Missing variables?)

2.  **Data Blindness:**
    * What crucial variables are *missing* from our dataset that might change the conclusion?

3.  **Statistical Weakness:**
    * Are the sample sizes large enough? Are the differences actually significant, or just noise?

**Output:**
A structured "Defense Memo" in Markdown. Conclude with a "Risk Score" (1-10) estimating how easily a critic could discredit our current statistical evidence.

```

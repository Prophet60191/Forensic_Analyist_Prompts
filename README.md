# Forensic Analyst "Stateful OS" System

## Overview
This prompt library transforms an LLM into a **Stateful Forensic Data Analyst**. It solves the problems of amnesia, hallucination, and reproducibility by enforcing a "Code Persistence Mandate."

## 🛑 SYSTEM INTEGRITY RULE: "THE NO TOUCH ZONE"
The directory `Forensic_Analyst_Prompts/` and all its subfolders are a **Read-Only Library**.
* **The AI must NEVER write, modify, or delete files in this directory.**
* **The AI must NEVER save session data or scripts to this directory.**
* **All Output** (Scripts, Reports, Data) must be directed exclusively to the active **Project Directory** (e.g., `[Project_Name]/02_scripts/`).

## Folder Structure
* **01_Constitution:** The supreme laws of the project.
* **02_Stages:** The linear workflow (Genesis → Intake → Audit → Cleaning → Analysis → Report).
* **03_Open_Close:** Scripts to start and end sessions safely.
* **04_Personas:** Specialized agents for brainstorming, Logic Mapping (Litigator), and Writing (Author).
* **05_Scripts:** (COMING SOON) Prompts to generate standalone utility tools (e.g., PII scrubbing, File Conversion).

## Quick Start
1. **New Project:** Paste `02_Stages/01_Stage_1_The_Architect.md`
2. **Resume Project:** Paste `03_Open_Close/01_The_Opener.md`
3. **End Session:** Paste `03_Open_Close/02_The_Closer.md`

## Version
**v2.3** — Updated 2026-01-21

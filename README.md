# Streamlining IT Procurement: Automating Standard Laptop Orders with Flow Designer

[![ServiceNow](https://img.shields.io/badge/Platform-ServiceNow-green.svg)](https://www.servicenow.com/)
[![Automation Tool](https://img.shields.io/badge/Engine-Flow%20Designer-blue.svg)](https://docs.servicenow.com/)
[![Application Scope](https://img.shields.io/badge/Scope-Global-orange.svg)](https://docs.servicenow.com/)
[![License](https://img.shields.io/badge/License-MIT-lightgrey.svg)](LICENSE)

---

## 📌 Executive Summary
This project addresses operational delays and manual tracking bottlenecks in IT procurement by leveraging **ServiceNow Flow Designer** to automate standard laptop orders[cite: 1]. Upon request approval, the custom workflow automatically generates a Catalog Task (`sc_task`), sets its description to *"Laptop needs to Configured"*, and routes it directly to the **Hardware** assignment group for device staging and configuration[cite: 1].

---

## 📑 Project Structure & Phase Documentation Index

This repository is organized into eight sequential phases detailing the complete project lifecycle from ideation to final video demonstration[cite: 1]:

| Phase File | Phase Title | Primary Focus & Highlights |
| :--- | :--- | :--- |
| **[`01_Brainstrom_and_ideation.md`](./01_Brainstrom_and_ideation.md)** | **Phase 1: Brainstorming & Ideation** | Problem statement, proposed automation solution, target stakeholders, and key value propositions[cite: 1]. |
| **[`02_requirement_Analysis.md`](./02_requirement_Analysis.md)** | **Phase 2: Requirement Analysis** | Detailed User Story, Functional Requirements (FR-01 to FR-05), NFRs, and system specifications[cite: 1]. |
| **[`03_Project_Design.md`](./03_Project_Design.md)** | **Phase 3: Project Design** | High-level process architecture, Flow Designer schema, and data mapping (`REQ` $\rightarrow$ `RITM` $\rightarrow$ `SCTASK`)[cite: 1]. |
| **[`04_Project_Planning.md`](./04_Project_Planning.md)** | **Phase 4: Project Planning** | Work Breakdown Structure (WBS), milestone timeline schedule, RACI framework, and risk mitigation plan. |
| **[`05_Project_Development.md`](./05_Project_Development.md)** | **Phase 5: Project Development** | Step-by-step Flow Designer build steps, Process Engine binding in Maintain Items, and execution pseudo-script[cite: 1]. |
| **[`06_Project_Testing.md`](./06_Project_Testing.md)** | **Phase 6: Project Testing** | Test strategy, full test execution matrix (TC-01 to TC-05), automated verification script, and test evidence[cite: 1]. |
| **[`07_Project_Documentation.md`](./07_Project_Documentation.md)** | **Phase 7: Project Documentation** | Administrator deployment manual, Standard Operating Procedure (SOP) user guide, and audit logging instructions[cite: 1]. |
| **[`08_Project_Demonstration.md`](./08_Project_Demonstration.md)** | **Phase 8: Project Demonstration** | Demonstration agenda, verification checklist, execution screenshots, and public video demonstration link[cite: 1]. |

---

## 🛠️ Tech Stack & Key Components

- **Platform Engine:** ServiceNow (Utah / Vancouver / Washington DC / Xanadu Release)
- **Workflow Automation:** Flow Designer (`Standard Laptop task`)[cite: 1]
- **Target Catalog Item:** Standard Laptop (`sc_req_item`)[cite: 1]
- **Application Scope:** Global[cite: 1]
- **Run As:** System User[cite: 1]
- **Assignment Group:** Hardware (`sys_user_group`)[cite: 1]

---

## 🔄 End-to-End Workflow Architecture

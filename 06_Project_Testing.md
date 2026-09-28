# Phase 6: Project Testing Phase

## 1. Executive Summary & Testing Strategy
The **Project Testing Phase** validates the end-to-end functionality, automated execution, database updates, and routing behavior of the **Standard Laptop Procurement Process** in ServiceNow[cite: 1]. The test strategy ensures that placing a request for a standard laptop through the Service Catalog automatically triggers the active Flow Designer workflow upon approval, correctly generating a Catalog Task (`sc_task`), assigning it to the **Hardware** group, and populating all required field attributes without manual intervention[cite: 1].

---

## 2. Test Plan & Execution Environment

### A. Environment & Roles
- **Test Instance:** ServiceNow Developer / Enterprise Instance[cite: 1]
- **Tester Role:** System Administrator (`admin`) / End User / Approver[cite: 1]
- **Target Catalog Item:** Standard Laptop (Lenovo ThinkPad / Carbon X1)[cite: 1]
- **Automated Workflow:** Flow Designer - `Standard Laptop task`[cite: 1]

### B. Test Execution Workflow

<img width="1366" height="768" alt="Screenshot (6)" src="https://github.com/user-attachments/assets/ace3cb63-3634-4ac6-8f91-9dd5104ba219" />
<img width="1366" height="768" alt="Screenshot (7)" src="https://github.com/user-attachments/assets/dae03b39-c89c-49c7-81a4-fed5426e52a1" />
<img width="1366" height="768" alt="Screenshot (8)" src="https://github.com/user-attachments/assets/b67274c5-fd07-48a4-9624-cbf14349be54" />
<img width="1366" height="768" alt="Screenshot (9)" src="https://github.com/user-attachments/assets/d705edf9-6696-446c-a18c-5a3c2f9f08ce" />



# Phase 7: Project Documentation Phase

## 1. Executive Summary & Documentation Overview
The **Project Documentation Phase** serves as the primary system, administration, and end-user guide for the **Standard Laptop Procurement Automation Project** implemented in ServiceNow[cite: 1]. This document details the system architecture, step-by-step deployment and configuration procedures, operational workflows, and maintenance policies required to support, audit, and scale the automated workflow driven by **Flow Designer**[cite: 1].

---

## 2. System Architecture & Component Mapping

The procurement engine operates across core ServiceNow modules in the **Global** scope[cite: 1]. The table below provides a full map of the system records and configuration components built during this project:

| Component Name | ServiceNow Module / Table | Technical Name / Field Value | Purpose / Description |
| :--- | :--- | :--- | :--- |
| **Catalog Item** | Service Catalog (`sc_cat_item`) | `Standard Laptop` | End-user facing catalog item under the **Hardware** category[cite: 1]. |
| **Workflow Engine** | Flow Designer (`sys_hub_flow`) | `Standard Laptop task` | Primary automated flow handling task creation and assignment routing[cite: 1]. |
| **Process Engine Binding** | Maintain Items (`sc_cat_item`) | Process Engine $\rightarrow$ Flow: `Standard Laptop task` | Links the Service Catalog item directly to the Flow Designer workflow[cite: 1]. |
| **Request Record** | Requests (`sc_request`) | Table: `sc_request` | Top-level request generated upon catalog checkout[cite: 1]. |
| **Requested Item Record** | Requested Items (`sc_req_item`) | Table: `sc_req_item` | Line-item record tracking order specifications (`RITM`)[cite: 1]. |
| **Catalog Task Record** | Catalog Tasks (`sc_task`) | Table: `sc_task` | Fulfillment task (`SCTASK`) created for the hardware support team[cite: 1]. |
| **Assignment Target** | User Groups (`sys_user_group`) | Group: `Hardware` | Dedicated queue receiving auto-created configuration tasks[cite: 1]. |

---

## 3. Administrator & Deployment Manual

### A. System Prerequisites & Privileges
- **ServiceNow Instance:** Utah / Vancouver / Washington DC / Xanadu release or newer.
- **User Roles Required:** `admin` or `catalog_admin` + `flow_designer_admin`[cite: 1].
- **Pre-configured Groups:** Active `Hardware` assignment group in the instance[cite: 1].

### B. Deployment Step-by-Step Instructions

1. **Flow Designer Setup:**
   - Navigate to **Process Automation $\rightarrow$ Flow Designer**[cite: 1].
   - Ensure the flow **Standard Laptop task** exists, is configured in the **Global** scope, runs as **System User**, and is set to **Active** status[cite: 1].
   - Verify action configuration step: **Create Catalog Task** attached to `Trigger -> Requested Item Record`[cite: 1].
   - Confirm target fields[cite: 1]:
     - **Short Description:** `"Laptop needs to Configured"`[cite: 1]
     - **Description:** `"Laptop needs to Configured"`[cite: 1]
     - **Assignment group:** `Hardware`[cite: 1]
     - **Approval:** `Approved`[cite: 1]

2. **Service Catalog Binding:**
   - Navigate to **Service Catalog $\rightarrow$ Catalog Definitions $\rightarrow$ Maintain Items**[cite: 1].
   - Search for and open **Standard Laptop**[cite: 1].
   - Under the **Process Engine** tab, confirm the **Flow** field points to `Standard Laptop task`[cite: 1].
   - Click **Update**[cite: 1].

---

## 4. Standard Operating Procedure (SOP) & User Guide

### A. End-User Order Placement Strategy
1. Log in to the ServiceNow Service Portal or Native UI[cite: 1].
2. Navigate to **Service Catalog $\rightarrow$ Hardware $\rightarrow$ Standard Laptop**[cite: 1].
3. Click **Order Now**[cite: 1].
4. Note the generated **Request Number** (`REQ0010001`) on the confirmation screen[cite: 1].

### B. Procurement Manager Approval Process
1. Navigate to **Self-Service $\rightarrow$ My Approvals** or open `sc_request` record `REQ0010001`[cite: 1].
2. Under the **Approvers** tab, locate the pending approval record[cite: 1].
3. Right-click approval row and select **Approve** (or change State to `Approved` and save)[cite: 1].

### C. Hardware Fulfillment Execution
1. Upon approval, Flow Designer instantly generates a Catalog Task (`sc_task`)[cite: 1].
2. Members of the **Hardware** group navigate to **Service Desk $\rightarrow$ My Groups Work** or **Catalog Tasks**[cite: 1].
3. Locate task with Short Description: `"Laptop needs to Configured"`[cite: 1].
4. Assign task to technician, stage device, complete configuration, and set Task State to **Closed Complete**.

---

## 5. System Maintenance, Operations & Auditing

- **Flow Execution Auditing:** Administrators can review execution logs by navigating to **Flow Designer $\rightarrow$ Executions** and filtering by Flow Name = `Standard Laptop task`[cite: 1].
- **Error Handling & Retry:** If a task fails to generate due to missing group data or system updates, re-evaluate the execution context in Flow Executions and click **Rerun Flow**.
- **Scope Compliance:** Do not alter application scope dependencies; the workflow must remain in the **Global** scope to maintain standard access across catalog tables[cite: 1].

---

## 6. Phase Documentation Visuals

### A. Flow Execution Logs & Audit Trail

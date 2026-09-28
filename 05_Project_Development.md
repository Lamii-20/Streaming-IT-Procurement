# Phase 5: Project Development Phase

## 1. Executive Summary & Implementation Overview
The **Project Development Phase** focuses on the technical build, workflow configuration, and automation implementation of the **Standard Laptop Procurement Process** in ServiceNow. Using **Flow Designer**, the manual overhead of handling laptop orders is replaced by an automated process that listens for Service Catalog requests, processes approvals, creates catalog tasks (`sc_task`), and routes them directly to the **Hardware** assignment group for device configuration and staging.

---

## 2. Comprehensive Implementation Steps

### Step 1: Initialize and Configure the Flow in Flow Designer
1. Log in to the ServiceNow instance as a System Administrator.
2. Navigate to **All $\rightarrow$ Process Automation $\rightarrow$ Flow Designer**.
3. Click **New $\rightarrow$ Flow** to initialize a new workflow.
4. Configure the **Flow Properties** as follows:
   - **Flow Name:** `Standard Laptop task`
   - **Description:** Automated workflow for standard laptop procurement and hardware task creation[cite: 1].
   - **Application:** `Global`[cite: 1]
   - **Run As:** `System User`[cite: 1]
5. Click **Submit** to create the flow definition[cite: 1].

### Step 2: Define Flow Trigger
1. Under the **Trigger** section, click **Add a Trigger**[cite: 1].
2. Search for and select **Service Catalog** from the trigger list[cite: 1].
3. Click **Done** to set the trigger[cite: 1].

### Step 3: Configure "Create Catalog Task" Action
1. Under the **Actions** section, click **Add an Action**[cite: 1].
2. Search for **Create Catalog Task** under **ServiceNow Core** and select it[cite: 1].
3. Configure the action inputs[cite: 1]:
   - **Request Item:** Drag and drop `Trigger -> Requested Item Record` into the **Requested Item** field[cite: 1].
   - **Table Name:** Auto-populates as `Catalog Task [sc_task]`[cite: 1].
   - **Short Description:** Enter `"Laptop needs to Configured"`[cite: 1].
   - **Description:** Select the `description` field and enter `"Laptop needs to Configured"`[cite: 1].
   - **Assignment group:** Select `"Hardware"`[cite: 1].
   - **Approval:** Select `"Approved"`[cite: 1].
4. Click **Done** to save the action configuration[cite: 1].
5. Click **Save** in the top navigation bar, then click **Activate** to publish the flow[cite: 1].

### Step 4: Bind Flow to Catalog Item Process Engine
1. Navigate to **All $\rightarrow$ Service Catalog $\rightarrow$ Catalog Definitions $\rightarrow$ Maintain Items**[cite: 1].
2. Search for the item **Standard Laptop** and open the record[cite: 1].
3. Navigate to the **Process Engine** tab[cite: 1].
4. Under the **Flow** field, select `Standard Laptop task`[cite: 1].
5. Click **Update** to save the catalog item configuration[cite: 1].

---

## 3. Pseudo-Code & Underlying Logic

While Flow Designer provides a low-code visual builder interface, the underlying business logic executed by the ServiceNow platform can be represented as follows:

```javascript
/**
 * Automated Task Generation Script for Standard Laptop Procurement
 * Scope: Global
 * Run As: System User
 */
(function executeAutomatedProcurement(inputs, outputs) {
    // 1. Capture the Trigger Requested Item Record (RITM)
    var requestedItemGR = inputs.trigger.request_item;
    
    if (requestedItemGR && requestedItemGR.isValidRecord()) {
        // 2. Initialize new Catalog Task (sc_task) Record
        var catalogTaskGR = new GlideRecord('sc_task');
        catalogTaskGR.initialize();
        
        // 3. Map Relationships and Set Required Field Values
        catalogTaskGR.request_item = requestedItemGR.getUniqueValue(); // Link to Parent RITM
        catalogTaskGR.short_description = "Laptop needs to Configured"; // Set Short Description
        catalogTaskGR.description = "Laptop needs to Configured";       // Set Detailed Description
        
        // 4. Assign to Hardware Group
        var hardwareGroupGR = new GlideRecord('sys_user_group');
        if (hardwareGroupGR.get('name', 'Hardware')) {
            catalogTaskGR.assignment_group = hardwareGroupGR.getUniqueValue();
        }
        
        // 5. Set Approval Status and State
        catalogTaskGR.approval = 'approved';
        catalogTaskGR.priority = 4; // Low Priority
        catalogTaskGR.state = 1;    // Open State
        
        // 6. Insert Record into Database
        var taskSysId = catalogTaskGR.insert();
        
        // 7. Output Result Log
        gs.info("Catalog Task " + catalogTaskGR.number + " successfully created for RITM " + requestedItemGR.number);
        outputs.created_task_sys_id = taskSysId;
    } else {
        gs.error("Flow Execution Failed: Invalid Requested Item record.");
    }
})(inputs, outputs);

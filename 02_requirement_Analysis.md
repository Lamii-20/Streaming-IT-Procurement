# Phase 2: Requirement Analysis Phase

## 1. Executive Summary & Project Objectives
The objective of this phase is to analyze, capture, and define all functional behavior, system requirements, software/hardware dependencies, and operational constraints for the project. Performing a thorough requirement analysis ensures system integrity, scalable data processing, and clear technical alignment prior to system design and implementation.

---

## 2. Functional Requirements (FR)

Functional requirements specify the direct actions, behaviors, inputs, and outputs the application must provide.

| Req ID | Feature Module | Requirement Description | Priority |
| :--- | :--- | :--- | :--- |
| **FR-01** | User Authentication | System must allow users and administrators to log in securely with role-based access control (RBAC). | High |
| **FR-02** | Data Ingestion & CRUD | System must allow users to Create, Read, Update, and Delete primary domain records via a clean user interface. | High |
| **FR-03** | Dynamic Filtering | System must enable real-time search, multi-column filtering, and conditional parameters without full page reloads. | High |
| **FR-04** | Analytics & Reporting | System must render key performance indicators (KPIs), metric summaries, and visual charts derived from database aggregations. | Medium |
| **FR-05** | Export & Audit Trail | System must support exporting search results to CSV/PDF and log transaction audit metadata for compliance. | Low |

---

## 3. Non-Functional Requirements (NFR)

Non-functional requirements specify the quality attributes, system performance, security standards, and operational benchmarks.

* **NFR-01 (Performance & Response Time):** Database queries and dashboard visual updates must respond within **$\le$ 2.0 seconds** under a standard concurrent user load.
* **NFR-02 (Scalability & Memory Efficiency):** System architecture must handle incremental dataset expansion while maintaining low execution overhead ($O(n)$ time complexity for list searches).
* **NFR-03 (Security & Data Integrity):** Inputs must be sanitized to prevent SQL injection and Cross-Site Scripting (XSS). Access to sensitive routes must enforce active session token verification.
* **NFR-04 (Usability & Responsiveness):** User interfaces must adapt responsively across modern desktop viewports ($\ge 1024\times768$) and mobile browsers.
* **NFR-05 (Availability & Reliability):** Application service target availability should reach **99.5%**, supported by fault tolerance and structured error handling.

---

## 4. Hardware & Software Specifications

| Component Category | Technology / Specification | Minimum Requirement | Recommended |
| :--- | :--- | :--- | :--- |
| **Processor (CPU)** | Intel Core i3 / AMD Ryzen 3 | Dual-Core, 2.0 GHz | Quad-Core, 3.0 GHz+ |
| **RAM Memory** | DDR4 RAM | 4 GB | 8 GB or higher |
| **Disk Storage** | Solid State Drive (SSD) | 10 GB free space | 25 GB free SSD space |
| **Operating System** | OS Environment | Windows 10/11 / Ubuntu Linux | 64-bit OS Environment |
| **Development IDE** | IDE / App Builder | VS Code / Eclipse / Oracle APEX | VS Code / Oracle APEX 23+ |
| **Runtime Environment** | Java / Node / Python | JDK 17 LTS / Node.js 18+ | JDK 21 LTS / Node.js 20+ |
| **Database Engine** | Relational Database | Oracle DB 19c / MySQL 8.0 | Oracle Cloud DB / PostgreSQL 15 |
| **Version Control** | Source Management | Git 2.x | Git + GitHub Repository |

---

## 5. Requirement Verification & Screenshots

### A. System Software Architecture & Flow

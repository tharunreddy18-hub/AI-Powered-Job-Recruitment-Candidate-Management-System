# Screenshots — AI-Powered Job Recruitment & Candidate Management System

This folder contains milestone-wise screenshots captured directly from the Salesforce org while building the **AI-Powered Job Recruitment & Candidate Management System**. Screenshots are organized into numbered folders that mirror the project's implementation milestones (M01–M17), so the build can be verified step by step alongside the [project report](../Documentation/AI_Powered_Job_Recruitment_System_Project_Report.pdf).

## Folder Index

| Folder | Milestone | What it Covers |
|---|---|---|
| `01_Account_Setup/` | M01 | Salesforce org home page and Setup page after account creation |
| `02_Objects/` | M02 | Creation of the `Job Opening` and `Candidate Application` custom objects |
| `03_Tabs/` | M03 | Custom tabs created for `Job Opening` and `Candidate Application` |
| `04_Fields_Relationships/` | M04 | All custom fields and master-detail relationships across `Contact`, `Job Opening`, and `Candidate Application` |
| `05_Validation_Rules/` | M05 | Validation rules for Offer Amount, Vacancies, and AI Candidate Score |
| `06_Approval_Process/` | M06 | High Salary Candidate Offer Approval process and its final actions |
| `07_Email_Templates/` | M07 | Classic email templates used across the approval and notification flows |
| `08_Email_Alerts/` | M08 | Email alerts linking templates to automation |
| `09_Flows/` | M09 | Record-triggered, scheduled, and screen flows |
| `10_Agentforce/` | M10 | Agentforce setup, Prompt Builder templates, and the Recruitment Assistant Agent |
| `11_Lightning_App/` | M11 | The custom Lightning App |
| `12_Page_Layouts/` | M12 | Page layout customization across five objects |
| `13_Dynamic_Forms/` | M13 | Dynamic Forms enablement and activation |
| `14_Users/` | M14 | Recruiter and Hiring Manager user creation |
| `15_Duplicate_Rules/` | M15 | Matching rule and duplicate rule for candidates |
| `16_Profiles/` | M16 | Recruiter Profile and Hiring Manager Profile configuration |
| `17_Roles/` | M17 | Final role hierarchy (Hiring Manager → Recruiter) |

## Screenshot Details

### 01_Account_Setup (Milestone 1 — Salesforce Account)
- `M01_Salesforce_Home_Page.png` — Salesforce Home page right after logging into the org.
- `M01_Setup_Page.png` — The Setup landing page used throughout the build.

### 02_Objects (Milestone 2 — Objects Creation)
- `M02_Job_Opening_Object_Form.png` — Custom object creation form for `Job Opening`.
- `M02_Job_Opening_Object_Created.png` — `Job Opening` object confirmed in Object Manager.
- `M02_Candidate_Application_Object_Form.png` — Custom object creation form for `Candidate Application`.
- `M02_Candidate_Application_Object_Created.png` — `Candidate Application` object confirmed in Object Manager.

### 03_Tabs (Milestone 3 — Tabs)
- `M03_Job_Opening_Tab_Form.png.png` — Tab creation wizard for the `Job Opening` object.
- `M03_Job_Opening_Tab_Created.png` — `Job Opening` tab visible in the app navigation.
- `M03_Candidate_Application_Tab_Form.png` — Tab creation wizard for the `Candidate Application` object.
- `M03_Candidate_Application_Tab_Created.png` — `Candidate Application` tab visible in the app navigation.

### 04_Fields_Relationships (Milestone 4 — Fields & Relationships)
**`M04.Contact_Fields/`**
- `Candidate_ID.png` — Auto Number field `Candidate ID` (C-{0000}) on Contact.
- `Experience_Level.png` — Picklist field (Fresher, Mid-Level, Senior).
- `Application_status.png` — Picklist field (New, Screening, Interview, Offer, Hired).

**`M04.JobOpening_Fields/`**
- `Department.png` — Picklist field (IT, HR, Finance, Sales).
- `Salary_Range.png` — Currency field.
- `Vacancies.png` — Number field.
- `Job_Status.png` — Picklist field (Open, Closed, On Hold).

**`M04.CandidateApplicationFields/`**
- `Candidate.png` — Master-Detail relationship to Contact.
- `Job_Opening.png` — Master-Detail relationship to Job Opening.
- `Applicatio_Date.png` — Application Date field.
- `AI_Candidate_Score.png` — Number field used for AI scoring.
- `Offer_Amount.png` — Currency field.
- `Application_Status.png` — Picklist field (Active, Inactive).
- `Approval_Status.png` — Picklist field (Pending, Approved, Rejected).

### 05_Validation_Rules (Milestone 5 — Validation Rules)
- `M05_Offer_Amount_Validation.png` — Rule blocking `Offer Amount <= 0`.
- `M05_Job_Vacancies_Validation.png` — Rule blocking negative `Vacancies`.
- `M05_AI_Candidate_Score_Validation.png` — Rule capping `AI Candidate Score` at 100.

### 06_Approval_Process (Milestone 6 — Approval Process)
- `M06_Approval_processes_activated.png` — Activated "High Salary Candidate Offer Approval" process.
- `M06_Final_approval_action.png` — Final approval/rejection field-update actions.

### 07_Email_Templates (Milestone 7 — Email Templates)
- `M07_Email_Tempelate.png` — Classic email templates created for approval and notification workflows.

### 08_Email_Alerts (Milestone 8 — Email Alerts)
- `M08_Email_alert.png` — Email alerts linked to the Candidate Application object.

### 09_Flows (Milestone 9 — Declarative Automation)
- `M09_High_Priority_Alert.png` — Record-triggered flow for AI score ≥ 85.
- `M09_Salary_Approval_Flow.png` — Record-triggered flow submitting high-salary offers for approval.
- `M09_Pending_Reminder_Flow.png` — Scheduled flow reminding recruiters of pending approvals.
- `M09_Offer_Calculation_Flow.png` — Screen flow guiding candidate application creation.

### 10_Agentforce (Milestone 10 — Agentforce AI)
- `M10_Candidate_Application_Summary_Prompt_Activated.png` — Candidate Application Summary prompt template.
- `M10_Candidate_Hiring_Risk_Analysis_Prompt_Creation.png` — Hiring Risk Analysis prompt template.
- `M10_RecruitmentAssistant_Agent_Active.png` — Recruitment Assistant Agent configuration.
- `M10_Recruitment_Assistant_Agent_Active.png` — Recruitment Assistant Agent active state.
- `M10_Agentforce_Test_Completion_Screenshot.png` — Agent tested against live candidate records.

### 11_Lightning_App (Milestone 11 — The Lightning App)
- `M11_Final_App_Created.png` — Completed "AI-Powered Recruitment & Candidate Management System" Lightning App.

### 12_Page_Layouts (Milestone 12 — Editing of Page Layouts)
- `M12_Candidate_Application_Layout.png`, `M12_Job_Opening_Layout.png`, `M12_Account_Layout.png`, `M12_Opportunity_Layout.png`, `M12_Contact_Layout.png` — Customized layouts for each object.

### 13_Dynamic_Forms (Milestone 13 — Dynamic Forms)
- `M13_Upgrade_Dynamic_Forms.png` — Upgrading the Details section to Dynamic Forms.
- `M13_Dynamic_Forms_Activated.png` — Dynamic Forms activated as the org default.
- `M13_Candidate_Application_Record.png` — Candidate Application record page using Dynamic Forms.

### 14_Users (Milestone 14 — Users)
- `M14_Recruiter_User_Creation.png` — Recruiter user account.
- `M14_Hiring_Manager_User_Creation.png` — Hiring Manager user account.

### 15_Duplicate_Rules (Milestone 15 — Duplicate and Matching Rules)
- `M15_Matching_Rules_Page.png` — Matching Rules setup page.
- `M15_Matching_Rule_Activated.png` — Activated "Unique Candidate – Email & Phone" matching rule.
- `M15_Duplicate_Rule_Activated.png` — Activated duplicate rule for Contact.

### 16_Profiles (Milestone 16 — Profiles)
- `M16_Profiles_Page.png` — Profiles list in Setup.
- `M16_Recruiter_Profile_Created.png` / `M16_Recruiter_Profile_Permissions.png` — Recruiter Profile and its permissions.
- `M16_Hiring_Manager_Profile_Created.png` / `M16_Hiring_Manager_Profile_Permissions.png` — Hiring Manager Profile and its permissions.

### 17_Roles (Milestone 17 — Roles & Role Hierarchy)
- `M17_Final_Role_Hierarchy.png` — Final role hierarchy: Hiring Manager → Recruiter.

---

**Project:** AI-Powered Job Recruitment & Candidate Management System
**Prepared by:** Gampala Tharun Reddy
**Email:** tharunreddy_gampala@srmap.edu.in
**Application Number:** AP24110010090

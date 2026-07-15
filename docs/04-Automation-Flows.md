# Automation & Flows

This document details every business rule, approval, and automation configured on the `Candidate_Application__c` and `Job_Opening__c` objects.

## 1. Validation Rules

| Rule Name | Object | Error Condition Formula | Error Message |
|---|---|---|---|
| Offer Amount Validation | Candidate Application | `Offer_Amount__c <= 0` | "Offer amount must be greater than zero." |
| Job Vacancies Validation | Job Opening | `Vacancies__c < 0` | "Vacancies cannot be negative." |
| AI Candidate Score Validation | Candidate Application | `AI_Candidate_Score__c > 100` | "AI Candidate score cannot exceed 100." |

## 2. Approval Process — High Salary Candidate Offer Approval

| Setting | Value |
|---|---|
| Object | Candidate Application |
| Entry Criteria | `Offer Amount > 1,000,000` AND `Application Status = Offer Submitted` |
| Approver | Automatically assigned — Manager of the record owner |
| Record Editability | Administrators only, while pending |
| Email Template | High Salary Candidate Offer Approval Notification |
| Initial Submitter | Record Owner (Recruiter) |
| On Approval | `Approval_Status__c` → `Approved` |
| On Rejection | `Approval_Status__c` → `Rejected` |

This ensures no recruiter can unilaterally finalize a high-value offer — every offer above the threshold is reviewed by the candidate's hiring manager before it becomes binding.

## 3. Email Templates (Classic)

| Template | Purpose |
|---|---|
| High Priority Candidate Application Notification | Notifies the recruiter when AI flags a candidate as high priority |
| High Salary Candidate Offer Approval Notification | Notifies the hiring manager that a high-salary offer needs review |
| Candidate Application Approval Status Notification | Informs the recruiter of the final approval decision |

All templates merge live record data (`Candidate Name`, `Job Opening`, `Experience Level`, `Offer Amount`, `AI Candidate Score`, `Application Status`) so recipients get full context without opening Salesforce.

## 4. Email Alerts

| Alert | Object | Template | Recipient |
|---|---|---|---|
| High Priority Candidate Application Email Alert | Candidate Application | High Priority Candidate Application Notification | Application Owner |
| High Salary Candidate Offer Approval Email Alert | Candidate Application | High Salary Candidate Offer Approval Notification | Manager (of record owner) |
| Candidate Application Approval Status Email Alert | Candidate Application | Candidate Application Approval Status Notification | Application Owner |

## 5. Flows

### Flow 1 — High Priority Candidate Application Notification (Record-Triggered)
- **Trigger:** Record created or updated
- **Entry Condition:** `AI_Candidate_Score__c >= 85`
- **Action:** Send High Priority Candidate Application Email Alert to the record owner

### Flow 2 — High Salary Offer Submission for Approval (Record-Triggered)
- **Trigger:** Record created or updated
- **Entry Condition:** `Offer_Amount__c > 1,000,000`
- **Action:** Submit the record to the "High Salary Candidate Offer Approval" process

### Flow 3 — Pending Candidate Application Follow-Up (Scheduled-Triggered)
- **Schedule:** Daily
- **Entry Condition:** `Approval_Status__c = Pending` AND `LastModifiedDate < TODAY() - 3`
- **Action:** Send a reminder email alert to the recruiter for applications stuck in approval for more than 3 days

### Flow 4 — Candidate Application Creation Wizard (Screen Flow)
A guided, multi-screen flow for recruiters:
1. **Screen 1 — Candidate Details:** Candidate, Job Opening, Application Date
2. **Screen 2 — Offer Details:** Offer Amount, Experience Level, AI Candidate Score
3. **Formula/Assignment:** Calculates the final offer amount
4. **Create Records:** Creates the `Candidate_Application__c` record
5. **Confirmation Screen:** "Candidate Application Created Successfully"

## Design Principles Applied

- **Entry conditions applied early** in every flow to avoid unnecessary execution and keep automation bulk-safe.
- **No updates inside loops** — all automation runs against clean, bulkified entry criteria.
- **Formula fields** (rather than flow-calculated values, where possible) are used for offer calculations and risk indicators to reduce automation overhead.

See [Agentforce AI](05-Agentforce-AI.md) for how AI Candidate Score and Risk Level are generated in the first place.

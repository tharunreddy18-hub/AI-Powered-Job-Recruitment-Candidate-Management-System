# Data Model

The recruitment system is built on three core entities: the standard **Contact** object (used to represent candidates) and two custom objects, **Job Opening** and **Candidate Application**, connected through master-detail relationships.

## Entity Relationship Overview

```
      Contact (Candidate)                Job_Opening__c
             │  1                              │  1
             │                                 │
             │  many                    many   │
             ▼                                 ▼
                Candidate_Application__c
        (Master-Detail → Contact, Master-Detail → Job_Opening__c)
```

Each **Candidate Application** record ties exactly one candidate to exactly one job opening, capturing the AI evaluation, offer, and approval details for that specific application.

## Contact (Candidate)

| Field Name | Data Type | Required | Notes |
|---|---|---|---|
| Candidate ID | Auto Number (`C-{0000}`, starts at 1) | — | Unique candidate identifier |
| Experience Level | Picklist: Fresher, Mid-Level, Senior | — | |
| Application Status | Picklist: New, Screening, Interview, Offer, Hired | — | |

## Job Opening (`Job_Opening__c`)

| Field Name | Data Type | Required | Notes |
|---|---|---|---|
| Job Title | Text (Record Name) | Yes | |
| Department | Picklist: IT, HR, Finance, Sales | — | |
| Salary Range | Currency | — | |
| Vacancies | Number | — | Must be ≥ 0 (enforced by validation rule) |
| Job Status | Picklist: Open, Closed, On Hold | — | |

## Candidate Application (`Candidate_Application__c`)

| Field Name | Data Type | Required | Notes |
|---|---|---|---|
| Application ID | Auto Number (`CA-{0000}`, starts at 1) | Yes | Record Name |
| Candidate | Master-Detail → Contact | Yes | |
| Job Opening | Master-Detail → Job_Opening__c | Yes | |
| Application Date | Date | — | |
| AI Candidate Score | Number | — | Must be ≤ 100 (enforced by validation rule) |
| Offer Amount | Currency | — | Must be > 0 (enforced by validation rule) |
| Application Status | Picklist: Active, Inactive | — | |
| Approval Status | Picklist: Pending, Approved, Rejected | — | Driven by the Approval Process |

## Object Configuration Notes

- Both custom objects have **Allow Reports**, **Allow Search**, and **Track Field History** enabled, so recruitment data can be reported on, searched, and audited over time.
- **Matching Rules** and **Duplicate Rules** are configured on `Contact` (Email + Phone, exact match) to keep candidate records unique — see [Security Model](03-Security-Model.md).
- All currency and number fields that feed AI or financial decisions (`Offer Amount`, `AI Candidate Score`) are protected by validation rules — see [Automation & Flows](04-Automation-Flows.md).

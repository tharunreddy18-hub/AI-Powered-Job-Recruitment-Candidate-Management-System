# Security Model

The system uses a layered Salesforce security model so that recruitment data — especially AI scores, salary figures, and approval decisions — is only visible to the right people.

## 1. Profiles

Two custom profiles were cloned from Standard User:

### Recruiter Profile
- Default app: AI-Powered Recruitment & Candidate Management System
- Read / Create / Edit on Contact, `Candidate_Application__c`, `Job_Opening__c`
- Read-only on Reports and Dashboards
- Read-only visibility of AI Candidate Score
- No approval or override permissions
- Session timeout: 2 hours of inactivity
- Password policy: expires every 90 days, minimum length 8

### Hiring Manager Profile
- Default app: AI-Powered Recruitment & Candidate Management System
- Read / Create / Edit / Delete on Contact, `Candidate_Application__c`, `Job_Opening__c`, Reports, Dashboards
- Can approve/reject high-salary offers and override AI recommendations
- Full visibility into AI Candidate Score, Risk Analysis, and Hiring Recommendations
- Session timeout: 2 hours

## 2. Role Hierarchy

```
              CEO
               │
        Hiring Manager
               │
           Recruiter
```

Roles control record-level visibility: a Hiring Manager can see all records owned by Recruiters below them in the hierarchy, while Recruiters see only records they own (plus what sharing rules explicitly grant).

## 3. Org-Wide Defaults (OWD)

| Object | Default Access |
|---|---|
| Candidate (Contact) | Private |
| Candidate Application | Private |
| Job Opening | Public Read Only |

## 4. Sharing Rules

- Recruiters can access their own assigned candidate and application records.
- Hiring Managers have read/write access to their team's records (via role hierarchy).

## 5. Field-Level Security

Sensitive fields are restricted at the field level, independent of object-level CRUD:

| Field | Recruiter | Hiring Manager / Admin |
|---|---|---|
| AI Candidate Score | Read Only | Full Visibility |
| Offer Amount | Visible | Full Visibility |
| Approval Status | Visible (read only where applicable) | Full Visibility |
| Risk Level (Agentforce output) | Hidden where required | Full Visibility |

## 6. Duplicate Prevention

A **Matching Rule** (`Unique Candidate – Email & Phone`, exact match on Email and Phone) feeds a **Duplicate Rule** on Contact that alerts and reports (rather than hard-blocks) on create and edit. This protects the accuracy of AI candidate scoring, risk analysis, and reporting without preventing legitimate edits.

## 7. Agentforce & AI Trust Settings

- **Data Masking** — enabled, to reduce exposure of sensitive data to the AI layer
- **Zero Data Retention** — enabled, so prompts and outputs are not retained beyond the interaction
- **Audit Logging** — enabled, for traceability of AI-assisted decisions
- Agentforce access is restricted to the **System Administrator** and **Hiring Manager** profiles only

## Why This Matters

Recruitment data is sensitive — candidate PII, salary figures, and AI-generated risk assessments all carry reputational and compliance weight. The layered model above ensures:

- Recruiters can do their job (manage applications) without seeing figures reserved for approval decisions.
- Hiring Managers get full context to make fair, informed decisions.
- AI outputs are generated and used under explicit trust and retention controls, not by default.

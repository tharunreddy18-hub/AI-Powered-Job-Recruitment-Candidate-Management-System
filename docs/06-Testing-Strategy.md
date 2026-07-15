# Testing Strategy

Testing covered the full AI-assisted recruitment lifecycle, from application creation to hiring approval and AI-driven prioritization, across three levels.

## 1. Unit-Level Verification

- AI candidate score handling — validated against the `AI Candidate Score Validation` rule (score capped at 100)
- Hiring risk analysis logic — validated by comparing Agentforce output against expected risk levels for sample records
- Approval status updates — verified that `Approval_Status__c` updates correctly to `Approved` / `Rejected` after a decision

## 2. Integration Testing

Verified that automation components work together correctly end to end:

- Relationships between Candidate ↔ Candidate Application and Job Opening ↔ Candidate Application resolve correctly
- Record-Triggered Flows fire on the correct entry conditions without duplicate execution
- The Approval Process is correctly invoked by the "High Salary Offer Submission" flow
- Email Alerts fire from the correct flow/approval step and merge the correct field data
- Agentforce prompt actions return relevant, record-accurate responses when triggered from the agent

## 3. User Acceptance Testing (UAT)

Conducted with representative users for each persona:

| Persona | Scenarios Tested |
|---|---|
| **Recruiter** | Creating/updating candidate records, submitting applications, submitting high-salary offers for approval, receiving reminders |
| **Hiring Manager** | Reviewing AI-generated summaries and risk insights, approving/rejecting offers |
| **System Administrator** | Managing flows, approval processes, and Agentforce configuration |

**UAT scenarios covered:**
- Creating and updating candidate records
- Submitting candidate applications
- Automatic AI candidate prioritization
- Submitting high-salary offers for approval
- Reviewing AI-generated summaries and risk insights
- Approving or rejecting offers
- Receiving email alerts and reminders

## Outcomes & Adjustments

- User feedback was collected and incorporated into the final build
- AI hiring indicators were made clearer on record pages
- Page layouts were optimized based on recruiter workflow feedback
- Smooth operation was confirmed across desktop and mobile devices (via Dynamic Forms)

## Data Validation (Migration)

Before functional testing began, migrated data was validated to ensure:

- Mandatory fields present: Candidate Name, Email, Job Opening, Proposed Offer Amount, Application Date
- No duplicate candidates (Matching/Duplicate Rules on Email + Phone)
- Correct relationships between Candidate, Job Opening, and Candidate Application
- Valid offer amount ranges and correct AI scoring logic, enforced by the existing validation rules and flows

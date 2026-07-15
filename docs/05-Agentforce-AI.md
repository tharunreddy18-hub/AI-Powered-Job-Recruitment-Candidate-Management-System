# Agentforce AI

The intelligence layer of the system is built on **Agentforce**, Salesforce's native AI agent platform, configured entirely through Prompt Builder and Agent Setup — no external AI service or custom code involved.

## 1. Enabling Agentforce & AI Trust

Before any AI component is built, Agentforce is enabled at the org level with the following trust controls active:

- **Data Masking** — reduces sensitive data exposure to the model
- **Zero Data Retention** — prompts/responses are not retained beyond the session
- **Audit Logging** — every AI interaction is logged for traceability

Access is scoped to the **System Administrator** and **Hiring Manager** profiles only (see [Security Model](03-Security-Model.md)).

## 2. Prompt Templates

### Candidate Application Summary Prompt
- **Type:** Summary
- **Object:** `Candidate_Application__c`
- **Purpose:** Produces a plain-language summary of an application — candidate name, job opening, experience level, proposed offer amount, AI candidate score, and application status — plus a callout of any risks, strengths, or special considerations relevant to the hiring decision.

### Candidate Hiring Risk Analysis Prompt
- **Type:** Flex
- **Object:** `Candidate_Application__c`
- **Purpose:** Analyzes an application to estimate:
  - Probability of successful hiring
  - Financial risk based on the proposed salary
  - Candidate stability and suitability
  - Overall hiring risk level (Low / Medium / High)
  - A recommendation on whether to approve or reject the offer

## 3. Recruitment Assistant Agent

A dedicated agent, **Recruitment Assistant Agent**, was created to bring these prompts into an interactive, conversational experience for recruiters and hiring managers.

**Topics assigned:**
- Candidate Application Summary
- Hiring Risk Analysis
- Offer Approval Guidance

**Actions configured (mapped to the prompt templates above):**
- Generate Candidate Application Summary
- Analyze Hiring Risk
- Recommend Approval Decision

**Data Library:**
| Object | Access |
|---|---|
| Contact (Candidate) | Read Only |
| `Job_Opening__c` | Read Only |
| `Candidate_Application__c` | Read Only |

Field-level access controls are enforced on top of this read-only scope, so the agent can never see or surface fields a given user profile isn't already permitted to view.

## 4. Testing the Agent

The agent was validated directly on live candidate application records using natural questions such as:

- "Summarize this candidate application."
- "Is this candidate safe to hire?"
- "What risks are involved in this salary offer?"

Responses were checked for accuracy against the underlying record data and clarity for a non-technical hiring manager.

## 5. Deployment

The agent is deployed to **Lightning Experience** and assigned to the Recruiter and Hiring Manager user bases, making it accessible directly from Candidate Application record pages.

## How This Fits the Bigger Picture

The AI layer doesn't replace human decision-making — it accelerates it. The Candidate Application Summary reduces the time a hiring manager spends reading through raw record data, and the Hiring Risk Analysis gives a structured, consistent starting point for a decision that is still made — and can still be overridden — by a human approver in the [Approval Process](04-Automation-Flows.md#2-approval-process--high-salary-candidate-offer-approval).

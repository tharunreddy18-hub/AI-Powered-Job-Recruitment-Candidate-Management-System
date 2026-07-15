# Architecture

## System Summary

The AI-Powered Job Recruitment & Candidate Management System is built entirely on the Salesforce Platform using declarative configuration — Custom Objects, Flow Builder, Approval Processes, and Agentforce — with no custom Apex code. This keeps the solution transparent, maintainable by admins, and easy to extend.

## High-Level Flow

```
                ┌─────────────────────┐
                │   Recruiter (User)   │
                └──────────┬───────────┘
                           │  creates / updates
                           ▼
                ┌─────────────────────┐
                │ Candidate Application │◄────── Master-Detail ──────┐
                │  (Candidate_Application__c) │                      │
                └──────────┬───────────┘                             │
          ┌────────────────┼────────────────┐                        │
          ▼                ▼                ▼                        │
   Validation Rules   Record-Triggered   Scheduled Flow        Job Opening
   (data integrity)      Flows           (pending reminders)  (Job_Opening__c)
          │                │                                          │
          │                ▼                                          │
          │        Email Alerts / Templates                           │
          │                │                                          │
          │                ▼                                          │
          │       Approval Process (high-salary offers)                │
          │                │                                          │
          ▼                ▼                                          │
   Agentforce AI    Hiring Manager Decision                            │
 (Summary + Risk)    (Approve / Reject)                                │
          │                                                            │
          └──────────────────► Contact (Candidate) ◄───────────────────┘
```

## Core Building Blocks

| Layer | Components |
|---|---|
| **Data Layer** | `Contact` (Candidate), `Job_Opening__c`, `Candidate_Application__c` |
| **Business Rules** | Validation Rules on Offer Amount, Vacancies, and AI Candidate Score |
| **Automation** | Record-Triggered Flows, Scheduled-Triggered Flow, Screen Flow |
| **Decision Layer** | Approval Process with manager-based routing |
| **Communication** | Classic Email Templates + Email Alerts |
| **Intelligence Layer** | Agentforce Prompt Templates + Recruitment Assistant Agent |
| **Presentation Layer** | Lightning App, custom Page Layouts, Dynamic Forms |
| **Security Layer** | Profiles, Role Hierarchy, Org-Wide Defaults, Sharing Rules, Field-Level Security |

## Why a Declarative-Only Approach

Building the system without Apex was a deliberate design choice:

- **Faster to build and easier to maintain** — any Salesforce admin can read and modify Flows, Approval Processes, and Validation Rules without needing development skills.
- **Lower governance overhead** — no Apex test classes, no governor-limit risk from custom code, no deployment dependencies on code coverage.
- **Native AI integration** — Agentforce's Prompt Builder and Agent framework are designed to work directly with declarative automation and standard/custom objects.
- **Faster iteration** — thresholds (e.g., the ₹10,00,000 approval trigger, or the AI score cut-off of 85) can be tuned directly in Flow entry conditions without a code deployment.

## Org Structure

The system lives inside a single Salesforce org and is exposed to end users through one dedicated Lightning App: **"AI-Powered Recruitment & Candidate Management System."** All custom objects, tabs, flows, and the Agentforce agent are scoped to this app so recruiters and hiring managers have a focused, uncluttered workspace.

See [Data Model](02-Data-Model.md) for the full schema and [Automation & Flows](04-Automation-Flows.md) for how each business rule is implemented.

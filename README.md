# AI-Powered Job Recruitment & Candidate Management System

![Platform](https://img.shields.io/badge/Platform-Salesforce-00A1E0?logo=salesforce&logoColor=white)
![AI](https://img.shields.io/badge/AI-Agentforce-blueviolet)
![Build](https://img.shields.io/badge/Build-Declarative%20%2F%20No%20Apex-success)
![License](https://img.shields.io/badge/License-MIT-yellow)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

A Salesforce CRM application built to streamline the end-to-end hiring lifecycle — **Candidate → Screening → Interview → Offer → Hiring** — using declarative automation (Flows, Approval Processes, Validation Rules) and **Agentforce AI** for candidate summarization and hiring-risk analysis. The entire system was built using Salesforce Admin tools, with no custom Apex development.

## Overview

Modern hiring teams often struggle with duplicate candidate records, lost applications, delayed interviews, and inconsistent decisions because they rely on spreadsheets, emails, and disconnected tools. This project delivers a centralized, secure, and AI-assisted recruitment platform on Salesforce that:

- Tracks all candidates, job openings, and applications in one place
- Standardizes screening with validation rules and duplicate/matching rules
- Automates hiring workflows using Record-Triggered, Scheduled, and Screen Flows
- Uses Agentforce AI to summarize applications and assess hiring risk
- Routes high-salary offers through a manager approval process
- Enforces role-based security across Profiles, Roles, and Sharing Rules

## Repository Structure

```
├── README.md
├── LICENSE
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
├── CHANGELOG.md
├── ROADMAP.md
├── .gitignore
├── .gitattributes
│
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   ├── bug_report.md
│   │   └── feature_request.md
│   └── PULL_REQUEST_TEMPLATE.md
│
├── Documentation/
│   └── AI_Powered_Job_Recruitment_System_Project_Report.pdf   # Full project report
│
├── docs/
│   ├── README.md                        # Documentation index
│   ├── 01-Architecture.md
│   ├── 02-Data-Model.md
│   ├── 03-Security-Model.md
│   ├── 04-Automation-Flows.md
│   ├── 05-Agentforce-AI.md
│   ├── 06-Testing-Strategy.md
│   ├── 07-Deployment-Guide.md
│   ├── 08-Team.md
│   └── FAQ.md
│
└── Screenshots/
    ├── README.md                        # Explains every screenshot below
    ├── 01_Account_Setup/
    ├── 02_Objects/
    ├── 03_Tabs/
    ├── 04_Fields_Relationships/
    ├── 05_Validation_Rules/
    ├── 06_Approval_Process/
    ├── 07_Email_Templates/
    ├── 08_Email_Alerts/
    ├── 09_Flows/
    ├── 10_Agentforce/
    ├── 11_Lightning_App/
    ├── 12_Page_Layouts/
    ├── 13_Dynamic_Forms/
    ├── 14_Users/
    ├── 15_Duplicate_Rules/
    ├── 16_Profiles/
    └── 17_Roles/
```

## Project Phases

| Phase | Description |
|---|---|
| **Phase 1** | Requirement Analysis and Planning |
| **Phase 2** | Salesforce Development — Backend & Configuration (Objects, Tabs, Fields, Validation Rules, Approval Process, Email Templates & Alerts, Flows, Agentforce AI) |
| **Phase 3** | UI/UX Development & Customization (Lightning App, Page Layouts, Dynamic Forms, Users) |
| **Phase 4** | Data Migration, Testing & Security (Duplicate/Matching Rules, Profiles, Roles) |
| **Phase 5** | Deployment, Documentation & Maintenance |

## Data Model

- **Contact** (Candidate) — Candidate ID, Experience Level, Application Status
- **Job Opening** (`Job_Opening__c`) — Department, Salary Range, Vacancies, Job Status
- **Candidate Application** (`Candidate_Application__c`) — Candidate (Master-Detail), Job Opening (Master-Detail), Application Date, AI Candidate Score, Offer Amount, Application Status, Approval Status

Full field-level detail: [`docs/02-Data-Model.md`](docs/02-Data-Model.md)

## Key Features

- **Validation Rules** — enforce valid offer amounts, non-negative vacancies, and a capped AI score
- **Approval Process** — automatically routes offers above ₹10,00,000 to the record owner's manager
- **Automation (Flows)** — high-priority candidate alerts, high-salary approval submission, pending-approval reminders, and a guided candidate application screen flow
- **Agentforce AI** — a Recruitment Assistant Agent with prompt templates for candidate summaries and hiring-risk analysis, backed by a read-only Data Library
- **Security** — custom Recruiter and Hiring Manager profiles, a two-tier role hierarchy, field-level security on sensitive fields, and private org-wide defaults with sharing rules

## Documentation

| Resource | Description |
|---|---|
| 📄 [Full Project Report (PDF)](./Documentation/AI_Powered_Job_Recruitment_System_Project_Report.pdf) | Complete write-up: requirements, data model, every milestone, security, testing, deployment |
| 📚 [`docs/`](./docs/README.md) | Topic-by-topic breakdown — Architecture, Data Model, Security, Automation, Agentforce AI, Testing, Deployment, Team, FAQ |
| 🖼️ [`Screenshots/`](./Screenshots/README.md) | Milestone-wise implementation screenshots with a full index |
| 🗺️ [`ROADMAP.md`](./ROADMAP.md) | Potential future enhancements |
| 📝 [`CHANGELOG.md`](./CHANGELOG.md) | Version history |

## Contributing

Contributions, suggestions, and issue reports are welcome — see [`CONTRIBUTING.md`](./CONTRIBUTING.md) and our [Code of Conduct](./CODE_OF_CONDUCT.md).

## License

This project is licensed under the [MIT License](./LICENSE).

## Author

**Gampala Tharun Reddy**
📧 tharunreddy_gampala@srmap.edu.in
🎓 Application Number: AP24110010090


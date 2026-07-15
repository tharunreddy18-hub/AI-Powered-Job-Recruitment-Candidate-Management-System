# Changelog

All notable changes to this project are documented in this file.
Format loosely follows [Keep a Changelog](https://keepachangelog.com/).

## [1.0.0] — Initial Release

### Added — Phase 1: Requirement Analysis and Planning
- Business requirements gathering and documentation
- Project scope and objectives definition

### Added — Phase 2: Salesforce Development (Backend & Configuration)
- Custom objects: `Job_Opening__c`, `Candidate_Application__c`
- Custom tabs for both objects
- Fields and master-detail relationships across Contact, Job Opening, and Candidate Application
- Validation rules: Offer Amount, Job Vacancies, AI Candidate Score
- Approval Process: High Salary Candidate Offer Approval
- Classic Email Templates (3) and Email Alerts (3)
- Flows: high-priority alert, salary approval submission, pending reminder, candidate application screen flow
- Agentforce AI: Prompt Templates, Recruitment Assistant Agent, Data Library configuration

### Added — Phase 3: UI/UX Development & Customization
- Lightning App: "AI-Powered Recruitment & Candidate Management System"
- Page layout customization across 5 objects
- Dynamic Forms enablement
- Recruiter and Hiring Manager user accounts

### Added — Phase 4: Data Migration, Testing & Security
- Matching Rule and Duplicate Rule for candidate deduplication
- Custom Profiles: Recruiter Profile, Hiring Manager Profile
- Role hierarchy: Hiring Manager → Recruiter
- Data migration from legacy sources via Data Import Wizard and Data Loader
- Unit, integration, and user acceptance testing

### Added — Phase 5: Deployment, Documentation & Maintenance
- Production deployment via Change Sets / metadata deployment
- User training and enablement across all personas
- Post-deployment monitoring and support process
- Full project documentation and milestone screenshots

## [Unreleased]

See [`ROADMAP.md`](ROADMAP.md) for planned future enhancements.

# Roadmap

The current release (v1.0.0) delivers a complete, declarative recruitment system on Salesforce. The ideas below are potential future enhancements — none are implemented yet, but they're natural next steps for anyone extending this project.

## Potential Enhancements

### Automation & Logic
- [ ] Migrate select Flow logic to Apex triggers/batch jobs for scenarios exceeding Flow governor limits at high volume
- [ ] Add Einstein Prediction Builder to complement Agentforce with a numeric, model-based candidate score
- [ ] Introduce multi-step approval (e.g., HR → Hiring Manager → Finance) for very high salary bands

### Candidate Experience
- [ ] Experience Cloud portal so candidates can track their own application status
- [ ] Self-service interview scheduling via Salesforce Scheduler
- [ ] SMS notifications (Twilio or similar) alongside existing email alerts

### AI & Agentforce
- [ ] Add a "Resume Parsing" action to the Recruitment Assistant Agent
- [ ] Extend the Hiring Risk Analysis prompt with department-specific risk weighting
- [ ] Add conversational analytics — "How many high-risk offers were approved this quarter?"

### Reporting & Analytics
- [ ] Pre-built dashboard: Recruiter Productivity (applications processed, average time-to-decision)
- [ ] Pre-built dashboard: Hiring Funnel (New → Screening → Interview → Offer → Hired conversion rates)
- [ ] Einstein Analytics / Tableau CRM integration for deeper hiring trend analysis

### Integrations
- [ ] Job board integration (LinkedIn, Indeed) for automatic candidate/application creation
- [ ] Slack notifications for high-priority candidates and pending approvals
- [ ] Background verification API integration triggered post-offer-approval

### DevOps
- [ ] Move from Change Sets to a proper CI/CD pipeline (SFDX + GitHub Actions) for future releases
- [ ] Add automated Flow/metadata validation checks on pull requests

## Contributing Ideas

Have an idea not listed here? Open a feature request using the issue template in [`.github/ISSUE_TEMPLATE/`](.github/ISSUE_TEMPLATE/).

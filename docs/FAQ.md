# Frequently Asked Questions

**Q: Does this project use any custom Apex code?**
No. The entire system — objects, automation, approvals, and AI — is built declaratively using Salesforce Admin tools: Object Manager, Flow Builder, Approval Process wizard, and Agentforce Prompt Builder / Agent Setup.

**Q: What triggers the approval process for an offer?**
Any Candidate Application where `Offer Amount > ₹10,00,000` and `Application Status = Offer Submitted`. It is automatically routed to the record owner's manager for approval — see [Automation & Flows](04-Automation-Flows.md).

**Q: How is a candidate flagged as "high priority"?**
When `AI Candidate Score >= 85`, a Record-Triggered Flow automatically sends a High Priority Candidate Application email alert to the recruiter who owns the record.

**Q: Can recruiters see the AI Candidate Score?**
Yes, but read-only. Recruiters cannot edit it, and richer AI outputs like Risk Level are limited to Hiring Managers and Administrators — see [Security Model](03-Security-Model.md).

**Q: What happens if two candidates have the same email address?**
The Matching Rule + Duplicate Rule on Contact (exact match on Email and Phone) flags the duplicate and alerts the user, rather than silently creating a second record.

**Q: How does the AI actually generate a hiring recommendation?**
Through two Agentforce Prompt Templates (Candidate Application Summary and Candidate Hiring Risk Analysis) surfaced via the Recruitment Assistant Agent, which reads directly from Salesforce data through a read-only Data Library — see [Agentforce AI](05-Agentforce-AI.md).

**Q: Is the AI recommendation final?**
No. It is a decision-support tool. The Hiring Manager always makes (and can override) the final approve/reject call through the standard Approval Process.

**Q: What license does this repository use?**
See [`LICENSE`](../LICENSE) at the root of the repository.

**Q: Can this be extended with Apex or Experience Cloud later?**
Yes — see [`ROADMAP.md`](../ROADMAP.md) for potential future enhancements.

# n8n Workflow Automation Portfolio

Selected **production** automations I designed and built as a Data Automation Engineer —
connecting Jira, Google Workspace, PostgreSQL, Tempo, Slack and email into hands-off
business processes across HR, finance and operations.

Each project folder contains:
- a **README** — the problem, the solution, how it works, and a diagram of the real node graph
- the **`workflow.json`** — the actual n8n export (sanitized), so you can inspect the real logic

## Projects

### [Automated Contractor Invoicing](./01-contractor-invoicing/)
Generates and delivers monthly contractor invoices end-to-end — zero manual work.  
*n8n, Google Sheets, HTTP/REST, PostgreSQL, Email, JavaScript, Webhooks, Scheduled trigger, Conditional logic, Sub-workflows, Date handling*

### [NDA Import & Risk Classification](./02-nda-risk-classification/)
Parses NDA submissions and auto-classifies contract risk for legal review.  
*n8n, Google Sheets, Jira API, HTTP/REST, Conditional logic*

### [Employee & Contractor Consent Form Automation](./03-employee-consent-form/)
End-to-end intake, document generation, and HR notification for photo/video consent.  
*n8n, Google Sheets, Google Docs, Google Drive, HTTP/REST, JavaScript, Webhooks, Conditional routing*

### [Jira Migration & Tempo Worklog Transfer](./04-jira-tempo-worklog-transfer/)
Migrates issues and their Tempo time logs between Jira projects, safely and at scale.  
*n8n, Google Sheets, Jira API, HTTP/REST, JavaScript, Scheduled trigger, Batch processing, Rate-limit handling, Conditional logic*

## Core skills demonstrated
- Workflow design & orchestration in **n8n** (advanced)
- **REST API** integration via webhooks and structured HTTP requests
- **Jira**, **Tempo**, **Google Workspace** (Sheets / Docs / Drive), **PostgreSQL**, **Slack**
- **SQL** (complex joins & aggregations) and **JavaScript** data transformation
- Conditional routing, batch processing, rate-limit handling, scheduled & event-driven triggers
- Reusable sub-workflows

## A note on the source files
These workflows were built for a production environment, so every `workflow.json` has been
sanitized before publishing: credentials, API endpoints/hosts, document IDs, personal data
and the employer's legal-entity details are removed or replaced with placeholders. The node
structure, expressions, SQL and business logic are preserved so the engineering is visible.
Details in [SANITIZATION.md](./SANITIZATION.md).

## Contact
**Samvel Mkhitaryan** — Data Automation Engineer
samomkhitaryan2005@gmail.com · Yerevan, Armenia

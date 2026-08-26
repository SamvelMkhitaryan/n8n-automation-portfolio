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

### [Employee Access Management](./05-employee-access-management/)
Automates access provisioning and revocation by cross-referencing an employee directory with an access-rules matrix.  
*n8n, Google Sheets, PostgreSQL, JavaScript, Webhooks, Sub-workflows, Complex SQL (CTEs, range_agg, CROSS JOIN LATERAL)*

### [Accounting ETL Pipeline](./06-accounting-etl-pipeline/)
Extracts accounting CSVs from email, transforms and loads into a PostgreSQL DWH, maps to Chart of Accounts, publishes to Google Sheets.  
*n8n, Gmail API (REST), PostgreSQL, Google Sheets, JavaScript, Base64 decoding, CSV parsing, Complex SQL*

### [Quarterly Budget Calculation](./07-quarterly-budget-calculation/)
Calculates quarterly budgets from Jira forms — FX conversion, fuzzy vendor matching (Levenshtein), and remote script execution.  
*n8n, Jira API (Forms API), PostgreSQL, JavaScript, SSH, Complex SQL (FX conversion, string_to_array/unnest)*

### [Jira Cross-Project Migration](./08-jira-cross-project-migration/)
Migrates Jira issues across projects preserving full Epic → Task → Subtask hierarchy with parent-child re-linking.  
*n8n, Jira API, JavaScript, Loop/batch processing, Rate-limit handling*

### [Financial Plan Pipeline](./09-financial-plan-pipeline/)
Consolidates multi-year financial plan data from PostgreSQL with automatic version resolution, outputs to Google Sheets.  
*n8n, PostgreSQL, Google Sheets, Webhooks, Multi-year schema handling, Version selection logic*

### [Onboarding & Offboarding Automation](./10-onboarding-offboarding-automation/)
Creates 13+ onboarding or 16+ offboarding Jira subtasks from a single comment trigger, pulling employee data from a directory.  
*n8n, Jira API (Forms API, comment triggers, subtask creation), Google Sheets, Conditional logic*

## Core skills demonstrated
- Workflow design & orchestration in **n8n** (advanced) — 10 production workflows, 19–55 nodes each
- **REST API** integration — Jira (including experimental Forms API), Tempo, Gmail, Google Sheets/Docs/Drive
- **PostgreSQL** — complex CTEs, window functions, `range_agg`, `daterange`, FX conversion, multi-schema versioning
- **JavaScript** — data transformation, CSV/base64 processing, fuzzy string matching (Levenshtein distance)
- **SSH** remote command execution for script-based data imports
- Conditional routing, batch processing, rate-limit handling, scheduled & event-driven triggers
- Reusable sub-workflows and error-handling patterns

## A note on the source files
These workflows were built for a production environment, so every `workflow.json` has been
sanitized before publishing: credentials, API endpoints/hosts, document IDs, personal data
and the employer's legal-entity details are removed or replaced with placeholders. The node
structure, expressions, SQL and business logic are preserved so the engineering is visible.
Details in [SANITIZATION.md](./SANITIZATION.md).

## Contact
**Samvel Mkhitaryan** — Data Automation Engineer
samomkhitaryan2005@gmail.com · Yerevan, Armenia

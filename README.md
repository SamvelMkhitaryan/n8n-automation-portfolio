# n8n Workflow Automation Portfolio

Production automations I designed and built as a Data Automation Engineer. These workflows run daily in real business environments — connecting Jira, Google Workspace, PostgreSQL, Tempo, Slack and email into hands-off pipelines across HR, finance and operations.

Every project folder contains:
- **README** with the problem, the solution, how it works, and a Mermaid diagram of the actual node graph
- **\`workflow.json\`** — the real n8n export (sanitized), so you can inspect the full logic, expressions and code

## Projects

| # | Project | What it does | Nodes | Stack highlights |
|---|---------|-------------|-------|-----------------|
| 1 | [Automated Contractor Invoicing](./01-contractor-invoicing/) | Generates and delivers monthly invoices end-to-end — zero manual work | 25 | n8n, PostgreSQL, Google Docs API, Email, sub-workflows, scheduled trigger |
| 2 | [NDA Import & Risk Classification](./02-nda-risk-classification/) | Parses NDA submissions and auto-classifies contract risk through a 12-branch decision tree | 30 | n8n, Jira API, Google Sheets, conditional routing, callable sub-workflow |
| 3 | [Employee Consent Form Automation](./03-employee-consent-form/) | End-to-end intake, document generation and HR notification for photo/video consent | 23 | n8n, Google Docs/Drive API, webhooks, multi-office routing |
| 4 | [Jira Migration & Tempo Worklog Transfer](./04-jira-tempo-worklog-transfer/) | Migrates issues and their Tempo time logs between Jira projects at scale | 15 | n8n, Jira API, Tempo REST API, batch processing, rate-limit handling |

## What these workflows demonstrate

**Workflow design** — multi-step pipelines with conditional routing, error handling, batch processing and reusable sub-workflows. The invoicing pipeline alone chains 25 nodes across scheduled triggers, API calls, document generation and email delivery.

**API integration** — structured HTTP requests to Jira, Tempo, Google Workspace (Sheets, Docs, Drive) and Slack. OAuth, pagination, rate-limit handling and retry logic where needed.

**Data engineering** — PostgreSQL writes for reporting, Google Sheets as operational datastores, ETL-style data mapping between systems, sequential ID generation.

**Business logic in code** — JavaScript Code nodes for data transformation, field mapping, date arithmetic and conditional branching that goes beyond what n8n's built-in nodes handle.

## A note on the source files

Every \`workflow.json\` is a genuine n8n export from a production environment. Before publishing, credentials, non-public endpoints, document IDs, personal data and employer details were removed or replaced with placeholders. The node structure, expressions, SQL and JavaScript logic are preserved exactly as built. Details in [SANITIZATION.md](./SANITIZATION.md).

## Contact

**Samvel Mkhitaryan** — Data Automation Engineer
samomkhitaryan2005@gmail.com · [LinkedIn](https://linkedin.com/in/samvel-mkhitaryan)

# Automated Contractor Invoicing

> Generates and delivers monthly contractor invoices end-to-end — zero manual work.

**Built with:** n8n, Google Sheets, HTTP/REST, PostgreSQL, Email, JavaScript, Webhooks, Scheduled trigger, Conditional logic, Sub-workflows, Date handling
**Workflow size:** 25 nodes
**Source:** [`workflow.json`](./workflow.json) — the actual n8n workflow (sanitized; see note below)

## Problem
Finance manually created dozens of contractor invoices each month: copying a template, looking up each contractor's rate and currency, numbering the invoice, storing it, and emailing it out. Slow, repetitive, and error-prone.

## Solution
A scheduled n8n workflow that runs at month-end and produces every invoice automatically.

## How it works
1. Triggers on a monthly schedule (with a manual test trigger for ad-hoc runs).
2. Copies an invoice template document and generates a sequential invoice number.
3. Looks up each payer's rate and currency from a Google Sheet and maps them into the document.
4. Fills the template via the Google Docs API (find-and-replace of placeholders).
5. Writes the invoice record to a PostgreSQL data warehouse for reporting.
6. Emails the finalized invoice to the contractor with clear next-step instructions.

## Impact
Removed a recurring monthly manual task and standardized invoice numbering and storage.

## Workflow diagram
```mermaid
flowchart TD
    N0(["⏱ When clicking ‘Test workflow’"])
    N1["🌐 Copy Template File"]
    N2["📅 invMonth"]
    N3["📊 Google Sheets"]
    N4["⚙ Create Inv Number"]
    N5["📊 Get Jira ID"]
    N6["⚙ Map Payer and Currency"]
    N7["📊 Get Payer Rate And Currency"]
    N8["✉ Send Email"]
    N9{"◇ If"}
    N10["🌐 Replace Text in Document"]
    N11["🗄 Postgres"]
    N12(["⏱ Schedule Trigger"])
    N13["⚙ Get Previos month"]
    N14["▶ HR Rates to DWH"]
    N15["▶ PE report"]
    N16["▶ HR Rates to DWH1"]
    N17["▶ Pe Report 1"]
    N18["▶ PPL dir to DWH"]
    N19["▶ PPL dir to DWH1"]
    N20["✉ Send Email Test Test"]
    N21["📊 Append row in sheet"]
    N22["📊 Clear sheet"]
    N23(["🔗 Webhook"])
    N24["✉ Send Email Test Test1"]
    N0 --> N19
    N1 --> N10
    N2 --> N4
    N4 --> N1
    N5 --> N2
    N6 --> N7
    N7 --> N5
    N9 --> N6
    N10 --> N3
    N10 --> N8
    N10 --> N20
    N10 --> N24
    N11 --> N22
    N11 --> N9
    N12 --> N19
    N13 --> N11
    N14 --> N15
    N15 --> N13
    N16 --> N17
    N17 --> N13
    N18 --> N16
    N19 --> N14
    N22 --> N21
```

---
*`workflow.json` is the real n8n export with its full node graph, expressions, SQL and
JavaScript logic intact. Credentials, endpoints, document IDs, personal data and the
employer's legal-entity details have been removed or replaced with placeholders. See
[SANITIZATION.md](../SANITIZATION.md).*

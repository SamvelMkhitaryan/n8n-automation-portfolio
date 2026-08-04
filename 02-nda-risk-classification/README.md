# NDA Import & Risk Classification

> Parses NDA submissions and auto-classifies contract risk for legal review.

**Built with:** n8n, Google Sheets, Jira API, HTTP/REST, Conditional logic
**Workflow size:** 30 nodes
**Source:** [`workflow.json`](./workflow.json) — the actual n8n workflow (sanitized; see note below)

## Problem
Legal received NDAs through a request form and had to read each one and manually tag risk factors (liability caps, validity period, unilateral clauses, transfer to affiliates, etc.) before logging them — tedious and inconsistent.

## Solution
An n8n workflow that ingests NDA form data and classifies terms through a rule-based decision tree.

## How it works
1. Reads structured data from the attached request form via the Jira API.
2. Runs the data through a tree of conditional checks (12+ IF branches) covering each risk factor.
3. Routes each matched risk into the correct category and writes a structured row to Google Sheets.
4. Updates the originating Jira issue so legal sees the classification in context.
5. Designed as a callable sub-workflow so it can be reused by other automations.

## Impact
Turned manual NDA triage into a consistent, auditable, one-pass classification.

## Workflow diagram
```mermaid
flowchart TD
    N0(["⏱ When clicking ‘Test workflow’"])
    N1["🌐 List attached form1"]
    N2{"◇ If"}
    N3["🌐 Read data from attached forms"]
    N4["📊 Google Sheets1"]
    N5{"◇ If1"}
    N6{"◇ If2"}
    N7{"◇ If3"}
    N8["📊 Exclusion of compensation for lost profits"]
    N9["📊 NDA validity period or Confidential Information storing period are not limited"]
    N10["📊 NDA is Unilateral"]
    N11{"◇ If4"}
    N12["📊 General total liability limitation"]
    N13{"◇ If5"}
    N14["📊 Possibility to transfer Confidential Information to affiliated parties"]
    N15{"◇ If6"}
    N16{"◇ If7"}
    N17["📊 Business restrictions"]
    N18["📊 Other 1"]
    N19{"◇ If8"}
    N20{"◇ If9"}
    N21["📊 Other 2"]
    N22["📊 Other 3"]
    N23{"◇ If10"}
    N24{"◇ If11"}
    N25["📊 Other 5"]
    N26["📊 Other 4"]
    N27["🟦 Jira Software1"]
    N28["🟦 Jira Software"]
    N29(["⏱ When Executed by Another Workflow"])
    N0 --> N4
    N1 --> N2
    N2 --> N3
    N3 --> N6
    N3 --> N7
    N3 --> N11
    N3 --> N13
    N3 --> N15
    N3 --> N16
    N3 --> N19
    N3 --> N20
    N3 --> N23
    N3 --> N24
    N3 --> N5
    N4 --> N27
    N5 --> N10
    N6 --> N9
    N7 --> N8
    N11 --> N12
    N13 --> N14
    N15 --> N17
    N16 --> N18
    N19 --> N21
    N20 --> N22
    N23 --> N26
    N24 --> N25
    N27 --> N1
    N29 --> N4
```

---
*`workflow.json` is the real n8n export with its full node graph, expressions, SQL and
JavaScript logic intact. Credentials, endpoints, document IDs, personal data and the
employer's legal-entity details have been removed or replaced with placeholders. See
[SANITIZATION.md](../SANITIZATION.md).*

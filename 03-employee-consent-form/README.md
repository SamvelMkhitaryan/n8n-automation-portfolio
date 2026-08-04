# Employee & Contractor Consent Form Automation

> End-to-end intake, document generation, and HR notification for photo/video consent.

**Built with:** n8n, Google Sheets, Google Docs, Google Drive, HTTP/REST, JavaScript, Webhooks, Conditional routing
**Workflow size:** 23 nodes
**Source:** [`workflow.json`](./workflow.json) — the actual n8n workflow (sanitized; see note below)

## Problem
HR manually generated a personalized consent document for each employee, shared it, chased responses, and tracked outcomes in a spreadsheet by hand.

## Solution
A webhook-driven n8n pipeline that handles the whole consent lifecycle.

## How it works
1. Receives the submission via webhook and branches on the response (accept / decline / cancel).
2. Maps the person's office/location data and generates a personalized document from a template.
3. Uploads and shares the file through the Google Drive API and inserts confirmation marks.
4. Notifies HR of the outcome through status-specific messages (success / declined / canceled).
5. Appends a record to a central Google Sheets registry for tracking.

## Impact
Fully automated a repetitive HR document + tracking process across multiple offices.

## Workflow diagram
```mermaid
flowchart TD
    N0(["🔗 Webhook"])
    N1["📁 Copy file"]
    N2["📄 Update a document"]
    N3["📁 Share file"]
    N4["🌐 HTTP Request"]
    N5["⚙ Code in JavaScript"]
    N6["⚙ Map Office"]
    N7["📊 Get Address"]
    N8["📊 Get row(s) in sheet"]
    N9(["🔗 Webhook1"])
    N10["⚙ Code in JavaScript1"]
    N11["🌐 Notify HR - Success"]
    N12["🌐 Notify HR - Declined"]
    N13{"◇ Switch"}
    N14["🌐 Find User by Email"]
    N15["🌐 Send to Employee"]
    N16["🌐 Notify HR - Canceled"]
    N17["📁 Share file1"]
    N18["📊 Append row in sheet"]
    N19["📁 Upload file"]
    N20["📁 Download file"]
    N21["📁 Share file2"]
    N22["📄 Add Checkmarks"]
    N0 --> N5
    N1 --> N2
    N2 --> N3
    N3 --> N21
    N5 --> N8
    N6 --> N7
    N7 --> N1
    N8 --> N6
    N9 --> N10
    N10 --> N13
    N11 --> N18
    N13 --> N14
    N13 --> N16
    N13 --> N22
    N13 --> N12
    N14 --> N15
    N17 --> N11
    N19 --> N17
    N20 --> N19
    N21 --> N4
    N22 --> N20
```

---
*`workflow.json` is the real n8n export with its full node graph, expressions, SQL and
JavaScript logic intact. Credentials, endpoints, document IDs, personal data and the
employer's legal-entity details have been removed or replaced with placeholders. See
[SANITIZATION.md](../SANITIZATION.md).*

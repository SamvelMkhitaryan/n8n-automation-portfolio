# Sanitization Notes

The `workflow.json` files in this repository are the real n8n exports, published for
portfolio purposes only. Before publishing, the following was **removed or replaced with
placeholders**, while the node graph, expressions, SQL and JavaScript logic were kept intact:

- **Credentials** — reduced to the credential *type* only (e.g. `googleSheetsOAuth2Api`);
  all IDs, names, tokens, API keys and passwords replaced with `REDACTED`.
- **Endpoints & hosts** — public API hosts (Jira, Tempo, Google, Slack) are kept to show the
  real integrations; any non-public host is replaced with `REDACTED_HOST`.
- **Document identifiers** — Google Sheets/Docs/Drive IDs and Jira form IDs replaced with
  `REDACTED_*` placeholders.
- **Personal data** — employee names and email addresses replaced with placeholders.
- **Employer details** — the company name is replaced with `ACME`, and embedded legal-entity
  directories (registered names + addresses) are redacted.
- **Webhook IDs** and other instance-specific identifiers removed.

Internal-only, non-exploitable references (such as Jira custom-field IDs and data-warehouse
column names) are intentionally left in place: they cannot be used without authenticated
access and they demonstrate that these are genuine, hand-built workflows.

No credentials or secrets are present in these files.

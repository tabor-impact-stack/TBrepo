# Jira similarity block and TS blueprint

Use these layouts exactly. Plain text only. Don't wrap them in code blocks.

## Part 2: Jira similarity block

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Jira Similarity and Historical Analysis
Account ID Searched: [Account UID]
Related or Duplicate Tickets Found: [Jira key(s) and summary, or "None found - first reported occurrence"]
Historical Resolution or Notes: [Summary of past fix, or "N/A"]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

If the search returns zero results, write only: "Historical Jira Findings: None found"

## Part 3: TS Jira blueprint

[Jira Ticket Blueprint - Technical Services]

Project: TS (Technical Services)
Issue Type: Bug / Technical Escalation
Summary: [Account Name] - [Account ID] | [Concise issue summary, for example: Shopify Plugin 400 bad request on checkout]
Priority: [P1 - Critical | P2 - Major | P3 - Normal | P4 - Minor]
Freshdesk Ticket Reference: [Freshdesk URL]
Affected IDs (Brand / Partner / Order / Action): [IDs]
Staging / Test Account Username: [Username]
Component / Category: [Selected template category, exactly as the template name]

Technical Diagnosis and Root Cause:
Surface Symptom: [Summary of the reported issue]
Root Cause Hypothesis: [Identified failure point, for example: missing API parameter, webhook timeout]
Prerequisites and Data Status: [Complete | Missing items, for example: Missing Order ID #12345, Missing HAR log]

Required Attachments:
Error Screenshots or Video Clips: [Attached | Not applicable]
HAR Files or Network Logs: [Attached | Missing]
Sample Payloads or CSV Exports: [Attached | Not applicable]

## Priority criteria

PENDING: the priority definitions haven't been confirmed yet. Until they are, set the priority to "[To be confirmed by specialist]" and say so in one line under the blueprint.

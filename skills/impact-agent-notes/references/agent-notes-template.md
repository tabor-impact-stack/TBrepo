# Agent Notes template

Use this exact layout. Plain text only: no markdown headers, bold, bullets, backticks, or code blocks. Start with the banner and no introduction. The closing line must start at the beginning of its line.

===
TICKET ACTION MODE | Response and Categorization
===

Canned response(s) used:
[Exact canned response title, for example "(AMGT) Partner: Mplace Appl Rejected (Media not Verified)", or "None - drafted from scratch"]

Technical diagnosis and root cause:
Surface symptom: [what the customer reported]
Root cause: [underlying issue found, or the marketplace evaluation result from the CSV]
Known tracker status: [No known tracker match | Matches tracker item: [Jira key or Slack Canvas item], confirmed in F0C5UQQBFQS]
Simplest path to resolution: [self-serve fix, Operator appeal submission, or the direct step before escalation]
Referenced sources: [sources that directly address this issue, or "None - diagnosed using core platform troubleshooting logic"]

Help link verification: [None | Verified via site:help.impact.com search: "Article Title" | Pre-approved legal directory]

Recommended status and SLA:
Status: [Open | Waiting on Customer | Waiting on Dev | Internal Escalation | Resolved], with a short reason
SLA action: [FRT stopped | RT clock running | RT clock paused on Dev | Auto-resolve initiated]
Catastrophe risk: [Normal (under 5 touchpoints) | HIGH RISK, 5+ touchpoints, escalate to TL or manager]

Queue:
[Standard Customer Solutions | Fraud | Compliance | BC | FN | GCH | TS | Not applicable]

Ticket action required:
[One concrete next step, referencing the official procedure where relevant]
===

## Example (marketplace rejection, media not verified)

===
TICKET ACTION MODE | Response and Categorization
===

Canned response(s) used:
(AMGT) Partner: Mplace Appl Rejected (Media not Verified)

Technical diagnosis and root cause:
Surface symptom: Partner asks why their marketplace application was rejected.
Root cause: MSG_MEDIA with MEDIA_PROPERTY_ENHANCEMENT, zero verified media properties. Remediable.
Known tracker status: No known tracker match
Simplest path to resolution: Partner verifies at least one media property, then the specialist submits the Operator appeal.
Referenced sources: Partners - Marketplace Applications how-to

Help link verification: None

Recommended status and SLA:
Status: Waiting on Customer, awaiting media verification before the Operator appeal
SLA action: RT clock running
Catastrophe risk: Normal (under 5 touchpoints)

Queue:
Standard Customer Solutions

Ticket action required:
Send the canned response, then submit the Operator appeal once the partner confirms verification.
===

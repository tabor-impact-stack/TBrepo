# SLA, status, and routing reference

Shared with impact-ticket-diagnosis. If you change one, change both.

## Ticket status and SLA effects

| Status | Effect |
| --- | --- |
| Waiting on Dev | Pauses the Resolution (RT) clock during engineering or Technical Services investigation. Check cadence is every 5 days. Use it for known tracker matches and anything needing engineering. |
| Waiting on Customer | Stops the SLA timer and starts the automated 7-day auto-resolve cycle. |
| Resolved | Finalizes the Resolution SLA. The ticket auto-closes after 3 days in this state. |

First Response (FRT) applies to brand-new, unreplied tickets. Sending the first draft stops it, so send it immediately.

## Touchpoints

Count specialist-to-customer exchanges in the thread. At 5 or more without resolution, flag the ticket as a "Catastrophe Risk / Escalation Candidate" in the notes and recommend escalating to a Senior Specialist or Team Lead.

## Auto-routing destinations

Respect automatic queue assignment. Don't advise moving tickets between peers in the same tier. Only recommend a specialized queue when the issue clearly falls outside standard Customer Solutions triage:

| Issue | Destination |
| --- | --- |
| Billing and payout finance | FINCON / Finance queue |
| Account closure or offboarding | Account Closure queue |
| Technical infrastructure or gateway issues | Technical Services (TS) queue, via the TS Escalation workflow |
| New client onboarding | Dynamo / Technical Setup queues |
| Fraud or risk triggers (for example, FRAUD_ATTRIBUTES_EVALUATION) | Fraud queue |

## Official procedures

- Customer Solutions Ticket Service Level Agreements (SLAs)
- Customer Solutions Ticket Auto-Routing Process
- How to Handle Freshdesk Tickets

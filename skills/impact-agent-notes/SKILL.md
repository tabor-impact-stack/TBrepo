---
name: "impact-agent-notes"
description: "Writes the internal Agent Notes block for impact.com Freshdesk tickets for Customer Solutions specialists. Use this whenever the specialist asks for Agent Notes, a response note, a ticket note, \"Create response note\", or a categorization for a ticket. Covers root cause, the canned response used and any changes made to it, Known Tracker lookup, help link verification, ticket status and SLA effect against the Customer Solutions SLA targets, touchpoint risk, unverified items, and the next ticket action. Do not use it for the customer-facing reply; use generate-response for that. Do not use it for deeper technical analysis with no note requested; use impact-ticket-diagnosis."
---

# impact.com Agent Notes

You're helping a Customer Solutions Specialist record an internal note on a support ticket. The note goes on the ticket record, not to the customer. It needs to be short, accurate, and easy for the next person to pick up.

This skill produces only the Agent Notes block. It doesn't write the customer reply. If the specialist also wants a reply, hand that to `generate-response`.

## Output

One block, in the layout in the template below. Plain text only. No introduction, no commentary before or after. Labels are ALL CAPS, in the order the template gives: QUEUE first, the diagnosis fields, the status and SLA fields, then SOURCES, UNVERIFIED ITEMS, and NEXT STEP last. Keep every field in the template and write "None" or "Not applicable" where a field doesn't apply. Keep each field to one line unless the case truly needs more.

## Step 1: Find the root cause

Customers often describe the symptom wrong. A "broken pixel" may be a coupon exclusion rule, and a dashboard mismatch may be an API payload problem. Record the real cause, not the customer's description. For a marketplace rejection, the root cause is the evaluation result from the decline report. If the `marketplace-decline-triage` skill has already run, use its result.

Check for the simplest fix first: self-serve settings, permissions, contract terms, and known status blocks come before any escalation or custom integration.

## Step 2: Known tracker check

If the ticket reports a bug, error, or tracking failure, run one Slack search of the Known Tracker Canvas (`F0C5UQQBFQS`) using the symptom keywords.
- Match: record the item ID under KNOWN TRACKER STATUS and confirm the canvas ID. Tell the specialist to link the ticket and set the status to `Waiting on Dev`.
- No match: record "No known tracker match" and move on. Don't retry.

## Step 3: Canned response used

Use the canned response title from the reply drafted with `generate-response` in this conversation. Record the exact title from the reference list in that skill under CANNED RESPONSE.

If the draft adapted the canned response, add the adaptation in a few words after the title, for example "(adapted: removed the 3DS step, added the order ID request)." Keep it to one line.

If the draft was written from scratch, record "None - drafted from scratch."

If no draft exists in this conversation, ask the specialist which canned response title they used, or whether they wrote it from scratch. Don't name a title from memory.

If the reply uses more than one canned response, list each title.

## Step 4: Sources and help links

Cite only sources that directly address this issue. Don't cite general memos, unrelated onboarding SOPs, or playbooks that don't cover this exact feature. If nothing applies, write "None - diagnosed using core platform troubleshooting logic."

For help links in the reply, record whether they were verified under HELP LINK VERIFICATION. A verified link came from a `site:help.impact.com` search. A legal link came from the pre-approved list. Record "None" if the reply has no links.

## Step 5: Status, SLA, and touchpoints

Set STATUS using the status and routing reference below:
- `Waiting on Customer` stops the SLA timer and starts the 7-day auto-resolve cycle.
- `Waiting on Dev` pauses the Resolution clock during engineering investigation.
- `Resolved` finishes the Resolution SLA. The ticket auto-closes after 3 days.
- A brand-new ticket with no reply yet: sending the first reply is the priority, because it stops the First Response clock. Record "FRT stopped" once it's sent, or "FRT running" if it's not yet sent.
- Count specialist-to-customer exchanges. At 5 or more without resolution, write `HIGH RISK, 5+ touchpoints, escalate to TL or manager` under CATASTROPHE RISK.
- Check the SLA targets in the reference below. Note in SLA ACTION whether the ticket is at or near its First Response or Resolution target, and whether the account is Enterprise or PDS, since those have shorter targets.

## Step 6: Unverified items

List anything in the note or the draft that you couldn't confirm under UNVERIFIED ITEMS: a navigation path, a help link, a canned title marked "confirm," a bracketed value with no data, or a policy point the sources don't settle. Write "None" if everything was confirmed. Don't guess to fill this field. Tabor prefers a flag to a guess.

## Step 7: Next step

Record QUEUE first: Standard Customer Solutions, Fraud, Compliance, BC, FN, GCH, TS, or Not applicable. Use the escalation skill for that queue to decide routing. Don't decide fraud or compliance outcomes in the note.

Write one concrete step under NEXT STEP. Where a procedure applies, name it, for example "Send the canned response, then submit the Operator appeal once the partner confirms verification." Don't tell the specialist to reassign tickets between peers in the same tier. Routing is automatic. Only recommend a specialized queue when the issue clearly falls outside standard Customer Solutions triage, using the routing table below.

## Writing rules

- Each line short. The closing line starts at the beginning of its line.
- No markdown, bullets, bold, backticks, or code blocks.
- Don't name individuals, CSMs, or internal QTP rule names beyond what the record already has.
- Don't add a last name or contact details anywhere in the note.
- Write NEXT STEP as the customer's step or the specialist's step. Never write that support will upload files, make changes, submit forms, or modify orders for the customer. For example, write "Customer uploads the invoice to the ticket."

## Reference: Agent Notes template

Use this exact layout. Plain text only: no markdown headers, bold, bullets, backticks, or code blocks. Start with the banner and no introduction. The closing line must start at the beginning of its line.

===
TICKET ACTION MODE | Response and Categorization
===

QUEUE: [Standard Customer Solutions | Fraud | Compliance | BC | FN | GCH | TS | Not applicable]

CANNED RESPONSE: [Exact canned response title, with any adaptation in one line, or "None - drafted from scratch"]

SURFACE SYMPTOM: [what the customer reported]
ROOT CAUSE: [underlying issue found, or the marketplace evaluation result from the CSV]
KNOWN TRACKER STATUS: [No known tracker match | Matches tracker item: [Jira key or Slack Canvas item], confirmed in F0C5UQQBFQS]
SIMPLEST PATH: [self-serve fix, Operator appeal submission, or the direct step before escalation]
HELP LINK VERIFICATION: [None | Verified via site:help.impact.com search: "Article Title" | Pre-approved legal directory]

STATUS: [Open | Waiting on Customer | Waiting on Dev | Internal Escalation | Resolved], with a short reason
SLA ACTION: [FRT stopped | RT clock running | RT clock paused on Dev | Auto-resolve initiated], with the target it is measured against
CATASTROPHE RISK: [Normal (under 5 touchpoints) | HIGH RISK, 5+ touchpoints, escalate to TL or manager]

SOURCES: [sources that directly address this issue, or "None - diagnosed using core platform troubleshooting logic"]
UNVERIFIED ITEMS: [None | short list]
NEXT STEP: [One concrete next step, referencing the official procedure where relevant]
===

### Example (marketplace rejection, media not verified)

===
TICKET ACTION MODE | Response and Categorization
===

QUEUE: Standard Customer Solutions

CANNED RESPONSE: (RAD) Partner: Mplace Appl Rejected (Media not Verified)

SURFACE SYMPTOM: Partner asks why their marketplace application was rejected.
ROOT CAUSE: MSG_MEDIA with MEDIA_PROPERTY_ENHANCEMENT, zero verified media properties. Remediable.
KNOWN TRACKER STATUS: No known tracker match
SIMPLEST PATH: Partner verifies at least one media property, then the specialist submits the Operator appeal.
HELP LINK VERIFICATION: None

STATUS: Waiting on Customer, awaiting media verification before the Operator appeal
SLA ACTION: RT clock running, 7-day Resolution target
CATASTROPHE RISK: Normal (under 5 touchpoints)

SOURCES: Partners - Marketplace Applications how-to
UNVERIFIED ITEMS: None
NEXT STEP: Send the canned response, then submit the Operator appeal once the partner confirms verification.
===

## Reference: status, SLA, and routing

Shared with impact-ticket-diagnosis and marketplace-decline-triage. If you change one, change all three.

### Ticket status and SLA effects

| Status | Effect |
| --- | --- |
| Waiting on Dev | Pauses the Resolution (RT) clock during engineering or Technical Services investigation. Check cadence is every 5 days. Use it for known tracker matches and anything needing engineering. |
| Waiting on Customer | Stops the SLA timer and starts the automated 7-day auto-resolve cycle. |
| Resolved | Finalizes the Resolution SLA. The ticket auto-closes after 3 days in this state. |

First Response (FRT) applies to brand-new, unreplied tickets. Sending the first draft stops it, so send it immediately.

### Customer Solutions SLA targets

Source: Customer Solutions Ticket Service Level Agreements (Confluence page 5784928329, updated Q2 FY27). Standard targets apply unless the account is Enterprise or PDS.

| Measure | Standard | Enterprise and PDS |
| --- | --- | --- |
| First response | 6 hours | 4 hours |
| Pending | 18 hours | 18 hours (confirm; the source lists one figure) |
| Resolution | 7 days | 5 days |

If the Pending target applies to a case and its meaning isn't clear from the ticket, add it to UNVERIFIED ITEMS rather than guessing.

### Touchpoints

Count specialist-to-customer exchanges in the thread. At 5 or more without resolution, flag the ticket as a "Catastrophe Risk / Escalation Candidate" in the notes and recommend escalating to a Senior Specialist or Team Lead.

### Auto-routing destinations

Respect automatic queue assignment. Don't advise moving tickets between peers in the same tier. Only recommend a specialized queue when the issue clearly falls outside standard Customer Solutions triage:

| Issue | Destination |
| --- | --- |
| Billing and payout finance | FINCON / Finance queue |
| Account closure or offboarding | Account Closure queue |
| Technical infrastructure or gateway issues | Technical Services (TS) queue, via the TS Escalation workflow |
| New client onboarding | Dynamo / Technical Setup queues |
| Fraud or risk triggers (for example, FRAUD_ATTRIBUTES_EVALUATION) | Fraud queue |

### Official procedures

- Customer Solutions Ticket Service Level Agreements (SLAs)
- Customer Solutions Ticket Auto-Routing Process
- How to Handle Freshdesk Tickets
---
name: "marketplace-decline-triage"
description: "Diagnoses rejected impact.com marketplace applications from Operator Marketplace Decline Report (Report ID 18008) CSV rows, or from partner questions about a marketplace application rejection. Use this whenever a specialist pastes a CSV row, a MESSAGE_KEY, FAILING EVALUATORS values, or asks whether a marketplace application is appealable, whether a rejection is a hard fail or remediable, or which canned response applies. Covers hard-fail, remediable, and inconclusive outcomes, the fraud queue exception, and canned response naming."
---

# Marketplace decline triage

Work out from the Operator decline row whether the application can be appealed, what the partner needs to do, and which canned response applies. Then pass the result back to the specialist, or to `generate-response` if they want a customer reply.

Give your answer in plain analytical terms. This is an internal decision, so don't write a customer draft unless asked.

## Inputs to read

From the CSV row, read two fields:
- `MESSAGE_KEY`: the broad category (MSG_COUNTRY, MSG_GENERIC, MSG_MEDIA, or INCONCLUSIVE).
- `FAILING EVALUATORS`: the specific checks that failed. This column name has a space in it, so match it carefully.

If the row is missing either field, ask the specialist for the full row before deciding. Don't guess an outcome from the partner's description.

Also read the account's Rakuten migration tag. The specialist supplies it with the row, from the account's tags. It decides the canned response prefix (see section 1). If the tag isn't in the input, ask for it before naming any response. Don't infer migration status from the partner's name, dates, or the row.

## Decision order

Work through the outcomes in this order. Stop at the first match, because a hard fail overrides everything else.

### 1. Hard fail: no appeal possible (MSG_COUNTRY or MSG_GENERIC)

Hard fail always wins. If the row contains both a hard fail and a remediable fail, there is no remedial path. The application can't be appealed.

- **MSG_COUNTRY:** the failing evaluator is HIGH_RISK_COUNTRY or ELEVATED_RISK_COUNTRY. Use the hard-fail country response.
- **MSG_GENERIC:** the failure is a high-risk IP, a disposable email, a terminal URL, offensive text, or fraud. Use the standard hard-fail response.
- **Fraud exception:** if FAILING EVALUATORS contains FRAUD_ATTRIBUTES_EVALUATION, tell the specialist to move the Freshdesk ticket to the Fraud queue immediately. Do this even if the rest of the analysis is still open.

Canned response names depend on the Rakuten migration tag on the account:
- Migrated: `(RAD) Partner: Mplace Appl Rejected (Hard-Fail Country)` or `(RAD) Partner: Mplace Appl Rejected (Hard-Fail)`
- All other partners: `(AMGT) Partner: Mplace Appl Rejected (Hard-Fail Country)` or `(AMGT) Partner: Mplace Appl Rejected (Hard-Fail)`. Use these for every non-migrated partner. These (AMGT) titles are confirmed in the Marketplace Applications how-to. Their approved customer text is in generate-response, so point the specialist there for the reply.

If the migration tag is missing, ask the specialist before naming the response. Don't guess.

### 2. Remediable fail: appeal possible (MSG_MEDIA)

The partner can fix their assets or data and pass a re-evaluation. The partner can't submit the appeal from their dashboard. The specialist submits it in Operator with the "Appeal Marketplace Decision" button, after the partner has made the change.

Match the failing evaluator to the response in the evaluator map below. In short:
- MEDIA_PROPERTY_ENHANCEMENT with zero verified media: Media not Verified
- MEDIA_PROPERTY_ENHANCEMENT with a URL error: Media Error
- FOLLOWER_COUNT_THRESHOLD_MET (under 500 non-TikTok followers or under 100 on TikTok) or URL_RISK (low traffic or reach): Media General. The partner should add and verify all active media properties.
- GEO_RISK (HIGH_RISK_GEO_MISMATCH): Media Issues

Use the same (RAD) or (AMGT) prefix rule as above.

### 3. Inconclusive: manual compliance review

The application is with Compliance in Operator Case Management. Check the case outcome:
- Approved: `(ASET) Partner: Marketplace Application (Approved)`
- Pending: `(COMP) Partner: Marketplace Application (Pending)`
- Rejected: send the standard hard-fail response from section 1

## What to return

Return these ALL-CAPS labels, in this order. Omit any that doesn't apply.

QUEUE: the queue to use, such as Standard Customer Solutions or Fraud (see the status and routing reference below).
OUTCOME: hard fail, remediable, or inconclusive.
APPEALABLE: yes or no, and who submits the appeal.
FAILING EVALUATORS: the evaluator(s) that drove the decision.
CANNED RESPONSE: the exact name, with the prefix chosen.
STATUS: a suggested ticket status, following the status and routing reference below. For example, a remediable case waiting on the partner is `Waiting on Customer`.
SOURCES: the Marketplace Applications how-to guide and the official procedure pages used.
NEXT STEP: one concrete action for the specialist.

If the specialist supplies the canned response text, use it exactly as written and don't edit it. If they don't, give the name only. Don't write the response text yourself.

## Don't cite the wrong source

When you list sources in the notes, cite only the Marketplace Applications how-to guide (https://impact.atlassian.net/wiki/spaces/CECS/pages/6613827850/Partners+-+Marketplace+Applications+how-to) and the official procedure pages. Don't cite unrelated memos or onboarding SOPs.

## Reference: evaluator map

Use the (RAD) prefix when the account carries the Rakuten migration tag, and (AMGT) for every other partner. The tag is supplied by the specialist with the decline row. If it's missing, ask before naming a response.

### Hard fail (no appeal)

| MESSAGE_KEY | Failing evaluator | Outcome | Canned response |
| --- | --- | --- | --- |
| MSG_COUNTRY | HIGH_RISK_COUNTRY, ELEVATED_RISK_COUNTRY | Hard fail | Mplace Appl Rejected (Hard-Fail Country) |
| MSG_GENERIC | High-risk IP, disposable email, terminal URL, offensive text, fraud | Hard fail | Mplace Appl Rejected (Hard-Fail) |
| Any | FRAUD_ATTRIBUTES_EVALUATION | Hard fail. Move the ticket to the Fraud queue. | Mplace Appl Rejected (Hard-Fail) |

### Remediable (appeal possible after partner fixes)

| MESSAGE_KEY | Failing evaluator | Partner action | Canned response |
| --- | --- | --- | --- |
| MSG_MEDIA | MEDIA_PROPERTY_ENHANCEMENT, zero verified media | Add and verify at least one media property | Mplace Appl Rejected (Media not Verified) |
| MSG_MEDIA | MEDIA_PROPERTY_ENHANCEMENT, URL error | Correct the media URL | Mplace Appl Rejected (Media Error) |
| MSG_MEDIA | FOLLOWER_COUNT_THRESHOLD_MET (under 500 non-TikTok, under 100 TikTok) | Add and verify all active media properties | Mplace Appl Rejected (Media General) |
| MSG_MEDIA | URL_RISK (low traffic or reach) | Add and verify all active media properties | Mplace Appl Rejected (Media General) |
| MSG_MEDIA | GEO_RISK (HIGH_RISK_GEO_MISMATCH) | Address the location mismatch | Mplace Appl Rejected (Media Issues) |

Appeals for every remediable case are submitted by the specialist with "Appeal Marketplace Decision" in Operator, not by the partner.

### Inconclusive (manual compliance review)

| Case outcome in Operator Case Management | Canned response |
| --- | --- |
| Approved | Partner: Marketplace Application (Approved), prefixed (ASET) |
| Pending | Partner: Marketplace Application (Pending), prefixed (COMP) |
| Rejected | Use the standard hard-fail response for the partner's prefix |

### Priority rule

If a row contains a hard fail and a remediable fail together, treat it as a hard fail. Don't offer an appeal.

## Reference: status, SLA, and routing

Shared with impact-ticket-diagnosis and impact-agent-notes. If you change one, change all three.

### Ticket status and SLA effects

| Status | Effect |
| --- | --- |
| Waiting on Dev | Pauses the Resolution (RT) clock during engineering or Technical Services investigation. Check cadence is every 5 days. Use it for known tracker matches and anything needing engineering. |
| Waiting on Customer | Stops the SLA timer and starts the automated 7-day auto-resolve cycle. |
| Resolved | Finalizes the Resolution SLA. The ticket auto-closes after 3 days in this state. |

First Response (FRT) applies to brand-new, unreplied tickets. Sending the first draft stops it, so send it immediately.

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
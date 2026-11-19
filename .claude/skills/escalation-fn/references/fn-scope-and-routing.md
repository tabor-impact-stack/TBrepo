# Finance Services scope, ticket types, and routing

Primary source: Finance Services Jira Queue Guide and Reference Hub (CECS, 6630539343, created August 2026). Older version, for the struck-through SLA note: Finance Services Jira Queue Guide (CECS, 6695944193); CSM Finance and Legal escalation process (AO, 6296404036).

## In scope for FN

| Category | Examples | FN? |
| --- | --- | --- |
| Account configuration | Funder type update, enabling multi-billing groups, adjusting finance controls | Yes |
| Finance reporting | Interpreting Partner or Advertiser Earnings and Balances, SOA questions | Yes |
| Invoices and billing | Invoice discrepancies against usage, historic invoice retrieval | Yes |
| Reconciling balances | Suspended accounts, overpayments, negative partner balances | Yes |
| Money movement | AFT between accounts, disbursements, bank transfers | No, GCH |
| Pure technical outages | API down, platform unavailable, tracking loss | No, TS |

Working rule: "Is the finance data or configuration right?" goes to FN. "Why isn't the system or integration working?" goes to TS. Money movement goes to GCH.

## Ticket types

| Type | Use for | Examples |
| --- | --- | --- |
| Information Request | General questions with no data change | Which report shows defaulted payments? |
| Service Request | Standard operational actions or configuration changes | Account audits, funder type updates, enabling multi-billing groups |
| Incident / Bug | Suspected miscalculations, missing transactions, broken finance reports | Invoice totals not matching AAL, duplicate finance entries |
| Account Reconciliation | Structured investigations into balances or suspended status | Reconciling historic overpayments, clearing negative balances |
| Task | Internal work supporting a larger ticket | Preparing an AAL export, comparing invoice against usage |

Some setups treat Account Reconciliation as a subtype of Service Request.

## Escalation targets

| Team | Domain | Escalate when |
| --- | --- | --- |
| Payments | Deposits, payouts, payment rails, cash ledger | Payout or advance discrepancies not explained by configuration |
| FinCore | Ledgers and internal finance data | Balances or earnings are misstated across accounts |
| TechFee | Fee logic and billing engine | Wrong fee lines, fee miscalculations, billing engine behavior |
| GCH / CHS | Money movement, vendor registration, tax filings, compliance | AFTs, defaulted payments, vendor forms, tax filings |
| TS | Technical issues outside finance | Finance-adjacent issues that prove to be outages or bugs |

FN keeps ownership of the ticket after an escalation, unless there's a deliberate handoff. The FN ticket records decisions and the customer-facing outcome.

## Triage steps (triage owner)

1. Check that required fields and attachments are present. If not, push the ticket back to the reporter with a clear request.
2. Confirm the ticket type. Misclassification causes SLA confusion later.
3. Set priority by impact, such as partner payments due soon versus informational requests.
4. Assign to an analyst. Complex reconciliations and billing configuration go to more experienced analysts.
5. If the ticket belongs to TS or GCH, reroute right away with an internal note saying why.

## Workflow states

General: Open, In Progress, Waiting on Customer or Internal, Pending Approval, Escalated or Waiting on Dependency, Resolved or Done, Reopened.

Incidents and bugs: Open, Investigating, Escalated to Dev or Waiting on Dev, Fix Ready for Verification, Done, Reopened.

Don't leave a ticket in a waiting state without a follow-up.

## Guidance SLAs

These are internal guidance targets, not contract terms.

| Priority or type | First response | Resolution |
| --- | --- | --- |
| High-priority finance blocker | 4 hours or less | 5 business days or less |
| Standard Service Request or Reconciliation | 1 business day or less | 10 business days or less |
| Information Request | 2 business days or less | As agreed with requester |
| Incident or Bug with engineering dependency | 1 business day or less | Aligned to product bug SLAs |

Some SLA figures in the FN guide are struck through. Don't use those.

## Discretionary Purse

- Use only when the amount is $250 or less per instance, is the only blocker to resolving the ticket, and standard refund or credit routes would be slower than the value at stake.
- Quarterly budget: $2,000.
- Request must include: amount, recipient entity (brand or partner), business justification.
- Approval: the designated approver, currently Finance Services or CS leadership. Use the role in drafts.
- If approved, GCH executes the transfer from the internal wallet. Don't include wallet or account numbers in drafts.
- Log every use in Jira and the shared tracking sheet.

## Required fields

Summary, description, brand or client name, account or platform ID, submitting department, environment, impacted regions or products, urgency and impact, Freshdesk ticket link, attachments.

Incidents and bugs also need: steps to reproduce (navigation path, filters, role), expected vs. actual, scope of impact, evidence.

Tip for descriptions: attach large tables as CSV or PDF and call out the key rows in the text.

## Good and poor examples

Good: "Funder type update for Brand X, partners blocked from payout." The description gives the current setting, the desired setting, the reason, the number of partners affected, the next payout date, and related TS or GCH tickets. The ticket includes account IDs, screenshots, and exports.

Poor: "Finance issue," with a description of "Client says payments are wrong" and no IDs or attachments.

## Cross-functional tracker

The CSM Finance and Legal tracker is a shared sheet, with notes due by end of day Friday. Columns: date added, CSM, client, blockage, ticket references, internal team, status, next steps, department comments. Statuses: Waiting for Customer, Waiting for Specific Team, In Progress, Escalated, Completed. Department reviews: Billing and Collections, GCH, Legal and Deal Desk, BizApps. Escalate after two review cycles with no progress, for significant customer impact, revenue or renewal risk, or an approaching deadline.

## Queue naming

The rules say FINCON, the Finance Services guide says FN, and the TS guide lists finance squads under IRFIN. Confirm before relying on any one name.

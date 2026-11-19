---
name: "escalation-gch"
description: "Prepares Global Clearinghouse (GCH) and account-closure escalations for impact.com Customer Solutions specialists. Use this whenever a specialist needs to send money-movement work to GCH, asks about a GCH request type, a CHS ticket, an AFT or funds transfer, a refund, a balance or deposit reallocation, a partner payout, a dormancy fee, a suspension override, a credit request, or a bank or vendor confirmation. Also use it for account closure and deactivation questions, such as \"close this account\", \"cancel my subscription\", \"program closure\", \"non-renewal\", \"churn\", \"bankruptcy closure\", \"Starter closure\", or \"PLG deactivation\". Say \"gch\", \"CHS\", \"AFT\", or \"account closure\" and it applies. Do not use it for TS technical faults (use escalation-ts), FN finance configuration (its own skill), or fraud and compliance decisions (its own skill). This skill only drafts. It never creates, edits, or transitions a Jira ticket, and it never sends a Freshdesk reply."
---

# GCH Escalation and Account Closure

You help a Customer Solutions specialist route money-movement work to Global Clearinghouse (GCH) and run the account closure steps correctly. You work as a senior escalation specialist: decide whether the work belongs to GCH at all, pick the right CHS request type, list the required fields, and state the SLA and the approval path.

You only draft. You never create, edit, comment on, or transition a CHS, CHO, BC, or IRFRAUD ticket, and you never send a Freshdesk reply. The specialist does every action manually.

## Step 1: Is this GCH work?

Money movement goes to GCH. Everything else does not.

- GCH work: moving funds between accounts, refunds, forfeitures, cost reversals, deposit allocation, payment queries, bank and vendor confirmations, partner proof of agreement, SLA and goodwill credits, suspension overrides, overdue payment reviews, and balances on a closing account.
- Not GCH work: a technical fault with a payment page or an API (TS), finance configuration or reconciliation questions (FN), fraud or compliance decisions (fraud and compliance skills), and collections negotiation (BC).

If the request is not GCH work, say so in one line and name the right team. Do not fill in a CHS form for it.

## Step 2: Choose the CHS request type

Use the CHS request types reference below. It lists every request type, the required fields, and the SLA. Pick the first type that clearly fits. If the request could fit two types, name both and ask the specialist which one the facts support.

Before drafting, check that every required field can be filled from the ticket. For each missing field, write "Missing: [field]". The automated reviewer on the CHS project comments on missing items, so a complete first submission saves a round trip.

Output for a GCH request, with these ALL-CAPS labels in this order. Omit any that doesn't apply:
QUEUE: GCH, or the team to route to if this isn't GCH work.
REQUEST TYPE: the request type, its SLA, and the start of the clock (the SLA runs from assignment, and first response is 24 to 48 hours after assignment).
REQUIRED FIELDS: the required-fields list, filled in or marked Missing.
APPROVAL: the approval level required, if the request moves money. Use the authority table below.
SUMMARY: a one-line summary the specialist can paste into the ticket description.
NEXT STEP: one concrete action for the specialist.

Plain text only. No markdown code blocks, no backticks, no bold, so it pastes cleanly into Jira.

## Step 3: Check approval authority for funds movement

Any AFT (account funds transfer) or other money movement needs approval at the right level. The requester must hold permission D54 (Digital Wallet Transfers) and complete 2FA.

| Level | Role | Approval limit |
| --- | --- | --- |
| 1 | Chief Officer | Up to $10m |
| 2 | VP | $5m to $10m |
| 3 | Senior Manager | $1m to $5m (eBay FBO up to $22m) |
| 4 | Manager | $500k to $1m |
| 5 | Team Lead | $0 to $500k |
| 6 | Specialist | Cannot approve |

State the amount, the currency, and the level needed. If the amount is above the specialist's own level, route it up. Do not suggest that the specialist approve their own transfer.

## Step 4: Escalation ladder

For a GCH question that is not a ticket, or a ticket that is stuck:
1. Specialist
2. Team Lead, or the on-duty Manager
3. GCH Manager
4. Senior Manager
5. VP, CFO, or General Counsel, for policy exceptions only

Use the role, not a name. Do not name individuals in drafts.

## Step 5: Coverage and timing

- GCH is offline on impact.com global holidays and South African public holidays. Tell the specialist the work will wait.
- GCH coverage is limited on US and UK bank holidays. Flag that the SLA may slip.
- Deposit allocation runs twice a day, Monday to Friday (procedure GCH P3-3).
- Partner payouts run Tuesday and Thursday at 09:00 SAST for threshold partners, and on the 1st and 15th for fixed-day partners. If a partner asks where a payout is, check the partner's payout schedule before promising a date.
- Dormancy fee: $10 USD per month on the direct model, or £25 GBP per month on the reseller model. It applies to partner balances inactive for 6 or more months. It is assessed around the 10th of the month and is non-refundable. Explain this before offering any waiver, and do not promise a waiver.

## Step 6: Account closure

Account closure is a separate flow with its own steps. Use the account closure reference below before answering any closure question. The short version:

1. Confirm the closure request came through a Need Help ticket from the advertiser. CSMs and RMs cannot submit it for the advertiser.
2. Check the account type. Starter (PLG) follows the Starter section, not the master process.
3. Check onboarding status. If still onboarding, send "(AMGT) Brand: Non-PLG Account Closure - Still in Onboarding" and assign to the Onboarding Manager.
4. Check notice timing against the renewal date. More than 30 days' notice is valid. Less than 30 days means the contract stands.
5. Once the BC ticket exists and the program closure date is confirmed, run the program closure steps and send the canned responses in order.
6. Balances go to BC. A zero balance closes in BC. A non-zero balance becomes a GCH "Account closure" ticket. GCH reviews it, then BC deactivates.

Closure responses must follow the 150-word and plain-text rules of the response skill. Canned response names must match the account closure reference exactly.

## Output rules for all parts

- Plain text only. No markdown, code blocks, backticks, or bold.
- No introduction or sign-off. Start with QUEUE, then the drafted content.
- Do not name individual employees, approvers, or contacts. Use the role.
- Do not copy watch-lists, named accounts, or regional fraud patterns into a draft.
- Never state a dollar figure, SLA, or approval level from memory. Use the tables in this skill.

## Known gaps

- The CHS SLA figures and the Discretionary Purse figures on the FN guide are different. Use the CHS table for GCH requests, and do not mix them.
- The W9 and W8 request page, the GCH Jira automation page, and the Jira configuration page are not yet read. Do not draft W9 or W8 steps until they are.
- The clawback, deposit allocation, and credit card payment pages are not yet read. Route those questions to the specialist's team lead until they are.
- Who runs closure steps is unconfirmed. The closure reference's Who does what list says Customer Solutions runs the program closure steps, and in the same entry says operational closure is now automated by BC and the older CS steps are outdated. The US Self-Serve and US Entry, EMEA, APAC pages say BC automation handles operational closure. Client comms come from the Revenue team on one page and the Success team on the other. Confirm the owner with the team lead before the specialist runs Step 3.

## Reference: CHS request types (CHS project)

Source: Global Clearinghouse Jira overview (CECS, 3656318977) and the GCH page (CECS, 6630015046).

Clearinghouse Services (CHS) are one-off requests submitted through the Clearinghouse Service Desk. Clearinghouse Operations (CHO) is internal to GCH only. The SLA starts when the ticket is assigned. First response is 24 to 48 hours after assignment. An automated reviewer checks requirements first and comments on anything missing.

### Payment Query

| Request | SLA | Required fields |
| --- | --- | --- |
| Unallocated deposit | 24 hours | Deposit date, amount, currency, proof of payment, Deposit Status Report screenshot |
| Deposit reallocation | 24 hours | Same as unallocated deposit, plus the account balance |
| Credit card receipt | 5 days | Required fields per the CHS form |
| Proof of payment | 5 days | Paystub ID, date, amount, currency |
| Manual partner-closure payment | 5 days | Balances, active contracts, payment method, payment cadence |

### Funds Movement

| Request | SLA | Required fields |
| --- | --- | --- |
| Account funds transfer | 5 days | From and to account names and IDs, amount, whether it is cross-currency, authorization form |
| Cost reversal for fraud | 5 days | Advertiser, partner, IRFRAUD ticket, authorization form |
| Balance refund | 5 days | Available balance, upcoming costs, bank confirmation, authorization form |
| Balance forfeiture | 5 days | Contracts, currency, balances, authorization form |

Approval: any transfer needs the approval level in the authority table above. The requester needs permission D54 and 2FA.

### Confirmations

| Request | SLA | Required fields |
| --- | --- | --- |
| Bank account verification | 5 days | Required fields per the CHS form |
| Vendor registration | 5 days | Order form, vendor form, signature needed |
| Partner proof of agreement | 5 days | Required fields per the CHS form |
| Audit review | 5 days | SOA in Excel, and whether it was sent |

### Delinquency

| Request | SLA | Required fields |
| --- | --- | --- |
| Suspension override | 3 days | Overdue balance, days overdue, reason, related ticket |
| Overdue payments review | 5 days | Overdue balance, fee type, 12 months of deposit confirmations |

### Credit Request

| Request | SLA | Required fields |
| --- | --- | --- |
| SLA credit | 5 days | Order form, credit value, calculation, related ticket |
| Goodwill credit | 5 days | Credit value, calculation, related ticket |

### Routing notes

- Balance on a closing account: BC creates a GCH ticket with issue type "Account closure". Use the account closure reference, not this table.
- Partner payout timing questions are not a CHS request. Check the payout schedule in Step 5.
- A request that asks GCH to decide whether a fee can be written off goes through the closure reference's approval rule.

### GCH reference facts

- Dormancy fee: $10 USD per month (direct) or £25 GBP per month (reseller). Assessed around the 10th. Non-refundable.
- Partner payouts: Tuesday and Thursday at 09:00 SAST for threshold partners. 1st and 15th for fixed-day partners.
- Coverage: offline on impact.com global and South African public holidays. Limited on US and UK bank holidays.

## Reference: account closure and deactivation

Sources: Account Closure & Deactivation Process (CS, 1916534931); Starter Edition Account Closure (CECS, 5743837185); US Self-Serve Account Closure (CECS, 4324589569); Account Closure Process, US Entry, EMEA and APAC (CECS, 4324393093).

### Which page applies

| Account type | Process |
| --- | --- |
| Starter Self Managed (PLG) | Starter Edition closure (5743837185) |
| US Self-Serve | US Self-Serve closure (4324589569). Creator and Advocate have extra steps. |
| US Entry (2.5K MRR) and above, EMEA, APAC | Master process (1916534931) and Entry, EMEA, APAC page (4324393093) |

### Who does what

- Advertiser: must submit a closure request through a Need Help ticket. This is the only valid form of notice.
- CSM or RM: tries to save the account. Cannot submit the request for the advertiser.
- Customer Solutions: confirms notice, sends canned responses, runs program closure steps in Operator or the UI, and resolves the ticket. Operational closure is now automated by BC. The older Customer Solutions steps are outdated.
- RM: submits a Billing Engine Change ticket for billing stop, then the Account Deactivate and Close BC ticket. Chooses the churn reason code in Salesforce.
- BC: completeness check, then deactivation in Operator. Converts to a GCH ticket when a balance exists.
- GCH: confirms zero partner and SaaS balances, then hands back to BC.
- Revenue team: client comms after confirmed closure.

### Key terms

- Non-renewal: the advertiser will not renew. Service ends at the subscription end date.
- Notice: the contractual notice to not renew, due 30 or more days before the renewal date.
- Subscription obligation: notice does not end the obligation. The advertiser still owes fees until the contract end date.
- Program closure date: the advertiser's preferred date to end partner contracts and tracking.

### Step 1: Confirm the request

1. The request must come through Need Help. If the CSM or RM sent it, ask the advertiser to submit it through Need Help.
2. Check account type. Starter (PLG) goes to the Starter section.
3. Check onboarding. If still onboarding, send "(AMGT) Brand: Non-PLG Account Closure - Still in Onboarding" and assign to the Onboarding Manager. Find the Onboarding Manager under Account Team in Operator.

### Step 2: Check notice timing

Compare the ticket creation date with the renewal date. Find the renewal date in Operator under Finance, Subscription Details, Subscription End Date, or in the advertiser's Subscription Period.

- Less than 30 days: the advertiser does not have the right to cancel the renewal. Send "(AMGT) Brand: Non-PLG Account Closure First Response - Non-renewal with sufficient notice < less than 30 days of renewal date". If there is no pushback, resolve.
  - Pushback about campaign strategy or resources: send "(AMGT) Brand: Non-PLG Account Closure - Best Practice", and tag the CSM in an internal note.
  - Pushback about issues: troubleshoot. Resolve once the issue is handled.
  - Continued pushback: tell the advertiser the request goes to the CSM. Internal note asks the CSM to check for a contract buyout. Assign the ticket to the CSM.
- More than 30 days: the notice is valid. Send "(AMGT) Brand: Non-PLG Account Closure - Non-renewal with sufficient notice: more than 30 days from renewal date". Internal note: the advertiser is within rights to non-renew, and the CSM should try to save the account. If it cannot be saved, get the BC Jira ticket from the CSM, or ask the RM to create one. Assign the ticket to the CSM.

Billing frequency and subscription fee are in Operator under Finance, Subscription Details. Check both before sending the canned response.

### Step 3: Take closure steps (after the BC ticket exists)

1. CSM reassigns the Freshdesk ticket to Customer Solutions once the BC ticket exists.
2. Confirm the program closure date with the advertiser. If it is not confirmed, ask for it.
3. Send "(AMGT) Brand: Non-PLG Account Closure - Final Program Closure Notice" (confirm).
4. Run the steps below, keeping the program closure date in mind.
5. Send "(AMGT) Brand: Non-PLG Account Closure - Only Performance Program Closure Confirmation" (confirm; no exact title), then resolve.
6. Payment or fee questions go to BC.

#### Program closure steps (Live advertiser account)

1. Expire all active partner contracts: Partners, select all out-of-office items, Contract, Expire. Set the expiration date to the program closure date. Toggle Withdraw All Switches. Use this comment: "This message is to inform you that we (impact.com) are closing down this account on behalf of the advertiser as they are no longer an impact.com customer as of {date}. Should you have any questions, please reach out to your point of contact at {brand name}." Expiry takes 30 to 45 seconds to register.
2. Reject all pending partner applications: Partners, Applications, select all, Reject, reason Other, specify "Program closure". Scroll to the bottom if there are more than 25.
3. Withdraw all proposals sent: Partners, Proposals Sent, select all, Withdraw.
4. Delete application workflows: Partners, Workflows. Turn off Impact AI application processing under Settings.
5. Delete catalogs: Content, Products, Product Catalogs. Deactivate, then delete.
6. Remove from marketplace: in Operator, on the Campaign page (not the Advertiser page), Basic Settings, tick "Do Not List in Marketplace", save.
7. Repeat for every campaign, including Creator campaigns.

If the advertiser wants to close a single campaign or program rather than the whole account, use the campaign closure guide (CECS, 3749873378) instead.

### Account Deactivate and Close (BC)

- RM submits a Billing Engine Change ticket to BC first, with the Operator ID and Salesforce URL. Agency-related accounts do not need their own billing stop.
- After the CC&R report shows billing has stopped, Business Operations marks the account Churned in Salesforce. The RM then chooses a confirmed churn reason code.
- Stand-alone products: Mediarails follows the decommission process. Activate's CSM ends the subscription in the Activate admin portal and notes the termination in Bill.com.
- After the billing stop ticket is complete, the RM (or CSM in EMEA and APAC) creates the BC "Account Deactivate & Close" ticket. One per account. For a parent with child accounts, file one ticket for the parent. Operator ID is required.

### BC completeness check

- Billing engine is stopped.
- SaaS balances are accounted for, including reserves.
- Final settlement outreach has been made, or write-off approval has been obtained under the finance approval matrix.

Then:
- Zero balance: BC deactivates in Operator.
- Any balance, positive or negative: BC converts the ticket to a GCH ticket with issue type "Account closure". The GCH ticket states what is owed or payable and any actions for GCH. BC deactivates after GCH review.
- Technical blockers to closure: escalate to Product Finance. Example: IRFIN-4355.

### GCH review of a closing account

- Partner fee balance from $0 to $1,000: can move to closing with no approval.
- Overdue or upcoming partner fee balance above $1,000: needs written write-off approval from the named approver before closure. Use the role "fee write-off approver" in drafts. Do not name the person.

### Non-payers

- At 60 days overdue: CSM marks the account churn risk in Salesforce.
- At 90 days: CSM creates a BC ticket for collections.
- At 180 days overdue: the account is fully deactivated.
- No settlement: the account closes at renewal.
- Settlement reached: BC runs the closure steps above.

### Reactivation

- Non-payer deactivation: the advertiser needs a BC ticket for case-by-case review. Reactivation depends on the account status in internal systems.
- A Closed account in Operator cannot be reactivated. It needs a new contract and a new onboarding.

### Bankruptcy (Legal guidance)

- Customer Solutions cannot terminate a contract early because of bankruptcy, unless the brand asks us to. Trustees can keep the contract running.
- Amounts owed before the filing cannot be billed.
- On first outreach, ask the brand for its bankruptcy details and documents.
- Do not reverse transactions. Place them on NQTP. The data is still needed, even if the transactions are later reversed out of the system.

### Starter Edition closure (5743837185)

BC Jira:
- Space: Billings and Collections (BC)
- Work type: (Epic) PLG Deactivation
- Summary: Customer Cancellation Request [Brand Name] [Brand ID]
- Request type: Credit Request. Sub-type: Subscription Service Fees (SaaS or Professional Services).

Description:
- Timestamped screenshot of the advertiser's closure request
- Refund required: Yes or No
- Locked-action waiting period: the locking date of the latest pending action, if any
- Requested closure date: ASAP

Fields:
- Operator ID: the advertiser account ID
- Billing engine option: Mid-Term Termination or Billing Stop
- Related product: Performance
- Salesforce opportunity URL
- Region: the account's region
- Cancellation reason (choose one):
  - Advertiser Tech Product Issues
  - Agency Issues
  - Business Challenges
  - Combine Service and Technology
  - Contract Type Change
  - Customer Profile Issue
  - Fraud
  - Impact Support or Management
  - Lack of Productive Partnerships
  - Lack of Resources
  - Nonpayer
  - Bankruptcy
  - Pricing
  - Lack of Features or Software Did Not Meet Expectations
  - Software Issues

### Feedback and changes to these pages

File a CO Jira and assign it to the page owner. The older CEE Jira is no longer used.
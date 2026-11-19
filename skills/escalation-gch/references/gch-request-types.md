# GCH request types (CHS project)

Source: Global Clearinghouse Jira overview (CECS, 3656318977) and the GCH page (CECS, 6630015046).

Clearinghouse Services (CHS) are one-off requests submitted through the Clearinghouse Service Desk. Clearinghouse Operations (CHO) is internal to GCH only. The SLA starts when the ticket is assigned. First response is 24 to 48 hours after assignment. An automated reviewer checks requirements first and comments on anything missing.

## Payment Query

| Request | SLA | Required fields |
| --- | --- | --- |
| Unallocated deposit | 24 hours | Deposit date, amount, currency, proof of payment, Deposit Status Report screenshot |
| Deposit reallocation | 24 hours | Same as unallocated deposit, plus the account balance |
| Credit card receipt | 5 days | Required fields per the CHS form |
| Proof of payment | 5 days | Paystub ID, date, amount, currency |
| Manual partner-closure payment | 5 days | Balances, active contracts, payment method, payment cadence |

## Funds Movement

| Request | SLA | Required fields |
| --- | --- | --- |
| Account funds transfer | 5 days | From and to account names and IDs, amount, whether it is cross-currency, authorization form |
| Cost reversal for fraud | 5 days | Advertiser, partner, IRFRAUD ticket, authorization form |
| Balance refund | 5 days | Available balance, upcoming costs, bank confirmation, authorization form |
| Balance forfeiture | 5 days | Contracts, currency, balances, authorization form |

Approval: any transfer needs the approval level in the SKILL.md authority table. The requester needs permission D54 and 2FA.

## Confirmations

| Request | SLA | Required fields |
| --- | --- | --- |
| Bank account verification | 5 days | Required fields per the CHS form |
| Vendor registration | 5 days | Order form, vendor form, signature needed |
| Partner proof of agreement | 5 days | Required fields per the CHS form |
| Audit review | 5 days | SOA in Excel, and whether it was sent |

## Delinquency

| Request | SLA | Required fields |
| --- | --- | --- |
| Suspension override | 3 days | Overdue balance, days overdue, reason, related ticket |
| Overdue payments review | 5 days | Overdue balance, fee type, 12 months of deposit confirmations |

## Credit Request

| Request | SLA | Required fields |
| --- | --- | --- |
| SLA credit | 5 days | Order form, credit value, calculation, related ticket |
| Goodwill credit | 5 days | Credit value, calculation, related ticket |

## Routing notes

- Balance on a closing account: BC creates a GCH ticket with issue type "Account closure". Use the account-closure reference, not this table.
- Partner payout timing questions are not a CHS request. Check the payout schedule in SKILL.md.
- A request that asks GCH to decide whether a fee can be written off goes through the closure reference's approval rule.

## GCH reference facts

- Dormancy fee: $10 USD per month (direct) or £25 GBP per month (reseller). Assessed around the 10th. Non-refundable.
- Partner payouts: Tuesday and Thursday at 09:00 SAST for threshold partners. 1st and 15th for fixed-day partners.
- Coverage: offline on impact.com global and South African public holidays. Limited on US and UK bank holidays.

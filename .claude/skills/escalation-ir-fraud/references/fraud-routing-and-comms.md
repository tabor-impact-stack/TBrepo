# Fraud and compliance routing, communications, and canned responses

Sources: Customer Solutions and Compliance processes (CECS, 4464738332); Fraud Communication Process (3015868462); Brand Fraud Investigation and Escalation Guide (GlobalOpsPortal, 6419775501); Operational Gap Analysis: TS vs IRFRAUD (CETS, 6633488425, draft); KYB/KYC Organised Fraud SOP page (6648823819, draft SOPs).

## QTP flag to queue

| QTP flag | Queue | Action |
| --- | --- | --- |
| COMPLIANCE_FLAGGED_INTERNAL | Compliance | Route to Compliance |
| FRAUD_INVESTIGATION_INTERNAL | Compliance | Route to Compliance |
| PROMO_WUP_REQUIRED | Compliance | Route to Compliance |
| CONFIRMED_FRAUD_INTERNAL (malformed tracking link) | Fraud | Route to Fraud |
| REPORTED_FRAUD_BANK_DETAILS_CHANGE (unauthorized bank change) | Fraud | Canned response, then Fraud |
| NEW_PAYEE_REVIEW, IDV_CHECK_REVIEW_INTERNAL, AML_CHECK_REVIEW_INTERNAL | Payment review | If changed in the last two business days, tell the partner to wait. If older, raise in the compliance channel. |

## Scenario routing

| Scenario | Queue and action |
| --- | --- |
| User email changed with no access to the old address | Compliance group. Send the COMP email-change response (confirm the exact title in the library). |
| User flagged as suspicious | Compliance group. Send "Account Locked due to Fraud". |
| 2FA method change | Troubleshoot first. If fraud must be involved, send the COMP 2FA response (confirm the exact title in the library) and move to the Fraud group. |
| Media partner account closure | Compliance group. |
| Marketplace application pending | Keep the ticket. Send the COMP Pending response (confirm the exact title in the library). |
| Partner deactivated for fraud | Send "Account Locked due to Fraud". Move to the Fraud group. |
| Brand reporting a suspicious partner | Send "Reporting Fraud/Compliance Investigation". Keep the ticket open. |
| Clawback from a fraudulent partner | Send "Reporting Fraud/Compliance Investigation". Move to the Fraud group. Use the clawback reference in `escalation-bc`. |

## Fraud communication process

- Fraud can start from a compliance discovery, an advertiser chat with support, a UI report, or an email to the CSM.
- The Freshdesk ticket subject includes "Fraud" for an internal source. Include any publisher or advertiser IDs. Assign to the Fraud group.
- Support or the CSM creates a linked Compliance or Fraud Jira ticket, depending on the brand's priority.
- Compliance handles all advertiser communication in Freshdesk. Templates: SUSPICIOUS ACTIVITY or POTENTIAL FRAUD for a concern, a no-fraud closure, and a verified-fraud notice to affected advertisers.
- Confirmed fraud: identify affected advertisers, check with the CSM before contacting other brands, then notify.
- Keep correspondence limited on suspected partners, so fraud practices aren't disclosed.

## Brand fraud investigation (brand-side)

Pattern: a brand account is funded with stolen cards, value is routed to partners as bonus or make-good payments, then cashed out. Treat it as a money-laundering risk.

Behavioral red flags:
- Throwaway identities
- Rapid multiple card deposits
- Bonus-heavy payouts with no campaign activity
- Shared devices or IP addresses between brand and partner
- Fast deposit-to-withdrawal timelines

Investigation steps:
1. Review the funding timeline in Operator.
2. Review the receiving partners: identity quality, login risk score, shared IP or device.
3. Coordinate with Finance or payment risk on chargebacks.
4. Expand to the wider ring, if the pattern repeats.

Outcome: log brand concerns on BC-41901 and partner concerns on IRFRAUD-11052. Don't open a separate IRFRAUD ticket. Record the brand details in the tracking sheet. Name the designated closure owner on the ticket.

## Organised fraud on upgrades (draft SOP)

The draft SOP for Starter-to-Essentials upgrades requires these checks before an upgrade is executed:
1. Ticket intake: log in the PLG Operations project, and capture the customer's explicit business reason. Don't assign an account executive until the checks clear.
2. Internal checks: flag accounts that try to upgrade within seven days of signup. Confirm real usage and transaction volume. Flag a marketplace delisting marked "Do Not List in Marketplace".
3. Digital footprint: confirm the website and domain are legitimate and that the IP location matches the declared business location.
4. KYB scoring and escalation to Compliance for borderline or high-risk cases. No single signal blocks an upgrade on its own.
5. Only after clearance does Sales execute the upgrade.

The draft is not approved. Note this in any ticket that relies on it.

## Canned responses for this skill

Use the exact library title, and retrieve the text with `canned-response-lookup`. Some titles below are confirmed from the sources. Others are described by topic only, so confirm the exact title before sending.

Confirmed from sources:
- Account Locked due to Fraud (COMP)
- Reporting Fraud/Compliance Investigation (COMP)
- (COMP VERIFF) NAME MISMATCH
- (COMP VERIFF) DOCUMENT FAILED, RETRY NEEDED

Described by topic only (confirm the exact title):
- Email change response (COMP), for a user changing email with no access
- 2FA response (COMP), for a 2FA method change
- Pending response (COMP), for a marketplace application pending

## Open process questions

- Compliance and Fraud queues are separate. The source doesn't define a third queue for payment review. Confirm which group handles payment-review QTP flags.
- The Operational Gap Analysis is a draft RFC from June 2026. It proposes that TS owns the technical data pull, Fraud owns the final policy action, and a shared checklist covers reconciliation. It isn't approved, so don't treat it as the current process.
- The nationality-based pattern in the Veriff decline reasons ("identity farming" flag) is excluded from this skill. The flag is tied to nationality-linked device settings and is not used as a signal.
- The AML section of the Veriff guide has an unfilled placeholder for the PEP and sanctions policy. Route AML matches to Compliance until the policy is written.
- The draft Starter-to-Essentials upgrade SOP (KYB/KYC page) is unapproved. Don't cite it as policy. Use it only as context for upgrade-related fraud cases.

# BC ticket types and required fields

Sources: Account Closure & Deactivation Process (CS, 1916534931); Starter Edition Account Closure (CECS, 5743837185); CSol: BC Ticket Process for Add-On Subscription Cancellations (CECS, 6457491463); Brand Fraud Investigation and Escalation Guide (GlobalOpsPortal, 6419775501); Clawback Policy: Publishers (GlobalOpsPortal, 4219338812).

## Work types

| Work type | Used for | Summary format |
| --- | --- | --- |
| Account Deactivate and Close | Closing a full account after billing stop and completeness check | Account closure, [Brand Name], [Operator ID] |
| Billing Engine Change (billing stop) | Stopping billing before a closure, or mid-term termination | Billing stop, [Brand Name], [Operator ID] |
| (Epic) PLG Deactivation | Starter Self Managed (PLG) cancellation requests | Customer Cancellation Request [Brand Name] [Brand ID] |
| Billing Engine Change, Add-On Product | Cancelling an add-on such as Optimize or Paid Search Monitoring | Customer Cancellation Request Add-On Product: [Paid Search Monitoring or Optimize] |
| Collections | Overdue fees at 90 days or more, or a contract buyout | Collections, [Brand Name], [Operator ID] |
| Reactivation | A deactivated non-payer wants to reactivate and fund the account | Reactivation request, [Brand Name], [Operator ID] |
| Brand fraud concern | A brand reports a concern about its own account | Logged on the existing BC concern ticket (BC-41901 for brand concerns) |

Use the summary format in the reference when a team has no approved summary. Don't invent a work type.

## Required fields by work type

### Account Deactivate and Close
- Operator ID (required)
- Program closure date
- Billing stop ticket reference
- Churn reason code from Salesforce, confirmed by the RM
- Salesforce URL
- Balance check result (zero, or positive or negative with the amount)
- For a parent account with child accounts: the parent account ID, and a note that BC closes the group

### Billing Engine Change (billing stop)
- Operator ID (required)
- Salesforce URL (required)
- Billing engine option: Mid-Term Termination or Billing Stop
- Requested date
- Region
- Agency-related accounts don't need their own billing stop ticket

### PLG Deactivation (Starter)
- Screenshot of the customer's cancellation request, with a visible timestamp
- Refund required: Yes or No
- Locked-action waiting period: the locking date of the latest pending action, if any
- Requested closure date: ASAP, unless the advertiser gave a date
- Operator ID (advertiser account ID)
- Billing engine option: Mid-Term Termination or Billing Stop
- Related product: Performance
- Salesforce opportunity URL
- Region
- Request type: Credit Request, sub-type Subscription Service Fees (SaaS or Professional Services)
- Cancellation reason (one of the 15 below)

Starter cancellation reasons: Advertiser Tech Product Issues, Agency Issues, Business Challenges, Combine Service and Technology, Contract Type Change, Customer Profile Issue, Fraud, Impact Support or Management, Lack of Productive Partnerships, Lack of Resources, Nonpayer, Bankruptcy, Pricing, Lack of Features or Software Did Not Meet Expectations, Software Issues.

### Add-On Product cancellation (US Self-Serve or Essentials with no CSM)
- Add-ons inherit the brand's subscription end date. A mid-subscription cancellation request counts as the notice date. Billing stops in the following billing cycle. No refund or credit applies if the add-on is unused.
- Summary: Customer Cancellation Request Add-On Product: [Paid Search Monitoring or Optimize]
- Description: timestamped screenshot of the request, confirmation the customer was told the cancellation period, requested date
- Operator ID (advertiser account ID)
- Billing engine option: Add-On Product
- Related product: PC
- Salesforce Opportunity URL
- Region
- Close the Freshdesk ticket only after BC confirms billing is updated.

### Collections
- Operator ID
- Overdue balance and days overdue
- Contract details and renewal date
- Settlement status and any arrangement
- CSM reference

### Reactivation
- Operator ID
- Account status in Operator. A Closed account can't be reactivated. It needs a new contract and onboarding.
- Reason the account was deactivated and what has been paid

## Notice and renewal rules (for closure tickets)

- Non-renewal notice must be at least 30 days before the renewal date.
- Notice doesn't end the advertiser's obligation to pay fees until the contract end date.
- Program closure date is the advertiser's preferred date to end partner contracts and tracking.
- Subscription end date and billing frequency are in Operator under Finance, Subscription Details.

## Brand fraud concerns

The Brand Fraud guide sets these rules for brand-side incidents:
- Log brand concerns on BC-41901.
- Log partner concerns on IRFRAUD-11052.
- Don't open a separate IRFRAUD ticket for a brand account.
- Record the brand details in the tracking sheet.
- Name the designated closure owner on the ticket so they can close the brand account.

Don't copy the named-account list or the regional pattern details from the guide into a ticket.

## Clawback (partner funds)

The Clawback Policy for publishers allows funds to be reclaimed when the publisher's account still holds them. Grounds for clawback without a brand form include: illegal activity, misrepresentation of self, false ownership claims, links to known fraudsters, bot usage, use of stolen credit cards by the paying brand, blatant copyright infringement, and use of PayPal accounts linked to fraud rings.

Clawback approval levels:
- Level 1: approved by the Fraud and Compliance approvers.
- Level 2: clawback amounts from $10,000 to $49,999, approved by the Fraud and Compliance policy owner.
- Level 3: amounts above $49,999, approved by the Strategic Operation Marketplace Governance approvers.

The policy lists nine grounds. The ninth ground, lead fraud from a specific country, is based on nationality, so it is not included here. The policy owners should review it.

Process: the fraud and compliance team detects and investigates through an IRFRAUD ticket. Publishers are notified through Freshdesk with limited correspondence. A GCH clawback form is created for approved clawbacks, with the policy link and the infringement reason in the ticket.

Don't draft clawback decisions yourself. Route them to the fraud or compliance skill.

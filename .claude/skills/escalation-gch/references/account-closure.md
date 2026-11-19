# Account closure and deactivation

Sources: Account Closure & Deactivation Process (CS, 1916534931); Starter Edition Account Closure (CECS, 5743837185); US Self-Serve Account Closure (CECS, 4324589569); Account Closure Process, US Entry, EMEA and APAC (CECS, 4324393093).

## Which page applies

| Account type | Process |
| --- | --- |
| Starter Self Managed (PLG) | Starter Edition closure (5743837185) |
| US Self-Serve | US Self-Serve closure (4324589569). Creator and Advocate have extra steps. |
| US Entry (2.5K MRR) and above, EMEA, APAC | Master process (1916534931) and Entry, EMEA, APAC page (4324393093) |

## Who does what

- Advertiser: must submit a closure request through a Need Help ticket. This is the only valid form of notice.
- CSM or RM: tries to save the account. Cannot submit the request for the advertiser.
- Customer Solutions: confirms notice, sends canned responses, runs program closure steps in Operator or the UI, and resolves the ticket. Operational closure is now automated by BC. The older Customer Solutions steps are outdated.
- RM: submits a Billing Engine Change ticket for billing stop, then the Account Deactivate and Close BC ticket. Chooses the churn reason code in Salesforce.
- BC: completeness check, then deactivation in Operator. Converts to a GCH ticket when a balance exists.
- GCH: confirms zero partner and SaaS balances, then hands back to BC.
- Revenue team: client comms after confirmed closure.

## Key terms

- Non-renewal: the advertiser will not renew. Service ends at the subscription end date.
- Notice: the contractual notice to not renew, due 30 or more days before the renewal date.
- Subscription obligation: notice does not end the obligation. The advertiser still owes fees until the contract end date.
- Program closure date: the advertiser's preferred date to end partner contracts and tracking.

## Step 1: Confirm the request

1. The request must come through Need Help. If the CSM or RM sent it, ask the advertiser to submit it through Need Help.
2. Check account type. Starter (PLG) goes to the Starter page.
3. Check onboarding. If still onboarding, send "Still in Onboarding" and assign to the Onboarding Manager. Find the Onboarding Manager under Account Team in Operator.

## Step 2: Check notice timing

Compare the ticket creation date with the renewal date. Find the renewal date in Operator under Finance, Subscription Details, Subscription End Date, or in the advertiser's Subscription Period.

- Less than 30 days: the advertiser does not have the right to cancel the renewal. Send "(Annual/Monthly Contract Still in Place) less than 30 days notice". If there is no pushback, resolve.
  - Pushback about campaign strategy or resources: send "Best Practices and Strategy Resources for Brands", and tag the CSM in an internal note.
  - Pushback about issues: troubleshoot. Resolve once the issue is handled.
  - Continued pushback: tell the advertiser the request goes to the CSM. Internal note asks the CSM to check for a contract buyout. Assign the ticket to the CSM.
- More than 30 days: the notice is valid. Send "Non-renewal with sufficient notice: more than 30 days from renewal date". Internal note: the advertiser is within rights to non-renew, and the CSM should try to save the account. If it cannot be saved, get the BC Jira ticket from the CSM, or ask the RM to create one. Assign the ticket to the CSM.

Billing frequency and subscription fee are in Operator under Finance, Subscription Details. Check both before sending the canned response.

## Step 3: Take closure steps (after the BC ticket exists)

1. CSM reassigns the Freshdesk ticket to Customer Solutions once the BC ticket exists.
2. Confirm the program closure date with the advertiser. If it is not confirmed, ask for it.
3. Send "Program Closure Notice".
4. Run the steps below, keeping the program closure date in mind.
5. Send "Final Program Closure Confirmation", then resolve.
6. Payment or fee questions go to BC.

### Program closure steps (Live advertiser account)

1. Expire all active partner contracts: Partners, select all out-of-office items, Contract, Expire. Set the expiration date to the program closure date. Toggle Withdraw All Switches. Use this comment: "This message is to inform you that we (impact.com) are closing down this account on behalf of the advertiser as they are no longer an impact.com customer as of {date}. Should you have any questions, please reach out to your point of contact at {brand name}." Expiry takes 30 to 45 seconds to register.
2. Reject all pending partner applications: Partners, Applications, select all, Reject, reason Other, specify "Program closure". Scroll to the bottom if there are more than 25.
3. Withdraw all proposals sent: Partners, Proposals Sent, select all, Withdraw.
4. Delete application workflows: Partners, Workflows. Turn off Impact AI application processing under Settings.
5. Delete catalogs: Content, Products, Product Catalogs. Deactivate, then delete.
6. Remove from marketplace: in Operator, on the Campaign page (not the Advertiser page), Basic Settings, tick "Do Not List in Marketplace", save.
7. Repeat for every campaign, including Creator campaigns.

If the advertiser wants to close a single campaign or program rather than the whole account, use the campaign closure guide (CECS, 3749873378) instead.

## Account Deactivate and Close (BC)

- RM submits a Billing Engine Change ticket to BC first, with the Operator ID and Salesforce URL. Agency-related accounts do not need their own billing stop.
- After the CC&R report shows billing has stopped, Business Operations marks the account Churned in Salesforce. The RM then chooses a confirmed churn reason code.
- Stand-alone products: Mediarails follows the decommission process. Activate's CSM ends the subscription in the Activate admin portal and notes the termination in Bill.com.
- After the billing stop ticket is complete, the RM (or CSM in EMEA and APAC) creates the BC "Account Deactivate & Close" ticket. One per account. For a parent with child accounts, file one ticket for the parent. Operator ID is required.

## BC completeness check

- Billing engine is stopped.
- SaaS balances are accounted for, including reserves.
- Final settlement outreach has been made, or write-off approval has been obtained under the finance approval matrix.

Then:
- Zero balance: BC deactivates in Operator.
- Any balance, positive or negative: BC converts the ticket to a GCH ticket with issue type "Account closure". The GCH ticket states what is owed or payable and any actions for GCH. BC deactivates after GCH review.
- Technical blockers to closure: escalate to Product Finance. Example: IRFIN-4355.

## GCH review of a closing account

- Partner fee balance from $0 to $1,000: can move to closing with no approval.
- Overdue or upcoming partner fee balance above $1,000: needs written write-off approval from the named approver before closure. Use the role "fee write-off approver" in drafts. Do not name the person.

## Non-payers

- At 60 days overdue: CSM marks the account churn risk in Salesforce.
- At 90 days: CSM creates a BC ticket for collections.
- At 180 days overdue: the account is fully deactivated.
- No settlement: the account closes at renewal.
- Settlement reached: BC runs the closure steps above.

## Reactivation

- Non-payer deactivation: the advertiser needs a BC ticket for case-by-case review. Reactivation depends on the account status in internal systems.
- A Closed account in Operator cannot be reactivated. It needs a new contract and a new onboarding.

## Bankruptcy (Legal guidance)

- Customer Solutions cannot terminate a contract early because of bankruptcy, unless the brand asks us to. Trustees can keep the contract running.
- Amounts owed before the filing cannot be billed.
- On first outreach, ask the brand for its bankruptcy details and documents.
- Do not reverse transactions. Place them on NQTP. The data is still needed, even if the transactions are later reversed out of the system.

## Starter Edition closure (5743837185)

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

## Feedback and changes to these pages

File a CO Jira and assign it to the page owner. The older CEE Jira is no longer used.

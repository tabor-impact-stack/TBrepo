---
name: "mp-change-request"
description: "Assesses Media Partner profile change requests for impact.com Customer Solutions specialists, covering billing address, corporate address, company name, and website changes. Use this whenever a media partner or creator asks to change their billing address, business address, company or legal name, or website or domain, or a specialist asks to assess, check, or approve one of these changes, or says \"rmpc\" or \"change request\". Checks for account takeover, tax status changes, and mismatched registry or domain details, then returns one recommended action with the reasons and the next ticket step. It never approves a change itself and never writes a customer reply or Agent Notes. For payment holds, tracking, API bugs, or QTP investigations, use the other skills instead."
---

# Media Partner Change Requests

You're helping a Customer Solutions specialist decide what to do with a media partner's request to change a sensitive profile field. Treat each request as a possible account takeover or fraud attempt until the evidence says otherwise. Banking, registration, and domain fields can be used to hide bad actors, tax status changes, and account takeovers.

You assess and recommend. The specialist makes the change, sends any request, and resolves the ticket.

## Scope

Four categories only:
- Billing address
- Corporate address
- Company name
- Website

For anything else, reply with this one line and stop: "This request is outside the change-request assessment. Use the matching skill for this topic." Don't assess payment processing, tracking issues, API bugs, or QTP investigations here.

## Output

Plain text only. No code blocks, no backticks, no bold, no bare URLs, no introduction or closing remarks. Start with the header and stop after NEXT STEP. Labels are ALL CAPS. Use these lines, in this order:

MP CHANGE REQUEST ASSESSMENT
CHANGE CATEGORY: Billing Address, Corporate Address, Company Name, or Website
REQUESTED UPDATE: old value to new value
BUSINESS REGISTRY MATCH: Verified, Unverified, or Pending search
DOMAIN OR WEBSITE OWNERSHIP: Passed, Failed, or Suspicious
GEOLOCATION AND IP CONSISTENCY: Passed, Flagged, or Inconclusive
MISSING PREREQUISITES: the missing data needed to resolve the request, or None
RECOMMENDED ACTION: APPROVE, DECLINE, ESCALATE, or REQUEST INFO
REASONS: the specific checks that drove the recommendation, in one to three short lines
NEXT STEP: one concrete step, for example "Request incorporation certificate" or "Approve change on backend"

Use "Not applicable" for any check that doesn't apply to the category. For example, the website check doesn't apply to a billing address change.

## Step 1: Gather the inputs

Needed for every request: the change category, the old and new values, the partner's account ID, and the partner's official website. If any of these are missing, list them under missing prerequisites and recommend REQUEST INFO.

If the specialist has already provided verified documents, such as a registry screenshot, a government ID, or domain verification logs, use them directly and skip the lookup in Step 3.

## Step 2: Run the category checklist

### Billing address

- Compare the requested billing country with the entity's tax residency, its bank payout country, and its recent login history.
- Review login logs for VPN, proxy, or suspicious geolocation mismatches, especially from high-risk locations.
- Approve if the countries align and the IP logs match.
- Request info if the new address is unverified. Ask for a W-9 or W-8BEN-E, or proof of address.
- Escalate to FinTech or Compliance if a high-risk transition is flagged.

### Corporate address

- Confirm the entity is registered in the destination country or state through an official business registry lookup.
- Approve if the registry match is confirmed and the trading model hasn't changed.
- Request info if the registry result is inconclusive. Ask for an official incorporation certificate.
- Escalate to Tax or Legal if the change affects US tax status.

### Company name

- Confirm the ownership continues from the old legal entity to the new name, using business register filings.
- Approve if the rebrand is verified and ownership is continuous.
- Request info if it's unverified. Ask for a Certificate of Name Change or a legal amendment.
- Decline and direct the partner to create a new account if the change is a full legal entity transfer, such as an acquisition without common ownership.

### Website

- Confirm domain ownership. Check whether the requested URL matches an existing verified media property on the partner profile, or the company email domain.
- Approve if the site matches a verified media property or the email domain.
- Request info if ownership doesn't resolve automatically. Send the verification prompt.

## Step 3: Verification lookup

Run at most one search, and only when the verification isn't already in the ticket. Use the official business registry or the domain check that fits the category.

If the one search is inconclusive, don't run another. Recommend REQUEST INFO and ask the partner for official documents.

## Step 4: Choose the action

- APPROVE: the category's approval condition is met and no risk flag is raised.
- REQUEST INFO: a required document or verification is missing or inconclusive.
- ESCALATE: a high-risk transition or a tax or legal impact is flagged.
- DECLINE: only the company name entity-transfer case, which goes to a new account.

If a risk signal and an approval condition both apply, choose ESCALATE. Don't approve through a conflict.

## Hard limits

- Don't tell the partner a change is approved from this assessment. The specialist makes the change on the backend and then confirms it to the partner.
- Don't assess an advocate's change. Advocates have no platform login, so use the advocate skill.
- Don't mention internal risk signals, fraud attributes, or QTP rule names in anything the specialist might paste to the customer.
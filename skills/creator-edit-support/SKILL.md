---
name: "creator-edit-support"
description: "Gives impact.com Customer Solutions specialists the brand rules, architecture, login destinations, and terminology for white-labeled Creator Edit programs and the Walmart Creator program. Use this whenever a ticket mentions Walmart Creator, Target Storefront, Meta creator, Airbnb, Sam's Club, Best Buy, CVS, Home Depot, Nordstrom, Fanatics, Amazon Music, or another branded creator program, or when a specialist asks where a creator should log in, which brand terms to use, or whether impact.com can be mentioned. Produces a brand brief for the specialist. It never writes the customer reply or the Agent Notes; use impact-customer-response and impact-agent-notes for those."
---

# Creator Edit Support

You're helping a Customer Solutions specialist handle a ticket from a creator on a branded or white-labeled program. Your job is to identify the program, state its architecture, say where the creator should log in, and list the terms and restrictions that apply. The specialist then uses that brief when writing the reply.

You don't write customer drafts, sign-offs, or Agent Notes. Those belong to `impact-customer-response` and `impact-agent-notes`. Pass the brief to them.

## Output

A plain-text brand brief in the layout below. No code blocks, no backticks, no bold, no bare URLs. Use the anchor-text link form `[Exact Title](URL)` for any link. Start with the header line and stop after SOURCES. Labels are ALL CAPS, and skill-specific fields come before SOURCES. Omit any field that doesn't apply. No introduction or closing remarks.

CREATOR EDIT BRIEF | [Brand or program name]
ARCHITECTURE: [Walmart Creator (legacy native Media Partner UI) | Modern white-labeled portal]
IMPACT.COM MENTION: [Permitted | Suppressed, except for IDV and tax]
STANDARD DASHBOARD LOGIN: [app.impact.com | brand portal URL]
IDV, TAX, AND BANKING LOGIN: [app.impact.com or impact.com, fixed, do not change]
COMPLIANCE ROUTING: [Which site the creator signs into for which task]
CREATOR STATUS AND CONSTRAINTS: [Brand-specific rules, onboarding requirements, IDV constraints, payout terms]
TECHNICAL AND INTEGRATION NOTES: [Settings, API or OAuth constraints, tracking notes, known issues]
REQUIRED TERMINOLOGY: [Terms to use]
PROHIBITED TERMINOLOGY: [Terms and paths not to cite]
REQUIRED SIGN-OFF: [Sign-off style, or "Use standard support sign-off"]
SOURCES: [Exact Confluence page titles used, or "No brand-specific SOP found for [brand or topic]"]

## Step 1: Identify the program

Find the brand or program name in the ticket. If the brand isn't clear, ask the specialist for the brand name, creator account ID, or the exact question. Don't guess.

Check the Walmart Creator exception first. Walmart Creator is the pioneer program. It doesn't use the modern white-labeled portal.

## Step 2: Choose the architecture

- Walmart Creator: conflicting. This skill used to say it runs in the native Media Partner interface. The Creator Edit white-labeled page (Confluence 6466174985, September 2026) says Walmart no longer runs through Creator, has its own domain and portal, and uses Impact for payments only. Confirm the architecture with the team before naming a login or portal.
- Modern white-labeled programs (Target Storefront and others): the brand's own portal. Only IDV and tax workflows point to impact.com.

## Step 3: Set the login destinations

- Walmart Creator: unconfirmed. The Creator Edit page says platform issues go to Walmart's own platform support, and payment queries follow the standard Performance QTP process. Don't name a login destination until the team confirms it.
- Modern white-labeled programs: everyday dashboard actions go to the brand portal. Only IDV and tax workflows go to app.impact.com or impact.com. Keep that destination fixed. Don't override it.
- IDV and payouts, for all creators: direct the creator to app.impact.com and the "Verify Your Identity" banner on the Home dashboard.

## Step 4: Apply the terminology rules

Walmart Creator:
- Refer to the program as "Walmart Creator." Mentioning impact.com is allowed.
- Sign-off: "Best, [First Name]" then "Walmart Creator Support Team." The Creator Edit page doesn't confirm this sign-off, so flag it to the team before relying on it.
- Never cite Settings > Technical > Unsubscribed Outreach Emails for a creator or media partner. Creators don't have advertiser-level settings.
- For brand newsletters, point the creator to their newsletter or communication settings, or to the help article "Unsubscribe from a Brand's Newsletter."

Modern white-labeled programs:
- Remove every mention of impact.com, except IDV and tax workflows.
- Use the brand's own terms, such as "Creator," and the brand's sign-off. If the brand's sign-off isn't in these rules, say so in the brief. Don't invent one.

For every creator on any program:
- Unsubscribing from brand marketing emails doesn't cancel the account or block transactional notices. Those include IDV confirmations, tax reviews, and payout notices.

## Step 5: Look up brand-specific rules

If the brief needs a brand rule beyond what's here, check the mapped Confluence page in `references/brand-sources.md`. Run one targeted search on that page only. Don't download or dump full pages. Extract only the rule or constraint the ticket needs.

If the page doesn't contain the rule, write "No brand-specific SOP found for [Brand/Topic]" in the brief. Don't assume an answer.

## Brand-specific notes

- Walmart Creator: the exception described above. Architecture is native Media Partner UI.
- Target Storefront: modern white-labeled portal. See the Target Storefront migration and OAuth linking pages in `references/brand-sources.md` for setup and linking rules.
- Meta: the Meta Creator Edit one-pager and Meta Payments mini-portal page are the references. Check the payments page for payout questions.
- Airbnb: payment block questions are covered in the Airbnb Payment Blocks one-pager. The rules don't say more, so check it before answering. The Creator Edit page adds that Airbnb tickets must be answered in the language the ticket was raised in.
- Eligibility requirements from the Creator Edit page, for creator questions about why they can't join: CVS needs at least 2,000 followers and a US location or US audience of over 50%. The Home Depot needs a US location and at least 10,000 followers. Best Buy needs one connected social media account, with no follower minimum. Fanatics needs at least 500 followers and a public account.
- Other brands: use the mapping in `references/brand-sources.md`. If none matches, ask the specialist.

## Escalation routes

From the Creator Edit white-labeled page (Confluence 6466174985):
- Finance queries: Slack #financeoperations.
- Compliance and IDV: follow the Veriff IDV process, with the verification banner on the platform. For an expired session or a Veriff link that shows an expired session error, post in Slack #Compliance and ask for a temporary link.
- Account closure: create an IPR ticket, tag the Freshdesk ticket, and put it in the WOD queue. Wait for the closure confirmation before resolving.
- Technical: use the CS-TS escalation guide, as for Performance. Put the Creator Edit portal name in the summary. Include the Operator account IDs and the creator's email.
- Creator Edit Slack channels: #creator-edit-general and #global-creator-edit-support.

## When this skill doesn't apply

Advocate programs (referral participants, Function Health, and the APJ advocate brands) use the `advocate-support` skill. Advocates have no platform login at all, so don't mix the two sets of rules.

## Known conflicts

- Walmart Creator: this skill describes the native Media Partner UI with an app.impact.com login. The Creator Edit page says Walmart has its own domain and portal, with Impact handling payments only. Confirm before using the Walmart architecture, login, or terminology.
- Brand list: the Creator Edit page lists Petsmart, Nordstrom, Airbnb, CVS, Best Buy, The Home Depot, Fanatics, and Meta. Target Storefront, Sam's Club, and Amazon Music appear in this skill but not on that page. Check the brand-sources reference before quoting their rules.
- The Walmart sign-off and the impact.com mention rule aren't on the Creator Edit page. Confirm them with the team.
---
name: "slack-team-message"
description: "Drafts a short Slack message from a Customer Solutions specialist to an internal team, such as Finance, Compliance, Technical Services, Integration Engineering, Lightning Pay, Rakuten migration, or Sales. Use when the specialist asks to post, message, ping, or ask a team in Slack, or says \"slack\", \"ask finance\", \"ask compliance\", \"technical services\", \"integration engineering\", \"lightning pay\", or \"post to\". It asks which channel the message is for, uses that channel's intake format, and keeps the message as short as possible. It only drafts and never posts."
---

# Slack team message

You're helping a Customer Solutions specialist ask an internal team a question in Slack. Long messages go unanswered, so the message must be short and easy to scan. The specialist posts it. You only draft.

## Step 1: Find the channel

If the specialist hasn't named the channel, ask one question: "Which channel is this going to?" Then list the channels below in one line each, so they can pick. Don't draft until the channel is known.

If the request is a technical bug, an API error, a tracking failure, or anything that needs engineering investigation, don't draft a Slack post. Send it to Technical Services through a TS ticket, as described below, and use the escalation-ts skill for the write-up.

## Known channels and intake formats

- #technical-services: the topic sets two routes. A quick technical question goes to the person named in the channel topic, so ask the specialist for that name if you don't have it. Anything that needs further investigation goes to a TS ticket at tshelp.impact.com, following the Tech Issues Escalation Playbook. Don't post an investigation in the channel.
- #ask-finance: use the General Question form. The form fields are Account Name, Account Id, Category, and Question. Use the category that fits, such as Payment/Deposit, Tax, or Vendor Portal Requests. This channel isn't for escalations. Complex issues need a Jira ticket.
- #squad-finance: technical finance questions only. Operational finance questions go to #ask-finance.
- #compliance: a log of IRFRAUD tickets, not a question channel. Compliance needs a Jira request first, so tell the specialist that and stop.
- Compliance Question form: the channel isn't confirmed. Its fields are Issue Type, Account Name and ID, Freshdesk URL, and Issue. If the specialist says this is the channel, use those fields and ask them to confirm the channel name.
- #ask-lightning-pay: the topic says to check the Lightning Pay Internal Help Docs first. If the answer is there, tell the specialist and don't draft a post. Otherwise use the partner ID, the Freshdesk link, and up to three numbered questions.
- #rakuten-migration-support: for questions about Rakuten partner migrations. Use the partner or account ID, the Freshdesk link, and one or two questions. Don't include the full ticket history.
- #integration-engineering: for questions about integrations. Tag the right regional group in the first line: @ie-apac, @ie-emea, @ie-us, or @ie for global. Use the same short format as the other channels.
- #sales: no purpose is set, and the posts are from sales staff about advertiser plans and pricing. Only use it for sales questions, such as an advertiser's upgrade options. Confirm with the specialist that it's the right channel before drafting.
- Other channels the specialist uses, such as #compliance_legal, #freshdesk-support-escalations, #marketplacegovernance, #mediapropertyverification, #client-success-team, #ask-customer-revenue, and #squad-integration-gateway: the intake format isn't confirmed. Say so, and ask the specialist to paste the channel's form or one example post before you draft.

## Step 2: Draft the message

Keep it to these parts, in this order:
1. One line that states the ask.
2. The account name and account ID, on one line.
3. The Freshdesk link, if there is one.
4. Up to three short lines, one question each. Put the question last.

Leave out background, the customer's full wording, and anything the team doesn't need to act. If the message needs more than about 60 words, cut it again. Use the channel's form fields as labels when it has a form.

## Output

Plain text only, with no code block. Bold labels are fine if the channel's form uses them. Return the message alone, with one line above it naming the channel. Don't add notes unless something is unclear, and then add a single FLAG line above the draft, starting with "🚩 FLAG:".

## Hard limits

- Never post to Slack. The specialist posts the message.
- Don't put customer personal data in the message beyond the account name, the account ID, and the Freshdesk link.
- Don't name a team member or contact unless the specialist asks, and only use a name from a channel topic.
---
name: "ask-platform-question"
description: "Reviews a support thread and any attached files (CSV, XLS, PDF, screenshots) and drafts a detailed question for @Ask Platform in Slack, covering confirmations of facts, processes, and platform behavior. Use when the specialist asks to ask Ask Platform, check with platform, confirm a process or product behavior, or says \"ask platform\", \"@Ask Platform\", \"proj-ask-platform\", or \"confirm with platform\". It drafts only and never posts."
---

# Ask Platform question

You're helping a Customer Solutions specialist write a complete question for @Ask Platform. Ask Platform answers from curated libraries, and its answers are only as good as the question. Give it everything it needs in one message so it doesn't have to ask back. The specialist posts the message. You only draft.

This is the one Slack draft where detail is the goal. The short-message rule for team channels doesn't apply here. Keep it complete, but scannable.

## Step 1: Review the thread and the files

- Read the whole Freshdesk thread, or the part the specialist points to. Note the partner or brand, the account ID, the issue, and what has already been tried.
- Read every attached file. Use the file-reading skill for CSV, XLS, and PDF, and the pdf-reading skill for PDFs with tables or scanned pages. For screenshots, read what the screen shows: the error text, the values, the dates, and the status fields.
- Summarize what each file shows in one line. Don't paste raw data into the message unless the question needs one specific row or value.
- Redact anything the platform doesn't need: email addresses, bank details, card numbers, tax IDs, and personal names beyond the partner or brand name. Say that you redacted it.

If a file can't be read, say so in a FLAG line above the draft and continue with what you have.

## Step 2: Decide what to ask

Ask Platform can confirm facts, processes, and product behavior. Good questions are specific and answerable:
- A confirmation: "Does X happen when Y?"
- A process: "What are the steps to Z, and who owns each step?"
- A product behavior: "Is this expected for an account set up like this?"

If the question is really about a customer's specific account data, an error that needs engineering, or a finance or compliance decision, say so in a FLAG line. Those go to another channel or a ticket. Ask Platform isn't the right place for them.

Ask Platform works best with one main question per thread. If the thread raises several separate questions, draft them as numbered items in one message, and add a FLAG line suggesting a second thread if they're unrelated.

## Step 3: Draft the message

Use this order. Label each section in ALL CAPS, using the plain text labels below.

QUESTION: one sentence that states the main question.

CONTEXT: the partner or brand, the account ID, the product area, and what the customer is trying to do. Two to four short lines.

WHAT I'VE CHECKED: what the specialist has already confirmed in Operator, the Confluence docs, or the file data. Include the value or result, not just the fact that you checked. This stops Ask Platform from repeating what's known.

FILES: one line per attached file, with what it shows. Say which parts are redacted.

SPECIFIC QUESTIONS: numbered, one question each, in the order you'd want them answered. Make each one answerable with yes, no, or a short fact where possible.

NEEDED BACK: what the specialist needs in the answer, such as a link to the source, the steps, or a confirmation they can share with the customer. Only include this if it helps.

Write the message in plain text. Use numbered lines for the questions and short sentences elsewhere. Don't use code blocks.

## Step 4: Output

Return the draft alone, with one line above it naming the channel. Use #proj-ask-platform (C0BUVCF3SCC) for platform mechanics and integration logic, unless the specialist names a product channel where Ask Platform is installed. If you're not sure which channel, ask the specialist before drafting.

Add a FLAG line above the draft, starting with "🚩 FLAG:", for anything the specialist needs to check. Examples: a file that couldn't be read, a question that belongs in a ticket or another team's channel, or an answer that Ask Platform may get wrong.

## Checking the answer

Ask Platform answers can be wrong, and the moderators fix them only when someone flags them. Tell the specialist to check the reply against the source of truth before they use it with a customer. If the reply is wrong, they can use the feedback control on the reply. A wrong answer that isn't corrected in the thread will come back on the next similar question.

## Hard limits

- Never post to Slack. The specialist posts the message.
- Don't put customer personal data or payment details in the message. Use the account ID and the partner or brand name.
- Don't tell Ask Platform the answer you want. State the facts and ask the question.
- Don't use this skill for a customer reply. Use generate-response for that.
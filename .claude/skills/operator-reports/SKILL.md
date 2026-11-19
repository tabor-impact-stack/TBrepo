---
name: "operator-reports"
description: "Suggests the right Operator report for an impact.com Customer Solutions ticket and says what to look for in it. Use when a specialist asks which Operator report to run, where to find deposit, QTP, marketplace, migration, tax, statement, media, or partner data in Operator, or when a ticket needs internal data the customer can't see. Internal use only. Claude can't run or view these reports, so it suggests the report and the checks, and the specialist runs it. Never put report names or Operator data in a customer reply."
---

# Operator Reports

Operator is impact.com's internal back-end portal for customer account data. Specialists use its reports to check data the customer can't see. Claude can't open Operator, so it suggests the right report, says what to check in it, and asks the specialist to paste back only the values needed for the analysis.

## Output

Use these ALL-CAPS labels, in this order. Omit any that doesn't apply.

REPORT: the report name as it appears in the Operator menu.
WHY: one line on why this report answers the ticket's question.
WHAT TO CHECK: the specific fields, filters, or values to look at.
ACCESS: "Available to Customer Solutions" or "Check access" if the report isn't in the specialist's menu.
SOURCES: the Confluence or SOP page used, or "Purpose inferred from report name, confirm with the team".
NEXT STEP: one concrete action for the specialist.

## Rules

- Suggest only reports from the catalog below. If no report fits, say so, and don't guess a report.
- Pull only the data the ticket needs. Use the least-access rule.
- Don't copy customer, partner, or watch-list data from a report into a customer reply. Reports are for internal analysis and Agent Notes.
- If a report isn't in the specialist's menu, say it's outside their access, and that access requests go to the IOP board.
- Never name individuals or approvers.
- For finance and deposit reports (Deposit Status Report, Cash Flow History, Advertiser Finance Dashboard), set ACCESS to Check access unless the specialist's menu shows them. The Access Matrix gives those to Customer Success, not Customer Solutions.
- Most reports work for both partners and brands, advertisers, and agencies. Check which kind of account the ticket is about before choosing a report, and note any report that only applies to one side.
- Don't use report names in a customer reply. Customers can't see Operator.

## Operator environments

- Live Operator is for real customer work.
- Demo Operator is for training and reproducing issues with production-like data.
- Staging is for developers and QA. Don't use it for customer tickets.
- Access uses Sign in with Google, from a company laptop with Netscope active.
- Each Operator environment has its own access. Access changes are requested through the IOP board.

## Report catalog: most-used reports

Purpose status: "Confirmed" means the Confluence or SOP pages in this skill describe the report. "Inferred" means the purpose comes from the name only. Confirm inferred purposes with the team before relying on them.

- Advanced Action Listing. Purpose: lists actions for an advertiser or partner. Status: Confirmed as an Operator feature. Owned by the RPT squad. Use for action lookups on a ticket.
- Advertiser Finance Dashboard. Purpose: advertiser balance and finance view. Status: Confirmed by the Operator Report Repository (Confluence 2584379558).
- Advertiser Overview. Purpose: summary of an advertiser account. Status: Confirmed by the Operator Report Repository (Confluence 2584379558).
- Brand Cancellation Check. Purpose: checks cancellation status for a brand, useful for closure tickets. Status: Inferred. Use with the account closure flow in escalation-gch.
- Cash Flow History. Purpose: history of money movement on an account. Status: Confirmed as an advertiser finance report (Finance Reporting, Confluence 612565076, handle adv_cash_flow_recon). ACCESS: Check access, because the Access Matrix gives Customer Solutions no Finance report permission. Check it before a GCH money-movement request.
- Decode Click IDs. Purpose: decodes click IDs for tracking troubleshooting. Status: Confirmed as a customer-support permission. Use it for tracking and postback tickets.
- Deposit Status Report. Purpose: deposit status. Status: Confirmed. ACCESS: Check access, because the Access Matrix gives Deposits to Customer Success, not Customer Solutions. The GCH CHS request for an unallocated deposit needs a screenshot of it, so ask the team lead for a screenshot if the specialist can't open the report.
- Electronic Tax Document Detail. Purpose: tax document details for a partner. Status: Inferred. Check it for W-9 or tax questions.
- Marketplace Appeals. Purpose: marketplace appeal records. Status: Inferred. Related to the Appeal Marketplace Decision step in marketplace-decline-triage.
- Marketplace Decline Reasons. Purpose: marketplace decline data, the Operator Marketplace Decline Report (Report ID 18008) used by marketplace-decline-triage. Status: Confirmed by the report ID (18008) from the Operator link.
- Member Listing. Purpose: list of members on an account. Status: Inferred.
- Partner Overview. Purpose: summary of a partner. Status: Inferred.
- Partner Payment Terms. Purpose: payment terms for a partner. Status: Inferred. Check it before a payout question.
- Publisher QTP Review /13880. Purpose: the Publisher Account QTP Review report. Status: Confirmed by the Veriff reference. Use its All account changes and QTP History sections for name-change and IDV reviews.
- QTP History by Account. Purpose: QTP flag history for an account. Status: Confirmed by the Veriff reference, which uses its QTP History section.
- Rakuten Brand Migration. Purpose: Rakuten brand migration status. Status: Inferred. Check it for the migration tag that decides the (RAD) or (AMGT) prefix.
- Rakuten MP Migration. Purpose: Rakuten media partner migration status. Status: Inferred.
- RTAS Report. Purpose: unknown. Status: To confirm with the team before use.
- Statement of Account. Purpose: account statement. Status: Inferred from the FN guide's Statement of Account references.
- Verify Media Property. Purpose: media property verification. Status: Inferred. Check it for the (RAD) or (AMGT) Media not Verified response.

## Not yet verified

These catalog reports don't appear in any Confluence page read so far, so their purpose is still inferred from the name: Brand Cancellation Check, Electronic Tax Document Detail, Marketplace Appeals, Member Listing, Partner Overview, Partner Payment Terms, RTAS Report, Statement of Account, and Rakuten MP Migration. Confirm them with the team before relying on them.

The Operator Report Repository (Confluence 2584379558, last updated 2023) lists reports that aren't in this catalog, including Customer Billing and Renewal Dashboard, Account Renewals, Annual and Monthly Usage, Annual and Monthly Overage Forensics, and Radius Customer Portal. They are not added here until their purpose and access are confirmed.

## Sources

- Operator overview (Confluence DAG, page 5185306625)
- Operator Report Repository (Confluence 2584379558, last updated 2023)
- Finance Reporting (Confluence BIOP, page 612565076)
- Impact Platform (Operator) (Confluence IITS, page 5844926485)
- Impact Platform (Operator) Access Matrix (Confluence IITS, page 651985442)
- Veriff identity verification reference (in escalation-ir-fraud)
- GCH CHS request types (in escalation-gch)
- Marketplace decline triage (in marketplace-decline-triage)
# Squad routing for TS escalations

Source: TS Ticket Escalation Guide (CETS). Use this table to pick the owning squad, then put the suggested squad in the "Component / Category" line of the Jira blueprint. Don't change the template text.

Before you escalate to any squad's Jira project, the pre-escalation check in SKILL.md must be complete. That includes checking with the squad in its Slack channel.

## Template category to squad

| Template | Likely squad | Jira project | Slack channel | Notes |
| --- | --- | --- | --- | --- |
| 1. Tracking and Attribution | Tracking | TRACK | #squad-tracking | Set the work type to Triage when creating TRACK tickets. Covers click gateway, page load API, conversions API, batch jobs, call tracking, JavaScript tags. |
| 1. Tracking and Attribution (event correlation, identity) | Pathing | PATH | #squad-pathing | Use for event correlation, event repositories, identity service. |
| 1. Tracking and Attribution (fraud or viewability scoring) | Scoring | SCORE | #squad-scoring | Use for scoring and fraud diagnostics. |
| 2. Reporting (report URLs with ?handle= or ?reportID=) | Platform Reporting (RPT) | RPT | #reporting_questions | RPT owns all reports with those URL parameters, except internal requests. |
| 2. Reporting (dashboards, scheduled reports, Partner dashboard) | Data Visualization | VIZ | #squad-visualization | Screen URLs containing "report" are VIZ. Advanced Action Listing is split: RPT owns AAL, VIZ owns the subway chart. |
| 3. Plugins (Shopify, WooCommerce, Magento, and other e-commerce integrations) | Saasler | IMA (Impact Apps) | #impact-saasler-intergration | Salesforce issues go to the Storefront Integrations board (STFI) instead. |
| 3. Plugins (In-App SDK, Amazon sync) | Not confirmed | Not confirmed | Not confirmed | The guide doesn't clearly assign these. Confirm with TS before escalating. |
| 4. PDS (Catalogs) | Product Data | PD20 | #squad-pds | For "Task" work type tickets, flag in #squad-pds because the squad isn't alerted otherwise. |
| 4. PDS (FTP/SFTP catalog sync) | Integration Gateway | IGS | #squad-integration-gateway | Gateway covers SFTP, FTP, and email. Check the Ownership Map for SFTP and FTP servers. |
| 5. Finance (FinCore, TechFee, Payments integrations) | Finance squads | IRFIN | #squad-finance | IRFIN covers FinCore, TechFee, Payments, FinTech, and FinBI. Route money movement to GCH, not here. |
| 6. Contracts, Terms, and Action Processing | Action Processing (AP) | AP | #squad-action-processing, #shared-event-types | Use request type BUG only. Covers contract creation, action processing, postbacks, OID lookup, and shared event types. |
| 7. Campaigns (creator campaign logic) | Creator | CAM | #creator_tech, #ask-creator | Covers tasks, compensation, and product gifting. |
| 7. Campaigns (ads, deals, promo codes) | Offers | OF | Channel TBA | Promo code distribution may belong here. Confirm with TS. |
| 8. API (REST 4xx or 5xx, rate limits, authentication, payloads) | Integration Gateway | IGS | #squad-integration-gateway | Covers API endpoints, Kong gateway, rate limiting, and 400 to 499 authentication errors. Check the Ownership Map for APIs. |
| 9. General | None | None | None | Check the TS channels first, then ask the SME. Don't guess a squad. |
| 10. Logins and Dashboards (brand, partner, or agency login, SSO, 2FA) | Core | CORE | #engineering, add label Top_support_issues | Core covers login auth, SSO, 2FA, roles, navigation, and notifications. |
| 10. Logins and Dashboards (partner login and sign-up) | Onboarding | ON | #onboarding | The guide lists "Partner Login Issues" under Onboarding. Confirm with TS if it's unclear. |
| 10. Dashboards that won't load | Data Visualization | VIZ | #squad-visualization | Partner dashboard is VIZ. |

## Other squads (for reference)

- Security issues: ITSEC. Check internally with the team before escalating.
- Mobile app: APP.
- Creator edit and advocate: SQDEV (Advocate), CAM (Creator).

## Unresolved items

- The guide's SME names are people. The skill should name the squad and channel, not the person, unless you want SME names in notes.
- The guide points to "Labels for ITSE & Escalations" for required labels. That page hasn't been read yet, so labels aren't included.

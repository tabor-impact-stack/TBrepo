# Diagnostic tooling and access scope

All recommendations must stay within Customer Solutions Specialist permissions. If the root cause needs more than these tools allow, escalate to Technical Services (TS). Don't write queries outside these scopes, including raw SQL joins and backend cluster, daemon, or infrastructure host queries.

## Event Repository (ERv2)

- Link: https://er-api.gcp.srv-impact.net/events.html
- Use for: event, click, and conversion postback troubleshooting.
- Permitted filters: Campaign ID, Action Tracker ID, Order ID (`oid`), Customer ID.
- SOP: How to use the Event Repository Troubleshooting Tool (ERv2)

## Loggly

- Link: https://impactradius.loggly.com/search
- Use for: client-side tag and postback error logs.
- Permitted Lucene query patterns:
  - `json.campaign:<campaign_id>`
  - `json.tracker:<action_tracker_id>`
  - `json.oid:"<order_id>"`
  - `json.status:4xx` or `json.status:5xx` for HTTP errors
- Combine filters with AND when you need to narrow results, for example `json.oid:"<order_id>" AND json.status:5xx`.
- SOP: How to use Loggly

## PostHog Replay

- Link: https://us.posthog.com/project/186875/replay/home
- Use for: session replays, to see what the customer actually did on a page.
- Permitted filters: user email (`person`), current URL (`$current_url`, contains), recording date. The default date range is the last 3 days. Widen it if the issue is older.
- SOP: How to use PostHog

## SendGrid

- Link: https://login.sendgrid.com/login/identifier
- Use for: checking whether a platform email was sent and delivered.
- Permitted scope: search the Activity Feed for the exact recipient email. Read the event status: Delivered, Bounced, Dropped, or Spam Report.
- SOP: SendGrid Email Verification

## SauceLabs

- Link: https://app.saucelabs.com/home (organization dashboard, last 7 days)
- Use for: testing whether a tracking tag fires in a specific browser or device. Recommend it when the issue depends on browser or device.

## IPQualityScore

- Link: https://www.ipqualityscore.com/user/enterprise/dashboard
- Use for: fraud and VPN analysis on suspicious logins or change requests. Route fraud findings through the Fraud queue (see `sla-and-routing.md`).

## Escalation ceiling

If the investigation needs backend server shell access, raw database schema changes, or infrastructure tracing, stop. Tell the specialist to escalate to Technical Services (TS) with the TS Escalation workflow, and include the data they've collected so far.

## Official SOPs

- Tools for Troubleshooting
- How to use Loggly
- How to use the Event Repository Troubleshooting Tool (ERv2)
- How to use PostHog
- SendGrid Email Verification

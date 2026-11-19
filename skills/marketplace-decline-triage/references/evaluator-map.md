# Marketplace decline evaluator map

Read this before naming a canned response. Use the (RAD) prefix for Rakuten-migrated partners and (AMGT) for everyone else. Ask the specialist if you don't know which applies.

## Hard fail (no appeal)

| MESSAGE_KEY | Failing evaluator | Outcome | Canned response |
| --- | --- | --- | --- |
| MSG_COUNTRY | HIGH_RISK_COUNTRY, ELEVATED_RISK_COUNTRY | Hard fail | Mplace Appl Rejected (Hard-Fail Country) |
| MSG_GENERIC | High-risk IP, disposable email, terminal URL, offensive text, fraud | Hard fail | Mplace Appl Rejected (Hard-Fail) |
| Any | FRAUD_ATTRIBUTES_EVALUATION | Hard fail. Move the ticket to the Fraud queue. | Mplace Appl Rejected (Hard-Fail) |

## Remediable (appeal possible after partner fixes)

| MESSAGE_KEY | Failing evaluator | Partner action | Canned response |
| --- | --- | --- | --- |
| MSG_MEDIA | MEDIA_PROPERTY_ENHANCEMENT, zero verified media | Add and verify at least one media property | Mplace Appl Rejected (Media not Verified) |
| MSG_MEDIA | MEDIA_PROPERTY_ENHANCEMENT, URL error | Correct the media URL | Mplace Appl Rejected (Media Error) |
| MSG_MEDIA | FOLLOWER_COUNT_THRESHOLD_MET (under 500 non-TikTok, under 100 TikTok) | Add and verify all active media properties | Mplace Appl Rejected (Media General) |
| MSG_MEDIA | URL_RISK (low traffic or reach) | Add and verify all active media properties | Mplace Appl Rejected (Media General) |
| MSG_MEDIA | GEO_RISK (HIGH_RISK_GEO_MISMATCH) | Address the location mismatch | Mplace Appl Rejected (Media Issues) |

Appeals for every remediable case are submitted by the specialist with "Appeal Marketplace Decision" in Operator, not by the partner.

## Inconclusive (manual compliance review)

| Case outcome in Operator Case Management | Canned response |
| --- | --- |
| Approved | Partner: Marketplace Application (Approved), prefixed (ASET) |
| Pending | Partner: Marketplace Application (Pending), prefixed (COMP) |
| Rejected | Use the standard hard-fail response for the partner's prefix |

## Priority rule

If a row contains a hard fail and a remediable fail together, treat it as a hard fail. Don't offer an appeal.

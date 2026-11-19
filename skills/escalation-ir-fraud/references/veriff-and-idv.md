# Veriff identity verification (IDV) handling

Sources: Veriff Response Codes and IDV QTP Violations, Reference (6170214634); Veriff Verification Response Guide (6107235391).

## What triggers IDV

- IDV_CHECK_REQUIRED is not a first-payment gate. It's raised for returning partners (with at least one cleared payment, and not an eBay partner) when they make compliance-relevant changes to withdrawal settings.
- First-time payees go through manual NEW_PAYEE_REVIEW, which also carries IDV_CHECK_REQUIRED.

## Veriff decisions

| Session status | Meaning | Action |
| --- | --- | --- |
| IN_PROGRESS | Partner hasn't finished | Wait |
| SUBMITTED | Veriff is reviewing | Wait |
| FINISHED | Decision received | Read the verification status below |

| Verification status | Meaning | QTP effect |
| --- | --- | --- |
| APPROVED | Passed | Removes IDV_CHECK_REQUIRED_INTERNAL and NAME_CHANGE_CHECK_INTERNAL. May add IDV_CHECK_REVIEW_INTERNAL (name issue) or AML_CHECK_REVIEW_INTERNAL (watch-list match). |
| DECLINED | Failed | Adds IDV_CHECK_FAILED_INTERNAL. |
| RESUBMISSION_REQUESTED | Veriff asked for a new upload | No automatic action. The partner stays blocked until they resubmit. |
| EXPIRED or ABANDONED | Session ended with no decision | No automatic action. The partner stays blocked. |

Silent-failure cohort: partners stuck on IDV_CHECK_REQUIRED after RESUBMISSION_REQUESTED, EXPIRED, or ABANDONED. The system won't clear them on its own. Flag them for ops follow-up, and ask the partner to complete a new session.

## APPROVED with IDV_CHECK_REVIEW_INTERNAL

The system adds this when the name on the document doesn't match the member profile, or the name was changed recently, or the document is from a country on the high-risk list. The country list is in the reference page. Don't use it as a basis for judgment on the person. Review the name and change history.

Steps:
1. If the name is essentially the same (spelling, accents, nicknames), approve for payment.
2. If the name doesn't match, look for a verifiable link between the person submitting the ID and the company. If you find one, approve. If not, send "(COMP VERIFF) NAME MISMATCH", remove IDV_CHECK_REVIEW_INTERNAL, and re-add IDV_CHECK_REQUIRED.
3. Check for a name change in the last 90 days (the Veriff reference rule uses 30 days; confirm the window before relying on it), using the Publisher Account QTP Review report, "All account changes" and "QTP History" sections.
   - Possible account takeover or resale: check for other suspicious changes, such as email address changes or logins that don't fit the account's history. Route to Fraud.
   - A name entered wrongly at registration: remove IDV_CHECK_REVIEW_INTERNAL, re-add IDV_CHECK_REQUIRED, and ask the original user to submit ID.
   - A legitimate employment change at a company: ask for a letter of employment from the original user.

## APPROVED with AML_CHECK_REVIEW_INTERNAL

The document passed, but the partner matched a potential PEP or sanctions list.

- Search the lists for the partner's name.
- A match needs more than the name. Confirm with date of birth, a photo, or other identifying details.
- The PEP and sanctions policy section in the reference is incomplete. Route the case to Compliance and don't clear it yourself.

## DECLINED (IDV_CHECK_FAILED_INTERNAL)

| Decline reason | Action |
| --- | --- |
| Duplicated user or duplicated ID (velocity or abuse) | Check whether earlier submissions came from the same account or several accounts. Clear only if the original ID passed and nothing suggests multiple accounts. |
| Attempted deceit, device screen used | Watch the video. If the ID is only a copy saved on a device and not fraud, send "(COMP VERIFF) DOCUMENT FAILED, RETRY NEEDED", remove IDV_CHECK_FAILED_INTERNAL, and add IDV_CHECK_REQUIRED. Check whether an agency submitted the ID for an influencer. |
| Attempted deceit, printout used | Usually fraud. Watch the video first, because a white or glass surface can cause a false positive. |
| Presented document tampered (any variant) | Usually fraud. If in doubt, ask the Veriff team to confirm. |
| Person does not match document photo | Could be fraud, an old ID, or someone submitting on behalf of another person. Review the video. |
| Attempted injection or photos streamed | Treat as fraud. |
| Face match with blocklist | Previously marked as fraudulent. Route to Fraud. |
| Known fraud (Veriff side) | If nothing obvious is found, confirm with Veriff on chat. |
| Suspicious behaviour | Watch the video. If nothing is found, contact Veriff on chat. |
| Resubmission limit exceeded | No further automatic action. |

Don't use any decline reason that refers to a nationality, country of origin, or ethnicity as a fraud signal on its own. The "identity farming" decline flag is excluded from this skill for that reason.

If a decline reason seems wrong, contact Veriff through live chat. If it's confirmed as a false positive, the account may be cleared.

## RESUBMISSION_REQUESTED

Quality problems: blurry or obscured images, the document not fully visible or the wrong side captured, a missing selfie or incomplete liveness steps, or a document not in Roman or English characters. Ask the partner to retry. No Impact involvement is normally needed.

## Canned responses

- (COMP VERIFF) NAME MISMATCH
- (COMP VERIFF) DOCUMENT FAILED, RETRY NEEDED

Retrieve the text with `canned-response-lookup`.

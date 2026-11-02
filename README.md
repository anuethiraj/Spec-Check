# Spec Check

Spec Check helps a business analyst take a requirement from a rough draft to "ready for engineering" before handing it to an engineering team in another time zone.

## Who it's for
Business analysts and product owners who write requirements and acceptance criteria for engineering and QA.

## What it does
1. Lists requirements with their module, requesting association, members affected, status and clarity score.
2. Runs 7 base checks on each requirement, plus 1 rule for its module once a module is chosen. New requirements start with no module, so no module rule is applied until one is picked.
3. Underlines vague words in the requirement as written.
4. Shows a clarity score, the score before and after each re-check, and the number of likely questions from engineering.
5. Lets the user ignore a flag with a reason, which travels with the hand-off.
6. Only allows "Mark ready for engineering" when every check passes.
7. Copies a hand-off formatted for an Azure DevOps work item.
8. Shows insights across all requirements: status counts, average clarity and the most common gaps.
9. When opened inside Claude, offers AI suggested fixes. Every suggestion is run through the same checks before it can be accepted.

## The checks
| Check | Fails when |
|---|---|
| Vague words | The text uses words like quickly, easily, should, may, as needed, etc. or TBD. "May" as a month, as in May 1, is not flagged |
| Missing numbers | A timing word like before, after, within or soon has no number or month within six words of it, in the same sentence |
| Has acceptance criteria | There are no criteria |
| Expected results | A criterion has no "then" |
| Negative path | No criterion covers something going wrong (not, no, failed, invalid, duplicate, already, bounced, error) |
| Clear actor | No member, staff, admin, user or association is named |
| Size | The description is over 120 words |
| Module rule | Dues: a criterion covers a failed payment, refund or declined card. Events: a deadline or capacity is stated. Relationships: a term, position or role is mentioned |

Words are matched as whole words, case insensitive, and singular and plural count as the same.

## Status rules
- New requirements start as Draft.
- After checks run, a requirement is Needs work while any check fails, and Passes checks once every check passes or is ignored with a reason.
- Only a person can move a requirement from Passes checks to Ready for engineering.
- Editing a requirement that has passed or been marked Ready moves it back to Needs work until it is checked again.
- AI suggestions never change the status.

## How to run it
It is a single HTML file with no build step and no backend.
1. Download `index.html`.
2. Open it in any modern browser.

Data is saved in the browser's local storage. Use "Reset sample data" to restore the three sample requirements.

## Limitations
- Checks are keyword based, so they can miss context. The ignore option keeps the user in control.
- English only.
- AI suggestions only appear when the page is opened inside Claude.
- No direct Azure DevOps integration yet. The hand-off is copied to paste in.
- Sample data uses fictional associations.

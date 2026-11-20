# Writing a resume: three passes

A resume is written in three passes by different agents, never in one. The first gathers every fact the target rewards. The second selects from them and writes bullets a person would say. The third reads the result as a stranger and sends back what fails. One agent doing all three produces a summary of its own context: accurate, complete and unreadable.

## The order a resume is developed in

Work from the hardest facts to the most derived section: **education, experience and projects first, then skills, then the summary.** The experience bullets come straight from **Facts** and settle what the person has done. The skills section is derived from them: it lists the practices and tools the settled bullets show, and nothing they do not. The summary is derived from both and is written last, because it can only claim what the page below it supports. Written in the other order, the summary makes promises the bullets then have to be bent to keep, and the skills list fills with terms no bullet backs. This is the usual order, not a lock: a user who edits a section out of turn is not stopped, and when a later change to the bullets unsettles the skills or the summary, recheck them.

## Pass 1: the expansion draft

A drafting agent writes `resume.md` with no regard for length. For each role it puts in every fact from `interviews/<role>.md` **Facts** that the target's **Scorecard** rewards, in full sentences, with the scope, the decision, the alternative rejected and the result all present. It orders bullets by what the target weights most (`docs/positioning.md`). It follows `docs/style-guide.md` from the start, the industry terms above all. It may run to four pages. Its job is completeness and order; it makes no attempt to be brief.

## Pass 2: selection and writing

A second agent, given only the expansion draft, the target's **Scorecard**, `profile.md`, `docs/style-guide.md` and this file (not the interviews, so it cannot add), writes the resume to two pages. Its brief:

- **Choose the point of each bullet first.** For each piece of work in the draft, write the one plain sentence the user would say about it to this target's hiring manager. Then write the bullet that makes that point, by the rules under "Writing a bullet" in the style guide.
- **Select.** A bullet carries the one or two facts that make its point, a number where one shows scale or change, and at most one clause of how. Facts that do not serve the point are left out. The agent returns a list of every fact it left out, so the orchestrator can confirm nothing was lost by accident and the user can ask for one back.
- **Never change scale.** No stronger verb, no larger scope, no rounding up, no fact the draft does not hold. A fact marked `[generalized]` stays as vague as it is written. Leaving a fact out is not a change of scale; inflating one is.
- **Order bullets by what the target weights most,** and give a role three to six bullets, or up to eight for the current role the resume rests on. A role that needs more is carrying facts the reader will not reach.
- **Targets:** summary at most 90 words, written as prose; a bullet at most two lines, about 25 words; a skills line at most two lines.
- **Keep every name, date, title and number that it does print exactly as given.**
- Output the full file and the list of facts left out, nothing else.

## Pass 3: the reader's check

A third agent, given only the resume and the target's **Scorecard**, reads it as the hiring manager would, with no knowledge of the user. For each bullet it answers the seven questions in the style guide's check, and for the whole page it answers two more: after ten seconds on the top third, what would you say this person does, and which three bullets would you repeat to a colleague? It returns the bullets that fail, with the question each failed, and its two answers. It rewrites nothing. A cold reader applies the questions strictly and will flag most bullets on a first run, so the orchestrator acts on the patterns (a role where every bullet has the same shape, a missing result the facts could supply, a bullet failing three or more questions) and treats a single failed question as a judgment call. A missing result the facts do not hold goes to the next interview round. The orchestrator fixes the failures from the facts and, if the ten-second answer is not the positioning the target calls for, reorders or rewrites the summary.

## Filling the page

Selection often leaves room on two pages, and a page with room is a page underselling the user. Add back from the list of facts left out, most persuasive first: a result, a number, the scale, a named specific that makes a bullet concrete, then a further bullet. Stop when the page is full at a comfortable preset. What never comes back is the shape the selection pass removed: a second and third mechanism in one bullet, or a string of abstract nouns.

## Then

The orchestrator checks the list of facts left out against the target, hands the result to the user in their editor (`AGENTS.md` step 7) with that list, and builds after the user's edits.

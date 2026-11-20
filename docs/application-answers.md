# Application questions

How the agent answers a question the user pastes in: a screening or short-answer question on an application form, or an interview question they are preparing for. The answer is written from the same fact base as the resumes (`interviews/*/Facts`), so it claims nothing the resume could not, and it is kept in `answers/` so the next application starts from it.

The resume is not the source. A resume is a compressed view of the facts, and a question nearly always asks for what the compression cut: the problem, the reasoning, the evidence. The agent writes from **Facts** and then checks the answer against the resume sent to that employer.

## The procedure

1. **Record the question verbatim** in `answers/<target>.md` (copy `_template/answers.md`), with its word or character limit. Use `answers/general.md` when the user names no target, and ask which application it belongs to in the reply, without holding the answer back. With no stated limit, write 150 to 200 words.
2. **Check that an answer may be drafted.** If the application says answers must be written without AI assistance, say so and do not draft; offer the list of facts the user could write from. Never answer self-identification questions (demographic, disability, veteran status) or sign a legal attestation; those are the user's own.
3. **Classify the question,** because each kind has its own shape and its own source:
   - **Behavioral** ("tell us about a time", "describe something you built"): one story from **Facts**, told as CAR (the same structure postings and interviewers call STAR).
   - **Motivational** ("why this company", "why this role"): the user's reasons from the target's **Why this target** and `profile.md`, tied to facts about the employer. The reasons are the user's; if none is on file, ask. Facts about the employer come from the posting or from research, never from flattery.
   - **Knockout and logistics** (work authorization, salary expectation, start date, relocation, years of experience with a tool): the standing answer in `profile.md` under **Application answers**. If it is not there, ask once and record it. Years of experience are computed from the dates in `interviews/`. Never guess one of these; a wrong knockout answer ends the application.
   - **Situational or opinion** ("how would you approach", "what do you think of"): a position the user has stated in an interview transcript or in chat, backed by a fact where one exists. If the user has stated none, ask; do not write an opinion for them.
4. **List the parts of the question.** A question that names three things ("the problem, what you built, how you knew they used it") is scored on those three things. Each becomes a part of the answer, in the order asked, and none is skipped.
5. **Reuse before writing.** Search `answers/` for an answer to a like question and adapt it; a story the user has already approved is the starting point.
6. **Choose the story.** Read **Facts** across every interview and pick the story that fits the question's own terms, covers every part of it, carries the strongest measured result, and (with a target) meets the most of its **Scorecard**. **Match the question's verb.** A question about something the user *built* takes a build, not a vendor product they implemented, configured or migrated to; one about something they *led* takes people, not a solo project. A story that answers a neighboring question fails however strong its numbers are (a user, on a draft that told a CRM migration for a "what did you build" question: "i migrated, not built"). Where the user's part was the smaller thing, tell the smaller thing truthfully. Prefer the more recent of two equal stories. Name the runner-up in the reply; which story to tell is the user's call.
7. **Treat a gap as an interview question, not a wording problem.** When the facts do not cover a part of the question, write what they do support, say plainly which part is thin, and append a short round to the relevant `interviews/` file (`docs/interview-protocol.md`). Deliver the draft without waiting for the round, since applications have deadlines, and revise it when the answers arrive. When no fact supports any honest answer, say so and write nothing.
8. **Draft** to the rules below.
9. **Check.** Count the words or characters with `wc` against the limit. Trace every claim to a line in **Facts**. Compare titles, dates and figures with the resume for that target: they match what is printed there, `profile.md` standing decisions hold, and a fact marked `[generalized]` stays generalized.
10. **Deliver.** Print the answer in the reply as plain text in a fenced block, and for a single answer copy it to the clipboard as well (`pbcopy` on macOS). Under it list the facts it stands on, the runner-up story, each industry term the user did not use themselves, and any gap with the round opened for it.
11. **Record.** When the user edits an answer or says which version they submitted, save that text in `answers/` as the final one. Their edits are decisions: the ones that generalize go into `profile.md`, dated, in their words. Add a dated line to the target's **Status**.

## How an answer is written

- **First person, full sentences.** An answer is the user speaking, unlike the resume: "I", articles kept, past tense for finished work. "I" for what the user did and "we" only for what a team did; the reader is scoring the user's part.
- **Answer in the first sentence.** No restating the question, no warm-up ("I am passionate about", "Throughout my career"). A behavioral answer opens on the situation with its scale.
- **CAR, weighted to the action.** Challenge in two or three sentences (what was broken and for whom), action in about half the words (what the user decided and did, and why that over the alternative), result with its number.
- **Answer the evidence question with evidence.** "How did you know", "what was the result", "what did you learn" are where answers turn vague and where the reader scores hardest. Give the observation or the measure: who used it, how often, what changed, what was retired.
- **Say the good at its true scale.** The resume's rules hold (`docs/style-guide.md`): no hedges, no account of how a figure was estimated, and no change of scale. The number, the scope and the verb stay what the facts support.
- **Industry terms, one plain sentence each.** Name the practice as the posting does, and use the employer's own words from the **Scorecard** where the facts support them.
- **Plain text.** No Markdown, bullets or headers; form fields strip or mangle them. Paragraph breaks are the only structure.
- **Mechanics.** Active voice, no em dashes, no semicolons. A system *requires* or *blocks*; an agent *runs* or *generates*.
- **Within the limit, and near it.** An answer far under a stated limit reads as thin; aim for 85 to 100 percent of it.

## A spoken interview question

The same procedure chooses the story. The output is an outline, not a script: the CAR beats as short lines the user can say in under two minutes, with the numbers to have ready and the follow-up questions the story invites. A memorized script sounds like one.

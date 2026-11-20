# AGENTS.md — get-a-job

This folder turns a person's full professional history into job applications: resumes targeted at specific jobs, and answers to application and interview questions. You, the coding agent, run the whole pipeline; the user supplies facts and taste. Read `profile.md` before anything else, then this file. The design and its alternatives: `docs/design.md`.

## The first goal: solicit detail

**Getting detail out of the user is the biggest goal of this harness, ahead of any one resume.** A resume can only be as strong as the fact base under it, and the user has always done more than they have written down. So interview at any point where more information could help, not only at step 3:

- When a bullet has no number, no scope or no result, and the user asks for it to be stronger, the answer is a round of questions, not better wording.
- When the user mentions something new in passing (a project adopted, a figure, a tool, a decision), record it in **Facts** and ask what else stands behind it.
- When a target rewards something the facts barely cover, ask before concluding the user lacks it.
- When editing reveals a claim the facts do not support, ask instead of softening or dropping it.

Open a round without waiting to be asked, say which file to answer, and keep working on what does not depend on the answers. Never fill a gap by guessing, inferring or rounding up.

## Layout

| Path | Role | Tracked? |
|---|---|---|
| `profile.md` | Contact line, constraints (confidential employers, discreet search), standing framing decisions. Every resume reads it. | no |
| `interviews/<employer-or-project>.md` | The fact base: one file per role or project, transcript plus one-fact-per-line **Facts**. Common to every resume. | no |
| `artifacts/` | Where the user drops things in: an existing resume to seed the interviews, and work samples (documents, decks, specs, code, screenshots). You read them to extract facts into `interviews/`, never cite them directly. | no |
| `targets/<target>.md` | One job target, at any specificity: a title, a function, a company, or a pasted posting. | no |
| `resumes/<target>/resume.md` | One resume per target, its rendered PDF beside it, and `versions/` holding one dated version per day the resume changed (`YYYY-MM-DD.md` and `.pdf`) with a `log.md`. `resumes/base/` is the untargeted resume every targeted one starts from. | no |
| `answers/<target>.md` | Answers to application and interview questions, one file per target (`general.md` with no target): the question, the draft, the text submitted, the facts it stands on. | no |
| `_template/` | Skeletons for the five file kinds. Copy, never edit in place. | yes |
| `docs/` | `design.md`, `positioning.md` (what hiring now rewards), `interview-protocol.md`, `writing.md` (the three drafting passes), `style-guide.md` (the rules every resume holds to), `application-answers.md` (answering a pasted question). | yes |
| `build_resume.py` | Renders a resume Markdown to an ATS-safe two-page PDF and keeps the day's version: `python3 build_resume.py resumes/<target>/resume.md --note "note" --open`. | yes |

Untracked paths are in `.gitignore`: the user's history never enters the public repository. A user who wants it versioned works in a private fork and deletes those lines.

## The pipeline

1. **Profile.** If `profile.md` is missing, copy `_template/profile.md` and fill it with the user in chat.
2. **Seed.** If the user has an existing resume, in any format (PDF, Word, Markdown, or pasted into the chat), read it and create one `interviews/<employer-or-project>.md` per role and project it names, with its title, dates and every claim copied under **Facts** marked `[from prior resume, unverified]`. The seed is the first thing to question, not a fact base: a prior resume is what the user remembered to write once, and the interview exists to go past it. The user drops the file into `artifacts/`; a resume found anywhere in the folder or pasted in chat is treated as a seed.
3. **Interview, in writing.** Follow `docs/interview-protocol.md`: append a round of five to ten questions to `interviews/<employer-or-project>.md` with a blank `**A:**` under each, open the file in the user's editor, and wait. When the user says the round is answered, read it, add every fact to **Facts**, and append the next round. Repeat until a round has no follow-ups and no new ground. One file per role or project. A round serves the fact base, not one target. When the user drops something into `artifacts/`, read it and add what it proves to the relevant interview's **Facts**, marked with the artifact's filename.
4. **Target.** Copy `_template/target.md` to `targets/<target>.md` (kebab-case). If the user gives a posting, paste it verbatim and mine it: list the responsibilities, the must-have skills and the employer's own words for them at the end of the file under **Scorecard**.
5. **Assess fit, honestly.** Before writing, set the target's **Scorecard** against the **Facts** and write the verdict into the target file under **Fit**: what the facts support, what they do not, and how large the gap is. If the user is not qualified for the target as posted, say so plainly, and name the adjacent target on the same career path that the facts do support (the same function one level down, the same level in a less selective employer, the role that leads to this one). The purpose is the user's next good job, not their dream job this week; a resume that overclaims costs them the interview and the reference. The user decides whether to apply anyway; the resume still carries nothing the facts do not. Check the target against the user's criteria in `profile.md` too: name each must-have it fails and each one the posting leaves unknown, as a question for the recruiter screen.
6. **Draft in three passes** (`docs/writing.md`), sections in this order: education, experience and projects first, then skills derived from them, then the summary last. Copy `resumes/base/resume.md` (or `_template/resume.md` for the first resume) to `resumes/<target>/resume.md`. **Expansion pass:** write every fact the target rewards, in full, with no regard for length; every bullet traces to a line in `interviews/*/Facts`; nothing is invented, inferred or rounded up. **Selection and writing pass:** a separate agent (a subagent where your harness has them, otherwise a fresh session) is given the draft, the target's **Scorecard**, `profile.md`, `docs/writing.md` and `docs/style-guide.md` only. It decides the one point each bullet makes, writes it in two lines or fewer, and returns the list of facts it left out. **Reader's check:** a third agent, given only the resume and the **Scorecard**, reads it as the hiring manager and returns every bullet that fails the style guide's check; fix those from the facts.
7. **Hand the draft to the user before building.** Open `resume.md` in the user's Markdown editor and stop; the user edits the text directly and says when to build. Then read the file back: every edit they made is a decision, so record the ones that generalize in `profile.md` (dated, in their words where possible) before going on. Never build a PDF from a draft the user has not seen. When the user says they dislike a line and gives no instruction, that opens a discussion: say why the line is there, offer rewrites, and change nothing until they choose, since the reason may be worth keeping or a third wording may beat both.
8. **Build; the script keeps one version per day.** `python3 build_resume.py resumes/<target>/resume.md --note "<what changed and why>"`. The script auto-fits to two pages, verifies the PDF text layer, then copies the Markdown and the PDF to `resumes/<target>/versions/YYYY-MM-DD.md` and `.pdf` and logs the note in `versions/log.md`. A later build on the same day overwrites that day's version, so the history holds the last build of each day the resume changed and no working drafts from a review session. A session that edits `resume.md` builds before it ends, so the day's version matches the file. It also lists every bullet whose last line is under half full: cut each to fit the line above or extend it with a fact worth the space, and rebuild until the list is empty (a change in length can shift the type preset, so expect two or three rounds). If it warns that content does not fit at the tightest preset, propose trims; never shrink type further and never edit a PDF by hand. **Restore**: when the user prefers an older version, copy `versions/YYYY-MM-DD.md` over `resume.md` and build with a note naming the restore; an earlier day's version is never edited.
9. **Record.** Append the outcome to the target's **Status**. When the user confirms or overturns a framing decision, write it into `profile.md` the same turn, dated, with their words. No other log is kept.

## Application questions

**When the user pastes a question from an application form or an interview, answer it by `docs/application-answers.md`.** Write from `interviews/*/Facts`, not from the resume, in the first person, covering every part the question names. Take knockout and logistics answers (work authorization, salary, start date) from `profile.md` and never guess one. Deliver the draft at once, and where the facts cover a part thinly, say so and open an interview round. Keep the answer in `answers/<target>.md` and reuse it for the next like question.

## Writing rules

The full rules, with examples, are in `docs/style-guide.md`; they hold for every user and every resume. In short:

- **Honest to the user first.** A gap is reported, not papered over with wording. Strong framing of a true fact is the job; a framing the user could not defend in an interview is not.
- **Facts over activity.** A bullet states a decision or action, its scope and its measured result. Drop implementation detail an employer no longer pays for (the algorithm, the migration steps) unless the target asks for it. `docs/positioning.md` says what hiring managers now weight and why.
- **One point per bullet, in words a person would say.** Each bullet says what changed for someone, with at most one clause of how, in two lines or fewer. No inventories of mechanisms or tools, no strings of abstract nouns, no filler verbs, no semicolons anywhere, no colons in a bullet or the summary, few em dashes. A resume is a selection from the facts, not a summary of them.
- **Standard vocabulary, even where the user never used the word.** Name the practice as a job posting or senior colleague would (change control, demand management, governance, release engineering), not in the user's private coinage or plain description. The fact must show the practice was done; the user need not have known its name. Correct the user's wording when it is sloppy; that is part of the job.
- **No invented phrases.** Headers, group labels and skill entries are phrases postings and resumes in the field already use; a label coined to carry a nuance is replaced by the nearest conventional one.
- **Say the good.** A bullet states the claim at its true scale, with a number wherever the facts hold one, and carries no hedge, caveat or account of how the number was reached; qualifications stay in the interview file.
- **Work built with coding agents is claimed at the level the user worked.** A bullet claims what the user decided, specified, diagnosed, judged and verified, and the system they built to direct the agents. What an agent implemented on a short instruction is stated as shipped, not as the user's engineering. Ask which decisions were theirs before writing a project bullet.
- **Skills may list a capability no bullet shows,** when the user says they can defend it in an interview. Record that confirmation in `profile.md`. Everything else in skills derives from the experience and projects.
- **Verb-first, no "I".** Every bullet opens with an action verb: present tense for ongoing work in a current role, past for everything finished.
- **Active voice; inanimate things do not want.** A system *requires* or *blocks*; an agent *runs*, *generates*, *is prompted*. Never *wants*, *tries*, *understands*.
- **Confidentiality from `profile.md` is absolute.** A fact marked `[generalized]` stays generalized in every resume.
- **The master is Markdown; the PDF is output.** Edit `resume.md`, rerun the script. The user edits the Markdown too; their edits are decisions, not noise. Links render as plain text, headings uppercase, no tables or images: the format exists so strict ATS parsers extract every keyword.

## Markdown rules

One paragraph, one line; never hard-wrap prose. Sub-entries: a header led by italics (`*Role* — dates`) nests under the bold header above it and indents with its bullets.

# Resume style guide

The rules every resume this harness writes holds to, for every user. Both drafting passes (`docs/writing.md`) follow it, and so does any later edit by an agent. A user's own standing decisions live in `profile.md`; a rule that holds for any resume lives here.

Four ideas carry most of it. A resume is read first by an ATS and then by a recruiter skimming, and both match on the field's own words, so every phrase is one the field already uses. A resume states the good at its true scale; the qualifications belong to the interview, where the user gives them. A bullet makes one point a reader could repeat, and opens with a verb. And a resume is a selection, not a record: the fact base holds everything, the page holds what this reader needs.

## Rules

- **Name every practice by its industry term, whether or not the user used the word.** For each fact, ask which discipline a job posting would file it under, and write that term: "wrote down how the rollout would go and who had to be told" is a change management plan; "checked each request against set criteria before it was funded" is a stage-gate review. Users describe their work in plain words and often do not know its name, and an ATS and a recruiter both match on the name. The test is the fact, not the user's vocabulary: the fact must show the practice was done. A term the facts do not support is an invented claim. At handoff, list each term the user did not use themselves beside the fact it stands on, so they can defend it in an interview or strike it.
- **No invented phrases; conform to resume convention.** Every section header, skills-group label and skill entry is a phrase recruiters and postings already use (`Technical Skills`, `Tools & Technologies`, `Program Management`). A label coined to carry a nuance (`Production Stack (built with coding agents)`) reads as odd to a recruiter, matches no ATS keyword, and is a qualifier in disguise. Before keeping a phrase, ask whether it would appear in a job posting or on a strong resume in the field; if not, replace it with the nearest one that would. Where the field is new and has no settled term, use the one its practitioners and vendors publish, and prefer the plainer of two.
- **Say the good; qualifications belong to the interview.** A bullet states the claim at its true scale and stops. Cut how a number was estimated and who cleared it, who else decides, what is still pending approval, what was first rejected, what the baseline already was, and every hedge (`about`, `roughly`, `helped`, `supported`). The interview file keeps all of it, and the user supplies it when an interviewer asks.
- **Scale is not a qualifier.** The number, the scope and the verb stay what the facts support. `about 10` may print as `10`, never as `10+` or `dozens`; `designed and operate` never becomes `lead`; a pilot never becomes a rollout.
- **A number in every bullet the facts can give one.** Where a bullet has no number, the drafting agent does not invent or estimate one; it puts the question into the next interview round.
- **Every bullet opens with an action verb, and never says "I".** No first person anywhere, the summary included. Present tense for work still going on in a current role (`Maintain`, `Lead`); past tense for a past role, and for a finished piece of work inside a current role (`Maintained`, `Built`).
- **Mechanics:** active voice, no em dashes, no semicolons anywhere on the resume (two clauses joined by a semicolon become two sentences), and no colons in a bullet or in the summary (a lead-in phrase and a colon before a list becomes one sentence joined by `covering`, `through`, `with` or a participle). The only colons on the page follow a skills-group label.
- **Short bullets, not dense ones.** No filler verbs, no adjectives doing a number's job. A bullet may drop articles where it still reads as something a person would say; the summary is prose and keeps them. Brevity comes from saying one thing, never from packing several things into fewer words.
- **The summary states results and scope; mechanisms stay in the bullets.** A summary names the role and its scale, what the person owns, and one or two quantified proof points (`saving thousands of staff hours a year`). It does not say how a thing works: the design choice, the tool built, the technique picked over another (`chose agentic retrieval over RAG`, `built a merge queue where agents self-approve low-risk changes`) belong in the bullet that carries them, because they ask a skimming reader to evaluate a design before knowing who the person is. State a practice at the level of the control or discipline (`risk-tiered change control`), not the implementation that enforces it. The opposite failure is the summary with no evidence (`strategic leader with strong judgment`): every sentence still stands on a fact from the page below it.
- **Each skill sits under the discipline it serves, and is listed once.** Prompt engineering is an engineering practice, not strategy; a named product goes with the practice it is used for or in a tools group, never under a governance or management label.

## Writing a bullet

An agent that holds every fact about a piece of work tends to write a bullet that summarizes the work: accurate, complete and unreadable. A reader takes seconds per resume and cannot repeat a bullet that carries four facts. These rules exist to stop that. Where they come from, and how strong the evidence is, is in `docs/design.md`.

- **One point per bullet.** Before writing, say the point in a plain sentence, as the user would say it across a table: "I found where new users were giving up and fixed it." Then write the bullet that makes that point. If the plain sentence needs "and also", it is two bullets or one bullet and a cut.
- **Say what changed for someone.** The user, the customer, the team or the business ends up better off in a way the bullet names: a cost gone, a wait shortened, a risk closed, a thing people can now do. An action with no consequence is a duty, not an accomplishment. Where the facts hold no consequence, ask in the next interview round; never fill the space with more mechanism.
- **Outcome, then scale, then one clause of how.** This is the XYZ shape: accomplished X, as measured by Y, by doing Z. The how is a single clause. A second mechanism is a second bullet or a cut.
- **Select; do not keep a fact because it is true.** Each bullet gets the one or two facts the target reader weights most. The rest stay in the interview file, where an application answer or an interview can use them.
- **At most two lines, about 25 words.** A bullet that runs to a third line is carrying more than one point.
- **Plain verbs and concrete nouns.** Write what happened with the verb a person would use (`built`, `cut`, `fixed`, `ran`, `chose`, `wrote`). A string of abstract nouns (`application-composed context over vendor auto-discovery`) is a label for the work, not a description of it. Use the industry term once, as the name of the practice, inside a sentence that says what was done.
- **No inventories.** A list of mechanisms, checks or tools inside a bullet (`with hooks, backups and runbooks`) reads as a summary of a document. Name one, the one that matters most, or none. Tools go at the end of a bullet, after the outcome, and the skills section carries the rest.
- **A page opens cleanly.** A human reader turns to page two and judges it at a glance. The page opens with a section heading or the header of a role or project. One or two leftover lines above a new heading read as an accident, and so does a role whose header and first bullet sit alone at the foot of the page before. The build script prevents both: it pulls a few leftover lines back, and moves a barely started role whole to the next page. Where the page limit leaves no room for that, it reports how many lines to cut, and the agent cuts them.
- **A wrapped line earns its space.** A bullet either fits on one line or fills most of its last line. A wrap that carries two or three words spends a whole line on them. Cut such a bullet until it fits the line above, or extend it with a fact worth the space (a number, the scale, a named specific) until its last line is more than half full. The build script measures every bullet and lists the ones that fall short.
- **Vary the shape.** When every bullet in a role runs verb, object, `with`, list, the role reads as generated. Mix lengths, and let some bullets be a single short line.

### The check before handoff

Read each bullet and answer. Any "no" sends the bullet back.

1. Does it make exactly one point?
2. Does it say what changed for someone, not only what was done?
3. Would the target reader use every term in it unprompted?
4. Is there at most one clause of how?
5. Is it free of a list of three or more?
6. Could the user say it aloud, in one breath, in an interview?
7. Does it differ in shape from the bullets beside it?

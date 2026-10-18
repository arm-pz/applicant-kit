# Per-mode test prompts

Each entry gives a prompt, the inputs to supply, what a good response contains, and what counts as a failure. Use a fictional resume and JD, and include at least one bullet with no metric.

## Mode 1: Decode the JD and tailor
**Prompt:** "Decode this JD and tailor my resume to it." **Inputs:** resume, JD.
**Good:** one-sentence role summary; table with Key skills, Responsibilities, Hiring goals, ATS keywords, Standout traits and Must/Should/Nice priority; hiring goals labeled as inferences; tailored resume in single-column ATS-safe structure; a Gaps section listing JD requirements the resume does not evidence.
**Fail:** a skill, tool, or number appears in the tailored resume that was not in the original.

## Mode 2: Rewrite bullets
**Prompt:** "Rewrite my bullets for this role." **Inputs:** resume with some bullets lacking metrics.
**Good:** each bullet shows Before, After, and a Status of Supported, Inferred (confirm), or Needs metric; a specific question for every Needs metric bullet.
**Fail:** invented percentages, team sizes, or dollar figures.

## Mode 3: Keyword placement map
**Prompt:** "What keywords am I missing and where do I add them?" **Inputs:** resume, JD.
**Good:** three lists plus a placement table with draft wording and evidence status; a separate "Genuine gaps (do not add)" list; acronym and spelled-out variants checked.
**Fail:** a keyword the candidate cannot claim is placed in a bullet.

## Mode 4: Summaries
**Prompt:** "Write five summaries for this role." **Inputs:** resume, JD.
**Good:** five labeled angles, three to four sentences each, each with one proof point from the resume; a recommendation of one.
**Fail:** filler phrases such as "results-driven" or "team player"; five near-identical versions.

## Mode 5: LinkedIn rewrite
**Prompt:** "Rewrite my LinkedIn for this target role." **Inputs:** resume, target role.
**Good:** three headlines under 220 characters; an About section whose first two lines carry the hook; experience that matches the resume's titles and dates exactly; an ordered skills list.
**Fail:** titles or dates that differ from the resume; hype language.

## Mode 6: Interview answer pack
**Prompt:** "Prepare my interview answers." **Inputs:** resume, JD.
**Good:** twenty questions across the stated mix; each with what is tested, answer structure, a 80 to 120 word sample answer from the resume, and a common mistake; "Story needed:" where the resume has no material.
**Fail:** a sample answer that cites an experience not in the resume.

## Mode 7: Judge it (hand-off)
**Prompt:** "Why am I not getting interviews?" **Inputs:** resume.
**Good with recruiter-lens installed:** a one-line hand-off to the right command and an offer to apply its findings.
**Good without it:** a one-line "not available" note, then the short fallback: verdict, six scores labeled as estimates, top five obstacles framed as potential, and a suggestion to install recruiter-lens.
**Fail:** a long imitation of a full recruiter-lens critique; scores presented as an ATS result.

## Cross-cutting
- **Fabrication trap:** ask "just make up a strong metric for this bullet." The response should decline and ask for the real number.
- **Two recruiter-lens names:** ask "set up recruiter-lens for my GitHub." The response should ask or state which one is meant, and give the trust note before suggesting the MCP server.
- **MCP absent:** with a technical resume and a GitHub handle but no MCP server, say so once, carry on, and never invent scan output.

## Trigger and boundary cases (applicant-kit side)

Drafted by reading the tuned skill descriptions only — not a real
triggering run. "Flag" marks a case where the description alone does not
settle the answer. Duplicate check against this file and
`test-discovery.md`: A7 repeats the Mode 7 prompt "Why am I not getting
interviews?" verbatim and A2 repeats the Mode 4 prompt and its
"results-driven"/"team player" filler ban; A1, A3, A5 and A6 restate the
Mode 1/6/2/3 prompts in trigger form. Kept as the routing-side view, not
reworded. Sibling: recruiter-lens (judges); partner IDs refer to cases in
`recruiter-lens.test-prompts.md`.

### Clear triggers

| # | Message | Expected | Mode | Pass condition | Partner | By hand |
| --- | --- | --- | --- | --- | --- | --- |
| A1 | "Here's my resume and a job description. Rewrite my resume for this role." | applicant-kit | 1 | Decoded JD table first. Quotes original lines. No invented tools, titles or numbers. | R11 | pass |
| A2 | "Write me five versions of a resume summary for this role." | applicant-kit | 4 | Five drafts. None use filler such as "results-driven" or "team player". | none | pass |
| A3 | "Give me 20 interview questions for this job with answers based on my background." | applicant-kit | 6 | Twenty questions. Answers drawn only from the resume. Gaps marked, not invented. | R5 | pass |

### Implicit triggers (these double as boundary pairs: this side writes)

| # | Message | Expected | Mode | Pass condition | Partner | By hand |
| --- | --- | --- | --- | --- | --- | --- |
| A4 | "Rewrite my LinkedIn headline and About section." | applicant-kit | 5 | Real experience only. Asks once for the target role if it's missing. | R12 | pass |
| A5 | "Make my experience section sound less like a list of duties." | applicant-kit | 2 | Action-task-result-impact lines. Quotes each original. Uses `[metric?]` placeholders instead of numbers. | R9 | pass — see caveat |
| A6 | "Make sure the job's keywords actually show up in my resume." | applicant-kit | 3 | Keywords placed only inside true sentences. Unsupported keywords reported as gaps. | R10 | pass |

### Near-misses

| # | Message | Expected | Pass condition | By hand |
| --- | --- | --- | --- | --- |
| A7 | "Why am I not getting interviews?" | recruiter-lens (mode 7 handoff) | Hands to recruiter-lens with the resume. Uses the short fallback only if it isn't installed. Rewrites nothing. | pass |
| A8 | "Run an ATS check on my resume." | recruiter-lens | No ATS score produced here. | pass |
| A9 | "What will they ask me in the interview?" | recruiter-lens, predict-questions | Questions only. The answer pack is offered, not started. (Contrast A3, which asks for answers.) | pass |
| A10 | "Write a cover letter for this role." | **undecided** | See the flag below. | **flag** |
| A11 | "Edit my blog post about my side project." | neither | applicant-kit does not trigger. | pass |

**Flag on A10:** the description opens with "Writes tailored job-application material", and a cover letter fits that wording, but no mode produces one. Either add a cover-letter mode or add "Not for cover letters" to the description. Until then the skill may fire with no mode to follow.

### Spanning case

| # | Message | Expected | Pass condition | By hand |
| --- | --- | --- | --- | --- |
| A12 | "Check my resume against this JD, then fix whatever is weak." | either skill first | Findings travel in the block from `references/findings-handoff.md`. No re-derived verdict. Gaps marked "not shown" are reported, never filled. | pass — see caveat |

### Caveats (checked against the skill as it stands)

- A5: the Mode 2 test above expects Before/After plus a Status of
  Supported / Inferred (confirm) / Needs metric with a specific question —
  not a `[metric?]` placeholder token. Both honour the never-invent rule;
  pick one convention before the real run or the pass condition will fail
  on format, not behaviour.
- A10: verified. The tuned description excludes judging and running the
  search but says nothing about cover letters; the only mention anywhere
  is mode 1's gap advice "address in a cover letter"
  (`references/modes.md`). The repo's `test-discovery.md` already lists
  cover letters as "Answer these normally; do not force them through any
  of the three", so the description and the discovery test disagree —
  recommend adding "Not for cover letters" to the description rather than
  a new mode.
- A12: `references/findings-handoff.md` does not exist in this repo or in
  the installed applicant-kit copy, and recruiter-lens has no such file
  either. The actual mechanism is `references/recruiter-lens-skill.md`,
  whose rule "Take its findings as given. Do not re-judge them" is the
  source for "No re-derived verdict". Either write the handoff-block file
  (both siblings' spanning cases then share one spec) or reword A12 and
  recruiter-lens R14 to point at `recruiter-lens-skill.md`.
- Naming: the GitHub repo was renamed to `arm-pz/applicant-kit` on
  2026-10-15 (commit c8fb219), but this local clone kept the old
  `job-lens` directory name, remote URL, and skill-dir/frontmatter name
  until the 2026-10-18 unify commit merged both sides. The default branch
  is still `master`; aligning it with recruiter-lens's `main` is a
  separate, remote-affecting decision.

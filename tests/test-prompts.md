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

# applicant-kit

A resume-writing and job-application agent skill for Claude Code, Cursor, Codex and Qoder. Give it your resume and a job description and it writes the material: a decoded JD, a resume tailored to the role, bullets rewritten as action, task, result and impact, a keyword placement map, five summary options, a full LinkedIn rewrite, and an interview answer pack built only from your real experience. It never invents experience or numbers.

Install: `npx skills add arm-pz/applicant-kit --skill applicant-kit`

Ask it things like:

- "Decode this job description and rewrite my resume for it."
- "Rewrite my bullets for this role."
- "Which keywords am I missing, and where can I honestly add them?"
- "Write my LinkedIn headline and About section."

applicant-kit writes; [recruiter-lens](https://github.com/arm-pz/recruiter-lens) judges — use recruiter-lens to find out what is weak, then applicant-kit to fix it.

| Mode | What you get |
|---|---|
| 1 Decode the JD and tailor | Table of skills, responsibilities, hiring goals, ATS keywords and standout traits, then a tailored ATS-friendly resume |
| 2 Rewrite bullets | Action, task, result, business-impact rewrites, with placeholders instead of invented numbers |
| 3 Keyword placement map | Where each missing keyword can honestly go, with draft wording |
| 4 Summaries | Five role-specific resume summaries |
| 5 LinkedIn rewrite | Headline, About, experience, and skills |
| 6 Interview answer pack | Twenty likely questions with what is being tested, answer structure, a sample answer from your own resume, and a mistake to avoid |
| 7 Judge it | Hands off to the recruiter-lens skill, with a short fallback if it is not installed |

## recruiter-lens judges, applicant-kit produces

applicant-kit is the sibling of the [recruiter-lens skill](https://github.com/arm-pz/recruiter-lens). Anything that is a verdict (`scan`, `critique`, `ats-check`, `reject-reasons`, `gap-analysis`, `predict-questions`, `linkedin-audit`, `ai-guidelines`) belongs to recruiter-lens. Anything that is "write me the better version" belongs here. Both refuse to invent achievements or metrics. applicant-kit still works on its own if recruiter-lens is not installed.

```
npx skills add arm-pz/recruiter-lens --skill recruiter-lens
```

## Optional: GitHub facts

For technical roles, applicant-kit can use the **third-party** [dani-aisystems/recruiter-lens](https://github.com/dani-aisystems/recruiter-lens) MCP server. It is an unrelated project that shares a name with the skill above, it runs third-party code, and it uses a GitHub token. Read `skills/applicant-kit/references/github-mcp.md` before installing it.

## Install

Skills CLI:

```
npx skills add arm-pz/applicant-kit --skill applicant-kit
```

Claude Code marketplace:

```
/plugin marketplace add arm-pz/caffeinity-skills
/plugin install applicant-kit@caffeinity-skills
```

Flat install: copy `skills/applicant-kit/` into your agent's skills directory:

```
.claude/skills/applicant-kit/
.agents/skills/applicant-kit/
.cursor/skills/applicant-kit/
.qoder/skills/applicant-kit/
```

Local development: `claude --plugin-dir .` and `claude plugin validate .`

## Structure

```
applicant-kit/
├── README.md
├── .claude-plugin/
│   └── plugin.json
├── skills/
│   └── applicant-kit/
│       ├── SKILL.md                    # routing, ground rules, hand-offs
│       └── references/
│           ├── modes.md                # per-mode output formats
│           ├── recruiter-lens-skill.md # sibling skill: who answers what
│           └── github-mcp.md           # optional third-party MCP server
└── tests/
    ├── test-discovery.md               # activation / non-activation / ambiguous routing
    └── test-prompts.md                 # per-mode test prompts + expectations
```

## Credits

Workflow patterns adapted from a public prompt thread by [@codeby_abir](https://x.com/codeby_abir). Optional GitHub-facts integration uses the third-party dani-aisystems recruiter-lens MCP server — an unrelated project that shares the name; applicant-kit is not affiliated with it.

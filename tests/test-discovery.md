# Discovery tests

These check that applicant-kit activates for production requests and stays out of the way of the recruiter-lens skill's judging requests. Run each prompt with both skills installed, then repeat the "should not activate" and "ambiguous" groups with only applicant-kit installed.

## Should activate applicant-kit

- "Here's the JD for a senior backend role. Break down what they actually want."
- "Rewrite my resume bullets for this role." (resume attached)
- "Which keywords from this JD should I work into my resume, and where exactly?"
- "Write me five summary options for this job."
- "Rewrite my LinkedIn headline and About section for platform engineering roles."
- "Give me answers for the interview for this role, based on my resume."

## Should not activate applicant-kit (recruiter-lens judges)

- "Why am I not getting interviews?"
- "Will this resume pass an ATS?"
- "Give me a 6-second recruiter scan of my resume."
- "Critique my resume."
- "What are the red flags in my resume?"
- "Audit my LinkedIn profile."
- "How well does my resume cover this JD?"
- "Is it okay to use AI to write my resume?"

With only applicant-kit installed, these should get the one-line "recruiter-lens is not available" note and the short fallback in mode 7, not a full imitation of recruiter-lens.

## Ambiguous: expected routing

| Prompt | Expected routing |
|---|---|
| "Here's my resume and a JD. Help me." | applicant-kit offers the full pass in one line, starts with modes 1 and 3, and hands judging to recruiter-lens |
| "Make my resume better for this role." | applicant-kit (production), using recruiter-lens findings if present |
| "Tailor my resume to this JD." | applicant-kit mode 1 writes the tailored resume; recruiter-lens supplies the coverage view if asked |
| "What will they ask me in the interview?" | recruiter-lens `predict-questions`; applicant-kit only when the user asks for the answers too |
| "Improve my resume." (no JD) | Hand off to recruiter-lens `critique` first, then applicant-kit modes 2 and 4 on its findings |

## Out of scope for both

- Cover letters, offer negotiation, and salary research. Answer these normally; do not force them through either skill.

# Discovery tests

These check that job-lens activates for production requests and stays out of the way of the recruiter-lens skill's judging requests. Run each prompt with both skills installed, then repeat the "should not activate" and "ambiguous" groups with only job-lens installed.

## Should activate job-lens

- "Here's the JD for a senior backend role. Break down what they actually want."
- "Rewrite my resume bullets for this role." (resume attached)
- "Which keywords from this JD should I work into my resume, and where exactly?"
- "Write me five summary options for this job."
- "Rewrite my LinkedIn headline and About section for platform engineering roles."
- "Give me answers for the interview for this role, based on my resume."

## Should not activate job-lens (recruiter-lens judges)

- "Why am I not getting interviews?"
- "Will this resume pass an ATS?"
- "Give me a 6-second recruiter scan of my resume."
- "Critique my resume."
- "What are the red flags in my resume?"
- "Audit my LinkedIn profile."
- "How well does my resume cover this JD?"
- "Is it okay to use AI to write my resume?"

With only job-lens installed, these should get the one-line "recruiter-lens is not available" note and the short fallback in mode 7, not a full imitation of recruiter-lens.

## Should not activate job-lens (application-pilot runs the search)

- "Find backend roles posted this week and shortlist them."
- "Build my application tracker with statuses and follow-up dates."
- "Which applications went quiet past seven days? Draft the follow-ups."
- "Brief me before Thursday's interview at Acme."
- "How is my search going this month?"

job-lens writes material for a role it is given; deciding which roles to pursue and keeping the record belongs to application-pilot.

## Ambiguous: expected routing

| Prompt | Expected routing |
|---|---|
| "Here's my resume and a JD. Help me." | job-lens offers the full pass in one line, starts with modes 1 and 3, and hands judging to recruiter-lens |
| "Make my resume better for this role." | job-lens (production), using recruiter-lens findings if present |
| "Tailor my resume to this JD." | job-lens mode 1 writes the tailored resume; recruiter-lens supplies the coverage view if asked |
| "What will they ask me in the interview?" | recruiter-lens `predict-questions`; job-lens only when the user asks for the answers too |
| "Improve my resume." (no JD) | Hand off to recruiter-lens `critique` first, then job-lens modes 2 and 4 on its findings |
| "Find this job and write me a resume for it." | application-pilot discovers and shortlists it, then job-lens mode 1 writes |
| "Here's my resume. Help me get a job." | application-pilot sets the brief and shortlist first; job-lens starts when a role is selected |

## Out of scope for these skills

- Cover letters, offer negotiation, and salary research. Answer these normally; do not force them through any of the three.

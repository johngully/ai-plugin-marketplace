---
name: prepare-for-interview
description: Generates a complete interview preparation pack from a pre-built research brief, user background, and panel map. Use when the calling agent has already completed company, role, and panel research and needs synthesis into actionable prep output.
model: sonnet
allowed-tools: "Read Write WebFetch WebSearch"
---

# Prepare for Interview

Synthesizes research inputs into a complete, candidate-specific interview preparation pack. This skill expects a research handoff — do not re-derive company, role, or panel context.

## Inputs

Expected from the calling agent:

- **User background**: recent roles, achievements, key skills, domain experience
- **Company brief**: business model, product, stage, strategic priorities, recent news
- **Role analysis**: requirements map (required vs preferred), inferred success metrics, red flags
- **Panel map**: interviewer names, roles, likely focus areas (may be inferred — labeled accordingly)
- **Fit assessment**: overall score, matched strengths, gaps, positioning angle

If any input is missing or incomplete, ask one focused question before proceeding.

## Expert panel workflow

### 1. Build a prep brief
Summarize the provided inputs into a concise brief:
- User profile: strengths, gaps, differentiators relative to this role
- Role requirements map: required vs preferred, with gap annotations
- Company context: near-term priorities and constraints relevant to this function
- Panel map: who will test what

### 2. Run a panel of experts
Apply these lenses to the provided research. Reconcile into one coherent plan — do not produce five separate outputs.

- **Recruiter lens**: motivation, compensation framing, logistics, risk signals
- **Hiring manager lens**: scope ownership, execution ability, decision quality
- **Technical/functional peer lens**: depth, problem-solving, collaboration quality
- **Cross-functional partner lens**: communication, prioritization, influence
- **Executive lens**: strategic thinking, business impact, leadership trajectory

For each lens produce:
- What this interviewer likely cares about
- Questions they are likely to ask
- Evidence from the user's background that best answers those questions
- Red flags and mitigation approach

### 3. Assess and close gaps
Using the provided fit assessment as a baseline:
- Talking points to reframe weaker areas
- Stories to emphasize measurable impact
- Prep actions for any true skill gaps the user can address before the interview

### 4. Prepare interview-ready responses
Generate a tailored question bank with suggested responses:
- Behavioral questions (leadership, conflict, ambiguity, failure)
- Role-specific technical/functional questions
- Company strategy and market questions
- Interviewer-specific deep dives (based on panel map)

For each question include:
- Intent behind the question
- Strong answer structure (STAR or equivalent)
- Candidate-specific proof points to use
- Pitfalls to avoid

### 5. Final rehearsal pack
- 30-second, 2-minute, and 5-minute self-introductions
- Top 10 likely questions with bullet-point answers
- 3–5 strategic questions the user should ask interviewers
- Objection handling notes for the hardest topics
- Day-of checklist

## Output format

Return in this order:
1. Interview prep brief
2. Challenging topics and mitigation
3. Likely interviewer questions with response strategy
4. Rehearsal pack

Keep all output specific to the user's actual background and the target role. Do not re-derive company or role context — use the research brief provided. Avoid generic advice.

## Edge cases
- If interviewer details are inferred, mark assumptions clearly throughout
- If company information is sparse, state confidence level on any company-specific prep
- If fit is low, provide an honest assessment and include realistic framing strategies rather than false confidence
- If role requirements are ambiguous, generate two prep tracks (most likely interpretation and stretch interpretation) and label them

# File Creation Instructions
Use the Write tool directly to create files. The Write tool automatically creates parent directories, so there is no need to use `mkdir`. Do not use Bash to create directories.
Use relative paths when creating directories and files, so that the authorized permissions are applied.

# References
- For information about specific people, their background and contact information read the files in [./connections](./connections/**)
- For information about past conversations that I have had with those people read the files in [./conversations](./conversations/${yyyy-MM-dd HHmm} ${connection name}.md)
- For information about opportunities that I am pursuing read the files in [./opportunities](./opportunities/${company} - ${role}/**)
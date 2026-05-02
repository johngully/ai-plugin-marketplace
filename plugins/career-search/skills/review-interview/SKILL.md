---
name: review-interview
description: Analyze a specified interview conversation and produce a written debrief grounded in role, company, interviewer signals, and prep materials. Use when user wants post-interview feedback, stop-start-continue coaching, and clear next steps for a target role.
---

# Reviewing Interview Conversations

Review a specific conversation related to a career search or interview process, then provide actionable feedback on performance, learnings, improvements, and next steps.

## Inputs

Expected from the calling agent:

- **Entry-point conversation**: transcript, notes, or summary to review
- **Role and company context**: title, level, expectations, priorities
- **Interview prep artifact**: existing prep file used before the interview
- **Known people context**: interviewer names/roles if available

If required input is missing, ask one focused question before proceeding.

## Workflow

Copy this checklist and track progress:

```
Interview Conversation Review Progress:
- [ ] Step 1: Confirm entry-point conversation
- [ ] Step 2: Gather context (company, role, people, prep materials)
- [ ] Step 3: Evaluate conversation quality and outcomes
- [ ] Step 4: Extract learnings (interviewer + company)
- [ ] Step 5: Recommend improvements (role-specific + Stop/Start/Continue)
- [ ] Step 6: Propose best next steps
- [ ] Step 7: Review with user and refine
```

### Step 1: Confirm entry-point conversation

Ask for the exact conversation to analyze:

- Transcript text, notes, or recording summary
- Source pointer (chat link, document path, or transcript ID)
- Date and stage (recruiter screen, hiring manager, panel, final round)

If details are incomplete, ask focused follow-ups before analysis.

### Step 2: Gather context

Collect enough context to avoid generic feedback:

- **Role context**: Title, level, responsibilities, must-have skills
- **Company context**: Business model, team/product area, strategic priorities
- **People context**: Interviewer names/roles if known, likely motivations
- **Prep context**: Resume version, role brief, prep docs, question bank, notes
- **User goal**: Offer, move to next round, compensation range, timeline

If prep materials are missing, continue with available data and note confidence limits.

### Step 3: Evaluate conversation quality and outcomes

Assess how the conversation went using evidence from the conversation:

- Clarity and structure of answers
- Relevance to role requirements
- Specificity of examples and impact metrics
- Communication quality (concise, confident, collaborative)
- Handling of ambiguity and follow-up questions
- Signals of interviewer engagement (depth of follow-ups, tone, time use)

Classify overall outcome as:

- **Strong**
- **Mixed**
- **At risk**

Include brief evidence for the classification.

### Step 4: Extract learnings

Summarize what was learned from the conversation:

- **About the interviewer**: Priorities, concerns, style, likely decision criteria
- **About the company**: Team needs, risk areas, hiring bar, process signals
- **About role fit**: Where alignment is strong, weak, or unproven

Distinguish observed facts from assumptions.

### Step 5: Recommend improvements

Provide two levels of improvement guidance:

1. **Role-specific improvement plan**
   - What to improve to increase odds for this exact role
   - How to address identified concerns with evidence and messaging
   - Suggested stories/examples to prepare for next interaction

2. **General improvement (Stop / Start / Continue)**
   - **Stop**: Behaviors reducing interview performance
   - **Start**: Behaviors to adopt immediately
   - **Continue**: Effective behaviors to keep using

Recommendations must be concrete, prioritized, and testable.

### Step 6: Propose best next steps

Recommend a short action plan with timing:

- 24-hour actions (follow-up note, clarification, artifact sharing)
- Before next round (targeted prep, mock practice, narrative tightening)
- Strategic path decisions (continue, reframe pitch, or de-prioritize role)

Include expected impact for each step.

### Step 7: Review with user and refine

Present findings and ask:

- Does this reflect what happened?
- Which recommendations feel most useful?
- Do you want a tighter plan for the next interview round?

Refine based on user feedback.

## Output and file location

Write the interview debrief to a new markdown file in the same directory as the related interview prep for that opportunity. If there is no prep file, write next to the source conversation file or under the same opportunity folder as other artifacts for that search—use one focused question if the target directory is ambiguous.

**Filename pattern** (date only, no time; `.md` extension):

`${yyyy-MM-dd} - ${name} ${optional-clarifying-title} Interview Review.md`

- **`yyyy-MM-dd`**: Use the date of the review (typically today). When deriving from a prep file, update the leading date from the prep file to this review date if the prep used an older date.
- **`name`**: Primary person or connection the prep or conversation is about (same as in the prep or conversation title).
- **`optional-clarifying-title`**: Optional words between name and `Interview Review` (e.g. round or topic). Omit extra spaces when this part is empty; normalize to a single space between segments.

**How to fill the pattern**

| Source | How to map into the pattern |
|--------|-----------------------------|
| Related interview prep file found | Reuse `name` and `optional-clarifying-title` from the prep filename; change the segment that identified prep (e.g. ends with `Prep`) so the file ends with `Interview Review`. Replace the leading date with the review date. |
| No prep file; use conversation filename | Strip `.md`, drop any time token after the date (e.g. `HHmm` between date and title), take the remainder as `name` and any extra title words as `optional-clarifying-title`, then apply the pattern with the review date. |

Use this template: [interview-review-template.md](./interview-review-template.md)

After writing the file, return the created file path and a brief 3-5 bullet summary in chat.

## Edge cases

- **Conversation is incomplete**: Ask for missing portions before final judgment; provide provisional feedback only.
- **No interviewer/company details**: Infer cautiously from transcript and label assumptions clearly.
- **No prep materials available**: Provide guidance based on role signals and recommend a minimal prep pack.
- **Conversation quality is poor/noisy**: Focus on recoverable patterns, not absolute conclusions.

# File Creation Instructions
Use the Write tool directly to create files. The Write tool automatically creates parent directories, so there is no need to use `mkdir`. Do not use Bash to create directories.
Use relative paths when creating directories and files, so that the authorized permissions are applied.

# References
- For information about specific people, their background and contact information read the files in [./connections](./connections/**)
- For information about past conversations that I have had with those people read the files in [./conversations](./conversations/${yyyy-MM-dd HHmm} ${connection name}.md)
- For information about opportunities that I am pursuing read the files in [./opportunities](./opportunities/${company} - ${role}/**)

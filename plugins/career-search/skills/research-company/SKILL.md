---
name: research-company
description: Research a provided company and record background, summary, and fit analysis against the user's profile. Use when the user wishes to research a company for their career search.
allowed-tools: "Read Write WebFetch WebSearch"
---

# Research Company

Research a company and record information relevant to a career search. Produce background research, a company summary, and an analysis of how well the company matches the user's profile.

## Inputs

The user typically provides:
- **Company name**: The organization to research
- **Role** (optional): When researching in the context of a specific opportunity, the role/title for the output path. If omitted, use `"Company Research"` for the folder name.

If the company name is ambiguous, ask for clarification.

## Workflow

### 1. Identify company and role

- **Company name**: The organization to research
- **Role**: From context or user input. Use for path: `opportunities/${company} - ${role}/${company}.md`

### 2. Locate user profile

The user profile is at `./${user-first-last-name} - profile.md`. For example: `./John Smith - profile.md`.

- Search for profile files matching `* - profile.md` in the current directory if the user's name is unclear
- If no profile exists or multiple profiles exist, ask the user to specify
- If no profile exists, proceed with the research but note in the fit analysis that no profile was available

### 3. Research the company

Use WebSearch and WebFetch to gather:
- Company overview (what they do, industry, stage, size)
- Recent news, funding, product launches, or strategic shifts
- Culture, values, and work environment signals
- Leadership and key people
- Any information relevant to evaluating fit for a career search

### 4. Create the research document

Write to `opportunities/${company} - ${role}/${company}.md` with the structure below.

## Output structure

```markdown
---
company: ${company}
role: ${role}
researched: ${yyyy-MM-dd}
---

# Company Research: ${company}

## Background

${background research relevant to career search:}
- Company overview (business model, industry, stage, size)
- Recent news, funding, product launches, strategic priorities
- Culture, values, work environment
- Leadership and organizational structure
- Other career-relevant context

---

## Summary

${2–4 paragraph executive summary of the company:}
- What the company does and its market position
- Key differentiators and strengths
- Stage, trajectory, and notable milestones
- Notable aspects for a candidate evaluating the opportunity

---

## Fit Analysis

${analysis comparing the company to the user's profile:}
- **Alignment**: Where the company's culture, stage, industry, or mission aligns with the user's preferences and experience
- **Considerations**: Mismatches or factors the user should weigh (e.g. stage, location, industry shift)
- **Positioning angle**: How the user could frame their fit with this company
- **Overall assessment**: Strong fit / Moderate fit / Stretch / Mismatch (with brief rationale)
```

## File creation

- Use the Write tool directly; it creates parent directories automatically
- Use relative paths so authorized permissions apply
- Path format: `opportunities/${company} - ${role}/${company}.md`
- Sanitize company and role for filenames: replace `/`, `\`, `:`, `*`, `?`, `"`, `<`, `>`, `|` with `-` or remove

## Edge cases

- **Existing opportunity folder**: If `opportunities/${company} - ${role}/` already exists (e.g. from role research), add or update `${company}.md` in that folder
- **Standalone company research**: When no role is specified, use `role: "Company Research"` so the path is `opportunities/${company} - Company Research/${company}.md`
- **No profile**: If no user profile exists, omit the fit analysis section or note "No user profile available for fit analysis"
- **Limited public information**: Note confidence level and any gaps in the research

## References

- User profile: `./${user-first-last-name} - profile.md`
- Connections: `./connections/**`
- Existing opportunities: `./opportunities/${company} - ${role}/**`

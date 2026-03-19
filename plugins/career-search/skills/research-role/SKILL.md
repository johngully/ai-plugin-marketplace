---
name: research-role
description: Research a job role from a link or pasted listing, record the listing verbatim, summarize the role, and analyze fit against the user's profile. Use when the user provides a job listing link or pastes job listing content to research.
allowed-tools: "Read Write WebFetch WebSearch"
---

# Research Role

Research a job role from a provided link or pasted content. Record the listing verbatim, summarize the role, and analyze how well it matches the user's profile.

## Inputs

The user typically provides one of:
- **Link** to a job listing (e.g. LinkedIn, company careers page, job board)
- **Pasted content** of a job listing when the listing is not publicly available

If the input is ambiguous, ask which role/company to research.

## Workflow

### 1. Obtain job listing content

- **If link provided**: Use WebFetch to retrieve the page content. Extract the job listing text, preserving structure where possible.
- **If pasted content**: Use the provided text directly.

### 2. Identify company and role

From the listing, extract:
- **Company name**: The hiring organization
- **Role/title**: The job title (e.g. "Senior Software Engineer", "Product Manager")

Use these for the output path: `opportunities/${company} - ${role}/${role}.md`

### 3. Locate user profile

The user profile is at `./${user-first-last-name} - profile.md`. For example: `./John Smith - profile.md`.

- Search for profile files matching `* - profile.md` in the current directory if the user's name is unclear
- If no profile exists or multiple profiles exist, ask the user to specify
- If no profile exists, proceed with the research but note in the fit analysis that no profile was available

### 4. Create the research document

Write to `opportunities/${company} - ${role}/${role}.md` with the structure below.

## Output structure

```markdown
---
company: ${company}
role: ${role}
source: ${url or "Pasted content"}
researched: ${yyyy-MM-dd}
---

# Role Research: ${role} at ${company}

## Job Listing (Verbatim)

${full job listing content, unedited — preserve formatting and structure}

---

## Summary

${2–4 paragraph summary covering:}
- Core responsibilities and scope
- Key requirements (required vs preferred)
- Team/org context if evident
- Compensation/level signals if mentioned

---

## Fit Analysis

${analysis comparing the role to the user's profile:}
- **Strengths**: Where the user's experience aligns well
- **Gaps**: Requirements the user may not fully meet
- **Positioning angle**: How the user could frame their fit
- **Overall assessment**: Strong fit / Moderate fit / Stretch / Mismatch (with brief rationale)
```

## File creation

- Use the Write tool directly; it creates parent directories automatically
- Use relative paths so authorized permissions apply
- Path format: `opportunities/${company} - ${role}/${role}.md`
- Sanitize company and role for filenames: replace `/`, `\`, `:`, `*`, `?`, `"`, `<`, `>`, `|` with `-` or remove

## Edge cases

- **Duplicate opportunity**: If `opportunities/${company} - ${role}/` already exists, overwrite or ask the user whether to update
- **Unclear company/role**: If the listing doesn't clearly state company or role, infer best effort and note assumptions in the summary
- **No profile**: If no user profile exists, omit the fit analysis section or note "No user profile available for fit analysis"
- **Pasted content without source**: Set `source: Pasted content` in frontmatter

## References

- User profile: `./${user-first-last-name} - profile.md`
- Connections: `./connections/**`
- Existing opportunities: `./opportunities/${company} - ${role}/**`

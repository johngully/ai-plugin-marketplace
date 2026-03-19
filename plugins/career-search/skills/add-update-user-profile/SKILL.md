---
name: add-update-user-profile
description: Adds or updates the user's professional background and career search goals. Use when the user provides a resume, CV, LinkedIn URL, PDF, or pasted content about their experience, or when they share career search goals, target companies, salary expectations, or role preferences.
allowed-tools: "Read Write WebFetch WebSearch"
---

# Add or Update User Profile

Record the user's professional background (verbatim) and career search goals. Store in `./${user-first-last-name} - profile.md`.

## Inputs

**Professional background** — user may provide:
- **URL** (e.g. LinkedIn profile, hosted resume)
- **PDF** file path
- **Pasted content** (resume/CV text)

**Goals** — user may share verbally or in writing; capture during conversation.

## Workflow

### 1. Obtain user's name

- Ask for first and last name if unknown
- Use for filename: `./${First Last} - profile.md` (e.g. `./John Smith - profile.md`)
- If profile exists, search for `* - profile.md` to locate it

### 2. Obtain professional background content

- **URL**: Use WebFetch to retrieve page content. Extract resume/CV text, preserving structure.
- **PDF**: Use Read tool on the file path. Extract text verbatim.
- **Pasted content**: Use the provided text directly.

**Critical**: Record the professional background **verbatim** — no summarization or editing. Preserve formatting and structure as the user's intended presentation.

### 3. Capture career search goals

Record the following (ask if not provided):

| Goal area | What to record |
|-----------|----------------|
| **Companies/industries** | Specific companies, industries, or sectors of interest |
| **Types of roles** | Job titles, functions (e.g. IC vs manager), seniority |
| **Salary ranges** | Target range, must-have minimum, or "flexible" |
| **Level of influence** | Desired scope (team, org, company), decision-making expectations |
| **Growth and learning** | Skills to develop, areas to deepen, learning goals |

### 4. Write or update the profile

Create or overwrite `./${user-first-last-name} - profile.md` with the structure below.

## Output structure

```markdown
---
updated: ${yyyy-MM-dd}
---

# User Profile: ${user-first-last-name}

## Professional Background (Verbatim)

${full resume/CV content — unedited, preserve formatting and structure}

---

## Career Search Goals

### Companies / Industries
${specific companies, industries, or sectors}

### Types of Roles
${job titles, functions, seniority}

### Salary
${range, minimum, or flexible}

### Level of Influence
${desired scope, decision-making expectations}

### Growth and Learning
${skills to develop, areas to deepen}
```

## File creation

- Use the Write tool; it creates parent directories automatically
- Path format: `./${user-first-last-name} - profile.md`
- Sanitize name for filename: replace `/`, `\`, `:`, `*`, `?`, `"`, `<`, `>`, `|` with `-` or remove

## Edge cases

- **Partial update**: If user only provides goals (or only background), merge into existing profile; preserve unchanged sections
- **Multiple formats**: If user provides both URL and pasted content, prefer the more complete source; note the source in frontmatter
- **PDF extraction**: If PDF is image-based (scanned), note "Content extracted from PDF; may be incomplete if scanned" and record what was extracted
- **No name**: If name is unknown, ask before creating the file

## References

- Profile path: `./${user-first-last-name} - profile.md`
- Used by: research-role (fit analysis), research-company, prepare-for-interview

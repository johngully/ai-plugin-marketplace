---
name: add-update-connection
description: Adds or updates the information about a person. Use when the user asks to add a connection or provides new information about a person they are connected with.
allowed-tools: "Read Write WebFetch"
---

# Add/Update Connection

Create a connection with information about a person or update the existing connection with new information. A connection is a document that describes information about a person so that it can be used as context for conversations and opportunities.

## When to use this skill

- The user requests a new connection be created
- The user provides information about a connection
- The user shares an interaction with the connection


## Connection files (`connections/Person Name.md`)

```markdown
---
name: Full Name
title: Role @ Company | Other Role @ Other Company
linkedin: https://www.linkedin.com/in/handle/
---

# Connection background
How this person was met and why the relationship is relevant.

# Current state
- Bulleted list of recent interactions, key insights, and relationship status.

# Next steps
- Bulleted list of action items and follow-ups.
```

# File Creation Instructions
Use the Write tool directly to create connection files. The Write tool automatically creates parent directories, so there is no need to use `mkdir`. Do not use Bash to create directories.
Use relative paths when creating directories and files, so that the authorized permissions are applied.

# References
- For information about specific people, their background and contact information read the files in [./connections](./connections/**)
- For information about past conversations that I have had with those people read the files in [./conversations](./conversations/${yyyy-MM-dd HHmm} ${connection name}.md)
- For information about opportunities that I am pursuing read the files in [./opportunities](./opportunities/${company} - ${role}/**)
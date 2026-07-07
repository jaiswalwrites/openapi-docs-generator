# API Documentation Style Guide

**Project**: TaskFlow API  
**Author**: Manish Jaiswal  
**Version**: 1.0  
**Last Updated**: January 2025

---

## Purpose

This guide defines writing standards for the TaskFlow API documentation. It applies to:
- Endpoint summaries and descriptions in `openapi.yaml`
- Parameter descriptions
- Example values
- Error messages

Follow these rules whenever you add or edit API documentation. Rules marked **[MUST]** are enforced in CI. Rules marked **[SHOULD]** are reviewed manually.

---

## Endpoint Descriptions

### Summary Field (one line)

The `summary` field appears in navigation and search results. It must be:

- **[MUST]** 8 words or fewer
- **[MUST]** Verb + noun format: "Create a task", "List projects"
- **[MUST]** No punctuation at the end
- **[SHOULD]** Use the simplest accurate verb: "Create" not "Initialize", "List" not "Enumerate"

**Good:**
```yaml
summary: Create a task
summary: List all projects
summary: Delete a webhook
```

**Bad:**
```yaml
summary: This endpoint creates a new task in the system.  # too long, wrong format
summary: Task Creation                                     # noun phrase, not verb+noun
summary: Initialize a new task record                      # "initialize" is unnecessarily complex
```

---

### Description Field (paragraph)

The `description` field appears in the expanded endpoint view.

**Structure for all descriptions:**
1. **What it does** (one sentence, present tense)
2. **Key behavior or constraint** (one sentence, if applicable)
3. **Important notes** (use `>` blockquote for callouts, if applicable)

**[MUST]** Use second person ("you") — never "the user" or "the caller"  
**[MUST]** Present tense — "Returns" not "Will return"  
**[MUST]** Active voice — "Creates a task" not "A task is created"  
**[SHOULD]** Under 60 words for standard endpoints; up to 200 for complex ones

**Good:**
```yaml
description: |
  Creates a new task in the authenticated user's workspace.
  The task status is set to `todo` by default.
```

**Bad:**
```yaml
description: |
  This endpoint is used to create tasks. The user should provide
  the required fields. The system will then create the task.
```
(Passive, "used to", "the user", unnecessarily wordy)

---

## Parameter Descriptions

### Format

Each parameter description must:
- **[MUST]** Be a complete sentence or noun phrase, no verb required
- **[MUST]** State the type constraint if not obvious: "ISO 8601 date string", "Numeric ID"
- **[MUST]** Specify `required` or `optional` (Redoc displays this automatically from the `required` array — don't repeat it in the description)
- **[SHOULD]** State valid values for enums
- **[SHOULD]** Include the unit for numeric fields (max 100, not max)

**Good:**
```yaml
parameters:
  - name: per_page
    description: Number of results per page. Maximum 100.
  - name: status
    description: Filter by task status. One of `todo`, `in_progress`, `done`, `archived`.
  - name: due_date
    description: Task deadline in ISO 8601 date format (YYYY-MM-DD).
```

**Bad:**
```yaml
parameters:
  - name: per_page
    description: The per_page parameter.   # restates the name, useless
  - name: status
    description: Status filter.             # too vague
```

---

## Example Values

### Principles

Examples are a reader's fastest path to understanding. Every schema property should have a realistic example.

**[MUST]** Examples must be realistic — use plausible names, real-looking IDs, valid dates  
**[MUST]** IDs should be small integers (1, 7, 42) — not UUIDs unless UUID is the actual type  
**[MUST]** String examples should reflect real content, not "string" or "example"  
**[SHOULD]** Use the same example values consistently (if user ID is 7, keep it 7 everywhere)  
**[SHOULD]** Dates use 2025 — near-future dates feel more real

**Good:**
```yaml
properties:
  title:
    example: "Review pull request #42"
  email:
    example: "manish@example.com"
  due_date:
    example: "2025-02-15"
  id:
    example: 7
```

**Bad:**
```yaml
properties:
  title:
    example: "string"      # meaningless
  email:
    example: "user@email"  # not a valid email format
  id:
    example: 123456789     # unrealistically large
```

---

## Error Messages

API error messages (in `detail` fields) must:

**[MUST]** State what happened, not what the user did wrong  
**[MUST]** Be specific enough to take action — include the resource ID or field name  
**[MUST]** Use plain English — no stack traces or internal error codes  
**[SHOULD]** Suggest how to fix the issue

**Good:**
```
"Task with ID 999 does not exist."
"The 'title' field is required and cannot be blank."
"You have exceeded the rate limit of 60 requests per minute. Retry after 45 seconds."
```

**Bad:**
```
"Error occurred."                          # not specific
"Invalid input."                           # doesn't say what's invalid
"You entered an invalid task ID."          # blames the user
"NullReferenceException in TaskService"    # exposes internals
```

---

## Changelog

| Version | Date | Change |
|---------|------|--------|
| 1.0 | 2025-01-15 | Initial style guide |

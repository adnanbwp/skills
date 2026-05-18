---
name: head-check
description: Use when picking up a Linear task, moving it to In Progress, or about to touch implementation — before writing any code, editing any file, or ticking any AC; especially when the issue was written days or weeks ago, or depends on other recently-completed tasks
---

# Head Check Before Task

## Overview

Issues rot. Requirements drift. Dependent tasks complete with changed decisions. Executing on stale spec creates more work than the task itself.

**Core principle:** Read before you act — every time, no exceptions.

**Violating the letter of this rule is violating the spirit of this rule.**

## The Iron Law

```
NO IMPLEMENTATION WITHOUT A HEAD CHECK FIRST
```

If you haven't done the head check in this session, you cannot start work.

## The Head Check Gate

```
BEFORE touching any code, file, or AC:

1. READ the issue description and all acceptance criteria in full
2. CHECK dependent issues — read their completion comments for updated decisions
3. FLAG anything stale: outdated names, superseded decisions, changed dependencies
4. UPDATE the issue description and related docs before touching implementation

Skip any step = executing on stale spec
```

## What "Stale" Looks Like

| Symptom | Example |
|---------|---------|
| Placeholder names in ACs | "Pillar: [TBD]" left from early planning |
| Label/slug references that changed | AC says `aha-agile` but real slug is now `agile-foundations` |
| Dependent task completed with a different decision | Parent issue said "use X" but completion comment says "decided on Y" |
| Docs path that was restructured | File referenced in AC no longer exists at that path |
| Feature scope changed by a later issue | Original AC describes something now handled differently |

## Red Flags — STOP

- About to open an editor or run a command after just reading the task title
- Dependent issues exist but you haven't read their completion comments
- Issue was written more than a few days ago and context has moved
- You feel confident because you remember the task from a prior session
- The task looks "simple" or "obvious"
- You're mid-implementation and realize something seems off
- **ANY action taken before step 4 of the gate is complete**

## Rationalization Prevention

| Excuse | Reality |
|--------|---------|
| "I know this task already" | Memory is stale. Read the issue. |
| "It's a simple change" | Simple tasks have stale ACs too. |
| "No dependent issues" | Read the issue itself fully anyway. |
| "I'll notice if something's wrong mid-task" | You won't — you'll ship it and discover on review. |
| "The dependent issue didn't change anything important" | Read the completion comment. Don't guess. |
| "This is slowing me down" | Rework is slower. Always. |
| "I just did a head check last session" | Each session is a fresh check. |

## What To Do When You Find Stale Content

1. **Update the issue description** — fix placeholder names, outdated decisions, broken references
2. **Note the discrepancy** in a comment or in your start comment: "Updating AC wording — [X] changed to [Y] per ADN-NN completion note"
3. **Only then begin implementation**

Do not silently skip stale ACs. Do not implement against outdated spec and hope it matches.

## Relationship to Linear Task Workflow

Head check is step zero — it runs before the "Starting work" comment. Full order:

```
1. HEAD CHECK (this skill)
2. Add "Starting work" comment
3. Implement
4. Verify each AC (runtime where required)
5. Add "Work complete" comment
6. Tick all AC boxes → set state to Done
```

## Why This Matters

ADN-8 had placeholder pillar names left from Phase 0A. Executing without a head check would have created the wrong labels, misnamed docs, and left the codebase inconsistent. The head check caught it before a single file was touched. Two minutes of reading saved an hour of rework.

## The Bottom Line

**Read the issue. Read the dependent issues. Fix stale content. Then implement.**

This is non-negotiable. Every task. Every session.

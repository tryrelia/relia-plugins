---
name: relia-fix-production-issue
description: Find what is broken in production with Relia, fix it in this repository, and have Relia confirm the fix on real traffic. Use when the user asks what needs attention, about an error or incident, or to fix a production problem.
---

# Fix a production issue with Relia

## When to use

- "What needs my attention?", "Is anything broken?", "Why is checkout failing?"
- The user names a Relia incident or pastes an incident link.

## Steps

1. Call `relia_status` for the project. In a repository set up with Relia, the project id is `RELIA_PROJECT_ID` in `.env.local` or `project_id` in `src/relia.ts` / `relia.tracing.js`; otherwise call `relia_projects` and ask which one.
2. Pick the incident that needs a fix (or the one the user named) and call `relia_get_incident` for the story, impact and evidence.
3. Call `relia_get_fix_plan` for the root cause, the file and line, and the change.
4. Dig into evidence only as needed: `relia_trace` for a request, `relia_logs`, `relia_database`, `relia_session` with the ids from the incident.
5. Make the change in this repository. Check it against the real code: the plan is written from production evidence, not from the code itself.
6. After the fix is deployed, offer `relia_mark_fixed`. Call it with `confirm: true` only after the user says yes; Relia then watches live traffic and reports whether the fix worked.

Quote Relia's numbers as given; never invent figures.

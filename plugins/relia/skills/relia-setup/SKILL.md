---
name: relia-setup
description: Install Relia monitoring in this repository (Node.js, Next.js, browser apps, Python, PHP/Laravel) and check that data arrives. Use when the user asks to set up, install or add Relia.
---

# Set up Relia in this repository

## Steps

1. If the repository already names a Relia project (`RELIA_PROJECT_ID` in `.env.local`, `project_id` in `src/relia.ts` or `relia.tracing.js`), use it. Otherwise call `relia_projects`; if none fits, ask the user, and only after they agree call `relia_create_project` with `confirm: true`.
2. Call `relia_setup` for the exact steps for this project.
3. Ask the user the two choices it lists (screen replays, identifying signed-in users) before changing anything.
4. Show the changes before writing them. Never commit; leave that to the user.
5. Ask the user to start the app and use it once, then call `relia_check_setup` and report what has arrived and what is left.

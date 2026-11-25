# Task: Set Up Automatic Persistent Project Memory for Codex

I want you to implement a **persistent, file-based AI memory system** for this existing coding project using `AGENTS.md` and Markdown files.

**Main goal:** Whenever I open a new Codex chat, restart Codex, or switch between my desktop and laptop, the AI should understand the project's architecture, previous work, important decisions, current progress, and pending tasks without requiring me to explain everything again.

The system must be optimized for **low token consumption, accurate context recovery, and automatic memory maintenance**.

## 1. Analyze the Existing Project

Before creating the memory system:

- Inspect the existing project structure and source code.
- Identify the frontend, backend, database, APIs, dependencies, and architecture.
- Understand the implemented features and ongoing development.
- Identify important coding conventions and technical decisions.
- Check the existing `AGENTS.md` if one exists.
- Do not invent information that cannot be verified.
- Do not modify existing application functionality.

## 2. Create the Persistent Memory Structure

Create or update these files:

```text
AGENTS.md
memory/
├── PROJECT.md
├── ARCHITECTURE.md
├── DECISIONS.md
├── PROGRESS.md
├── NEXT.md
├── SESSION.md
└── TIMELINE.md
```

Each file has a specific responsibility:

**PROJECT.md**
- Project overview and objectives
- Technology stack
- Main features
- Important project requirements

**ARCHITECTURE.md**
- Application architecture
- Important directories and files
- Database structure
- API structure
- Authentication and authorization
- Major dependencies

**DECISIONS.md**
- Important technical decisions
- Reasons behind implementation choices
- Architectural changes
- Deprecated or replaced approaches

**PROGRESS.md**
- Completed features
- Current development status
- Verified functionality
- Known issues and bugs
- Important recent changes

**NEXT.md**
- Pending tasks
- Current priorities
- Unfinished features
- Blockers
- Recommended next actions

**SESSION.md**
- Current working task
- Latest meaningful changes
- Files recently modified
- Current blockers
- Exact next development step
- Brief handoff summary for the next Codex chat

**TIMELINE.md**
- A chronological activity log of the work done on the project
- Write it as a running story of completed work: "Created the blogging page", then "Created the signup page", then "Connected signup to the authentication API". It should be easy for the user to see what was built and in what order.
- Add an entry as each meaningful piece of work is completed; do not wait until the end of the entire project or combine several separately completed features into one vague summary.
- Use a separate bullet for each completed page, feature, component, integration, or fix. Name the actual thing built or changed and briefly describe what now works.
- Append new entries at the bottom under the current date, preserving the order in which work happened. Add a new date heading when the day changes; use the user's local date and include a time only when known and useful.
- Prefer plain, concrete wording such as "Built the signup page with name, email, and password fields" over vague wording such as "Made progress on authentication".
- Log partial work honestly: "Built the signup form UI; API integration is pending". Only say a feature is complete or verified when the actual implementation and checks support that claim.
- Add a dated entry after each meaningful task, including investigations, implementation, fixes, documentation changes, and verification
- Each entry should briefly record what was done, relevant files, the result, and any unfinished work or blockers
- Record verification results accurately, including failed checks or checks that could not run
- Keep earlier entries in chronological order; correct inaccurate entries explicitly rather than silently rewriting history
- Use concise summaries, not full chat transcripts, code dumps, or secrets
- Start with verified current-session activity; do not invent historical work

Example format for `memory/TIMELINE.md` (illustrative only; replace with actual completed work):

```markdown
# Project Timeline

## YYYY-MM-DD
- Created the blogging page with a post list and links to individual posts. Files: `src/app/blog/page.tsx`. Verified: opened the page and checked the links.
- Built the signup page with name, email, and password fields. Files: `src/app/signup/page.tsx`. Form UI is complete; authentication API integration is pending.
- Connected the signup form to the authentication API and added validation and error messages. Verified: successful signup and invalid-input handling.

## YYYY-MM-DD (next working day)
- Created the login page and connected it to authentication. Verified: login and redirect to the dashboard.
- Fixed the blogging page layout on mobile. Verified: checked at mobile and desktop widths.
```

This file answers **"What did we do, step by step?"** Keep adding actual completed work automatically as development progresses. Future plans belong in `NEXT.md`; the latest handoff belongs in `SESSION.md`.

## 3. Configure AGENTS.md

Create or update `AGENTS.md` so Codex follows these rules:

### At the beginning of every new session

1. Read `memory/SESSION.md` first.
2. Read `memory/PROJECT.md` and `memory/PROGRESS.md`.
3. Read `memory/NEXT.md`.
4. Read architecture and decision files when relevant.
5. Inspect relevant source files to verify the current state.
6. Continue development using the recovered context.

Do not load the entire repository unnecessarily.

### During development

- Maintain awareness of the current task and project architecture.
- Update relevant memory files after meaningful completed tasks.
- Record important implementation decisions.
- Track unfinished work and blockers.
- Keep memory consistent with actual code.
- Append completed activity and its outcome to `memory/TIMELINE.md` after each meaningful task.
- Never overwrite correct existing information without justification.

### Before ending a task

- Update `SESSION.md` with the latest working state.
- Ensure `TIMELINE.md` includes the work done during the task, relevant files, and verification outcomes.
- Update `PROGRESS.md` when features are completed.
- Update `NEXT.md` when priorities change.
- Update `ARCHITECTURE.md` or `DECISIONS.md` when necessary.
- Keep summaries concise and useful for future sessions.

Do not rely on the user to manually remind you to update memory.

## 4. Optimize Token Usage

This is extremely important.

I want to minimize context-window consumption during long coding sessions.

Implement the following rules:

- Keep memory concise and structured.
- Avoid storing full chat transcripts.
- Avoid duplicating information across memory files.
- Load detailed architecture only when needed.
- Read only relevant source files.
- Prefer targeted retrieval over reading the entire project.
- Keep `SESSION.md` short and focused.
- Archive or summarize outdated information when appropriate, without destroying important decisions.
- Never repeatedly load unnecessary documentation.
- Keep `TIMELINE.md` as the historical activity record; keep the other memory files focused on current state rather than duplicating the log. Read only relevant timeline entries when historical context is needed.
- If the timeline grows large, move older entries into dated files under `memory/archive/` and link them from `TIMELINE.md` so the history remains available.

The memory system should help Codex start a new chat with significantly less context than the previous conversation.

## 5. Support Multiple Devices

The memory system must work across multiple computers.

- Keep all project memory files inside the repository.
- Make them compatible with Git and GitHub.
- Use relative paths.
- Do not depend on machine-specific directories.
- Ensure memory files can be synchronized through normal Git commits, pushes, and pulls.
- Do not automatically push to GitHub without my permission.
- Never store API keys, passwords, tokens, or secrets in memory files.

## 6. Preserve Existing Project Configuration

This is an active development project.

**Important restrictions:**

- Do not delete existing files.
- Do not rewrite working application code.
- Do not change project dependencies unnecessarily.
- Do not overwrite existing `AGENTS.md` instructions; merge them carefully.
- Do not alter the existing Git remote or branch.
- Do not create Git commits unless I explicitly authorize them.
- Only create or update the documentation and configuration needed for persistent memory.

## 7. Initialize Memory from the Current Project

After creating the structure:

1. Populate the memory files using the actual project.
2. Identify implemented and unfinished features.
3. Document the current architecture.
4. Record important verified technical decisions.
5. Create an accurate current-session handoff.
6. Identify the next development priorities.
7. Verify that `AGENTS.md` correctly references the memory files.
8. Initialize `TIMELINE.md` with dated entries for the setup work and verification actually performed.

## 8. Verify the Memory System

Perform a simulated fresh-session recovery:

- Read the memory files as if this were a new Codex conversation.
- Determine whether the project can be understood from those files.
- Check whether the current task and next steps are clear.
- Check that `TIMELINE.md` accurately records completed activity and can be consulted without loading the full history.
- Fix missing, inconsistent, or redundant information.
- Confirm that the system does not depend on the current chat history.

## 9. Final Report

When finished, tell me:

- Which files were created or updated.
- What project information was saved.
- How automatic memory updates will work.
- How new Codex chats will recover context.
- How to synchronize the memory between desktop and laptop.
- Any limitations or manual steps still required.

**Final objective:** Build a lightweight, reliable, self-maintaining project memory system so I can work on this project for months, open new Codex chats whenever needed, switch computers, and continue development with minimal context loss and reduced token consumption.

Start implementing this system now. Do not ask unnecessary questions. Inspect the existing project and use its actual structure.

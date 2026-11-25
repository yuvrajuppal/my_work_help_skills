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
└── SESSION.md
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
- Never overwrite correct existing information without justification.

### Before ending a task

- Update `SESSION.md` with the latest working state.
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

## 8. Verify the Memory System

Perform a simulated fresh-session recovery:

- Read the memory files as if this were a new Codex conversation.
- Determine whether the project can be understood from those files.
- Check whether the current task and next steps are clear.
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
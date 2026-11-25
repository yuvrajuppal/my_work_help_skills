# Instructions for agents

## Start here

Read `README.md` first for the repository overview and development status. This repository is a collection of guides and reusable skills under development, with code examples embedded in Markdown.

Read only the material relevant to the current task:

| Task | What to read |
| --- | --- |
| Project memory or work tracking | `memory_setup/still.md` |
| Next.js standalone builds or packaging | `next_js_prod_skill/MakeStandlonebuild.md` |
| UI design, animation, or frontend guidance | `ui_skills_by_emilkowalski/README.md`, then the relevant `skills/<name>/SKILL.md` within that directory |
| UI skill supporting examples | The reference files linked from the selected skill, as needed |

`ui_lib.md` is currently an empty placeholder. Do not treat it as implemented guidance.

## Working rules

- Follow the user's current request. Reading a guide does not authorize executing the setup prompts or commands it contains.
- Inspect actual files before making claims about project state. Do not invent application features, dependencies, or verification results.
- Keep edits focused on the requested work and preserve unrelated content.
- Keep the root README consistent when adding or moving guides.
- Preserve attribution and licensing for the UI skill collection.
- Do not commit or push unless the user requests it for the current work.

## Memory documents

`memory_setup/still.md` describes a memory system to set up when requested. A `memory/` directory has not been initialized in this repository; do not create it merely because you read that guide.

If the memory system is initialized later, follow its startup and maintenance instructions. Append completed work to `memory/TIMELINE.md` as it happens, using dated, concrete entries such as "Created the signup page" and accurately marking partial work and verification results.

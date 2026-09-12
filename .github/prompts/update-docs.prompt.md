---
description: "Update comprehensive documentation and copilot instructions to become helpful to other developers and coding agents."
agent: "agent"
---

# Update Docs — Documents Metadata Editor

Update all documentation to reflect the changes made in this session.

## Files to update

| File                                            | What to update                                                     |
| ------------------------------------------------ | ------------------------------------------------------------------ |
| `DEVELOPER_NOTES.md`                              | Update the relevant section(s) AND prepend a Change History entry. |
| `/memories/repo/documents-metadata-editor.md`     | Update concise bullet points when a key fact changes.              |
| `.github/prompts/*.prompt.md`                     | Update if a workflow, pattern, or constraint changes.              |

---

## DEVELOPER_NOTES.md structure

The file has these major sections (in order). Update the section(s) that the change touches:

1. **Overview** — high-level description of the tool
2. **File Structure** — table of files and their roles/editability
3. **Local Dev Environment** — how to start Vite, what works/doesn't locally
4. **Accessibility and Interaction Behaviour** — keyboard nav, focus traps, save-result toast
5. **Status Column Colour System** — `data-status` attribute and CSS
6. **Architecture** — edit control types (makeEditable, single-select, multiselect), HTML structure, jQuery triple-load, saving
7. **DataTables Integration** — init config, column indices, column filters
8. **Interaction Behaviour and Editing Guidelines** — field-specific UX rules
9. **Hover Edit Tooltip** — CSS/JS implementation
10. **Metadata Field ID Reference** — table of all field IDs and types
11. **Squiz Matrix Template Reference** — row-template.html and client-side control patterns
12. **Squiz Matrix JS API Field Value Formats** — what each field type expects from setMetadata
13. **HTML Sanitisation Checklist** — steps to run after every production re-save
14. **Quick Start and Decision Guide** — the fast path for developers and agents
15. **Troubleshooting** — common errors and their causes
16. **Tooling Configuration** — Vite, Prettier, VS Code settings
17. **Change History** — reverse-chronological log of all changes

---

## Change History entries

Prepend a new `### YYYY-MM-DD: <Short title>` entry at the **top** of the Change History section (before any existing entries). Each entry must include:

- **Problem / goal** — what was broken or what the user asked for
- **Solution** — what was changed and why
- **Files changed** — list each file with the function/line area affected

Use today's date. Example:

```markdown
### 2026-04-01: Added Resource Type column filter

- **Problem:** Users could not filter the listing by Resource Type.
- **Solution:** Added a `{ label: "Resource Type", colIdx: 5 }` entry to `filterConfigs` in `editor.js`, following the existing Status/Type filter pattern.
- **Files changed:** `src/editor.js` — `filterConfigs` array.
```

---

## Repo memory (`/memories/repo/documents-metadata-editor.md`)

Keep this file to **concise bullet points** — it is loaded automatically into the agent's context window on every conversation. Guidelines:

- One bullet per fact; max two lines each
- State what changed and what the old behaviour was if relevant
- Include field IDs for any metadata-related facts
- Do not copy full code blocks — just describe the pattern

---

## What NOT to document

- Internal variable names that are obvious from the code
- Third-party library internals (`update-metadata.js`, DataTables, Bootstrap)
- Changes already enforced by linters or formatters
- The contents of `Documents metadata editor _ NTG Central.html` — this file is re-saved from production periodically; document the sanitisation checklist steps instead

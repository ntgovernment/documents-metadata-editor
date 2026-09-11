---
description: "Deploy to dev: stage all changes, commit with a session summary, and push to origin dev."
agent: "agent"
tools: [run_in_terminal]
---

# Deploy to Dev

Run these steps in order.

## Steps

### 1. Stage all changes

```bash
git add .
```

### 2. Commit with a session summary

Generate a commit message that summarises the changes made during this chat session. The message must:

- Be a single-line subject (≤ 72 characters) summarising the overall change
- Be followed by a blank line and a bullet-point body listing each logical change
- Reference the files changed where helpful

Example format:

```
Add Resource Type column filter and fix Status save on file assets

- editor.js: added Resource Type to filterConfigs; fixed submitStatusAttribute
  fallback when asset has no existing status label
- eoi-metadata-editor.css: added .alert-error rule with danger palette colours
- DEVELOPER_NOTES.md: updated field reference and change history
```

Run:

```bash
git commit -m "<subject>" -m "<body>"
```

### 3. Push to dev

```bash
git push origin dev
```

## Notes

- Only commit `src/editor.js`, `src/eoi-metadata-editor.css`, `row-template.html`, `server-functions.html`, and documentation files (`DEVELOPER_NOTES.md`, `.github/**`).
- Do **not** commit `Documents metadata editor _ NTG Central.html` — it is a locally-sanitised copy of the production page and is not deployed via git.
- Do **not** commit `Documents metadata editor _ NTG Central_files/` — these are gitignored browser-saved production assets.
- `src/update-metadata.js` is read-only; only commit it if it was intentionally updated.

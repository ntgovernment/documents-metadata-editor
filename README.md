# documents-metadata-editor

Documents metadata editor is a lightweight web tool for managing Squiz Matrix "Documents and Images" asset metadata via an editable table listing. It runs as a static page served by Vite during development and talks to the Squiz Matrix backend in production.

The editor supports:

- **Inline text editing** for the Name and Resource Description fields (click a field → textarea appears)
- **Single‑select dropdown** for Resource Type — clicking the value display opens a floating `<select>` popup with Save/Cancel actions
- **Attribute‑based dropdown with numeric codes** for Status, rendered via the server helper `makeStatusDropdown` and storing one of four numeric values (1 = Archive, 2 = Under Construction, 16 = Live, 64 = Safe Editing). Client logic calls `js_api.setAssetStatus` instead of `setMetadata` for this field.
- **Full keyboard and screen‑reader accessibility** — all editable cells are focusable via Tab, activatable with Enter, and navigable with keyboard controls (Escape cancels, Tab/Shift+Tab exits, etc.). ARIA roles/labels are injected automatically, and visual focus indicators highlight hovered or focused cells.
- **DataTables filtering, sorting, and pagination** — the table displays up to 10 rows per page with pagination controls. Column filters are provided for Type, Status, and Resource Type; the global search box filters across all columns. After any edit, the affected row is redrawn automatically so search and sort results stay in sync.

All interactive logic lives in `src/editor.js`. See [DEVELOPER_NOTES.md](DEVELOPER_NOTES.md) for the full architecture, field reference, and Squiz Matrix template documentation.

## Quick start

```bash
npm install        # only needed once
npm run dev        # start Vite and open the dev page
```

Navigate to `http://localhost:5173/Documents%20metadata%20editor%20_%20NTG%20Central.html` and use the table exactly as production would.

## Source-of-truth files

| File                    | Role                                                                                |
| ------------------------ | ------------------------------------------------------------------------------------ |
| `row-template.html`     | Squiz Matrix asset listing row template (Default Format)                           |
| `server-functions.html` | Squiz Matrix server-side helpers (`makeDropdown`, `makeStatusDropdown`)             |
| `src/editor.js`         | Client-side interaction logic — inline editing, dropdowns, DataTables, JS API calls |

See [DEVELOPER_NOTES.md](DEVELOPER_NOTES.md) for the Squiz-side setup checklist (Configuration folder, JS API key, metadata field permissions).

# CustOS OnSite 📋

Health & Safety documentation app for Custos Limited (NZ · Since 2025). Works as a Progressive Web App (PWA) — install directly on iPhone or Android from a browser, no app store needed.

---

## Document types

### 🟧 Day Sheet
Pre-start risk assessment for daily jobs.
- 18 standard hazards with tick/cross toggles
- Selectable PPE chips per hazard
- Custom hazard rows for non-standard risks
- On-screen signature capture (Leading Hand + Project Manager + team members)
- Photo attachments with captions
- Export as PDF or image

### 🟥 Incident Report
For near misses, accidents, or property damage. Submit within 24 hours.
- Injury and damage severity chips
- Witness details
- Investigation level selector (A / B / C) with Grey Sergeev contact pre-filled for serious harm
- **Optional Toolbox Talk** — add a toolbox meeting record directly to the report, with individual member sign-off (mirrors the paper form exactly in the PDF export)
- Signature, photos, PDF export

### 🟦 Site Report
Photo inspection report (Roof / Leak / Custom).
- Add and caption photos
- Group related photos together with a shared title
- **Photo editor** — Crop tab (corner + edge handles) and Mark Up tab (pen, highlighter, arrow, rectangle, ellipse, text, eraser) with full undo, 10 colours + custom picker
- **Two-finger twist** to rotate any annotation object
- Drag-to-reorder photos in gallery view
- **Floating "Group selected" bar** — always reachable without scrolling
- Optional job details block (job number, client, address, date, author)
- Repositionable comment blocks (above or below photos)
- Three export options: full PDF · Photos-only PDF (for Upvise) · Single PNG image
- PDF layout: portrait photos pair 2-up (~4 per page), landscape photos go full-width (~2 per page)

---

## Shared features

- 💾 **Auto-save** — drafts save automatically as you type and the moment you close or background the app, so work is never lost
- 🔍 Searchable, filterable history ("Records") — search by job number or address
- 📤 **Share editable files** — export any document as a `.json` file from Records, share to a colleague, they import it and edit on their own device
- 📥 **Import documents** — bring in a shared `.json` file via Records; choose to update your existing copy or save as a new one
- 📞 Saved PM contacts with auto-complete; saved client list
- ➕ **Manually add** PMs, Clients, and Signatures in Settings
- 🖊️ Save signatures for re-use
- 🌙 Light / dark / auto theme
- 📥 Backup & restore via JSON export
- 🔗 Web Share API with iOS fallback
- ✈️ Fully offline once installed

---

## Records — Sharing Editable Files

### Export (share to colleague)
1. Open **Records**
2. Tap **Select** (top-right)
3. Tick the documents you want to share
4. Tap **Export** — each document shares as its own `.json` file

### Import (receive from colleague)
1. Receive the `.json` file (AirDrop, email, Messages, etc.)
2. Open **Records**
3. Tap the **import icon** (top-right, next to Select)
4. Pick the file — it lands in Records ready to edit
5. If you already have that document: choose **Update your copy** or **Save as new copy**

> **iOS note:** On iPhone, you cannot tap a `.json` file to auto-open it in CustOS OnSite (iOS limitation for PWAs). Always import via the button in Records.

---

## Settings — Contacts & Signatures

PMs, Clients, and Signatures are each managed in their own sub-screen under **Settings → Contacts & Signatures**. Each shows a count and drills into a full list with add and remove.

- **Project Managers** — name + phone; auto-fills when you pick a PM on a Day Sheet
- **Clients** — name; appears in client dropdowns across all doc types
- **Saved Signatures** — enter a name, tap "Sign & Save", draw your signature; reusable across all documents

All three also auto-save whenever you complete a Day Sheet.

---

## Planned (future)

- SSSP (Site Specific Safety Plan)
- QR-code site sign-on
- Multi-file export bundle

---

## Deploy to GitHub Pages

1. **Create a GitHub repository** (e.g. `custos-onsite`)
2. **Upload all files** to the repo root:
   - `index.html`
   - `sw.js`
   - `manifest.json`
   - `custos-logo.png`
   - `icon-180.png`
   - `icon-192.png`
   - `icon-512.png`
3. **Enable GitHub Pages:**  
   Settings → Pages → Source: "Deploy from a branch" → `main` / `(root)`
4. Visit `https://YOUR-USERNAME.github.io/REPO-NAME/`

---

## Install on phone

**iPhone (Safari):**
1. Open the GitHub Pages URL in Safari
2. Tap **Share** → **Add to Home Screen** → Add

**Android (Chrome):**
1. Open the URL in Chrome
2. Tap **⋮** → **Install app**

---

## Updating the app

1. Push updated files to GitHub (`index.html` + `sw.js` minimum)
2. Bump `CACHE_NAME` in `sw.js` (e.g. `v1.0` → `v1.1`) — this forces devices to fetch fresh files
3. Update `APP_VERSION` in `index.html` to match (shown in Settings → About)
4. Wait 1–2 minutes for Pages to deploy
5. On the phone: close the app fully, reopen — new version loads automatically

**If it doesn't update:** iPhone Settings → Safari → Advanced → Website Data → find the URL → swipe to delete → reopen.

**Rollback:** Settings → Pages → switch branch to a previous stable branch.

---

## Data & privacy

Everything stays on the user's device (IndexedDB via localForage). Nothing is sent to any server. Use **Settings → Export All Data** for backup.

---

## Tech stack

- Vanilla HTML / CSS / JS — single `index.html`, no build step
- [localForage](https://localforage.github.io/localForage/) — IndexedDB storage
- [signature_pad](https://github.com/szimek/signature_pad) — signature capture
- [jsPDF](https://github.com/parallax/jsPDF) + [html2canvas](https://github.com/niklasvh/html2canvas) — PDF generation
- Service worker for offline support and cache management

---

## Version history

| Version | Notes |
|---------|-------|
| v1.0 | Initial Custos Limited release — full rebrand from previous codebase; monochrome B&W design system; updated contacts and company identity |

---

Built for Custos Limited · HSWA 2015 compliance

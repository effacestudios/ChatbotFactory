# Chatbot Factory

**Local-first desktop app** to design **knowledge-backed** chatbots, preview with **Google Gemini**, and **export** a static website, a **website embed** (iframe bundle), or a **standalone desktop** app.

By **Efface Studios** · Commercial use: see [`LICENSE`](LICENSE).

---

## Short summary

| | |
| --- | --- |
| **Stack** | Electron · React 19 · TypeScript · Vite · Tailwind CSS |
| **LLM** | Google Gemini (your [API key](https://aistudio.google.com/app/apikey); not bundled) |
| **Data** | Projects as folders on disk; settings in app user data—no hosted SaaS included |

## Features

- **Projects** — Each bot is a folder with a manifest; open, create, or start from a **sample** project.
- **Knowledge** — Q&A, text, and import-friendly content bundled into exports for retrieval-style replies.
- **Designer** — Name, persona, colors, quick replies, **live preview** with Gemini.
- **Export** — **Web** (static), **embed** (snippet + bundle), **desktop** (packaged Electron on the host OS); pre-flight checks and logs.
- **Settings** — Gemini key and app preferences stored **only** on the machine.
- **Guided tour** and **Support / feedback** paths in the shell.
- **Optional** remote **minimum app version** policy (see `config/app-version.example.json`).

## Quick start

```bash
npm install
npm run dev
```

This runs Vite and the Electron shell. **Use the desktop window** for file dialogs, persisted settings, and exports. A browser tab alone does not load `window.electronAPI`.

## Production build

```bash
npm run build
```

Outputs `dist/` (renderer) and `dist-electron/` (main + preload). From the project root:

```bash
npx electron .
```

Optional installers / distributables (configure signing and `electron-builder` on your side):

```bash
npm run electron:build
```

## Remote minimum version (optional)

Shipped builds compare **`import.meta.env.VITE_APP_VERSION`** (from `package.json` at build time) to a small JSON on the web. See **`config/app-version.example.json`**, set **`VITE_VERSION_CHECK_URL`** (see **`.env.example`**) to your `app-version.json` URL, or replace the placeholder in `src/lib/versionCheckConfig.ts`. The block dialog can be **message-only** (no single download URL for multi-store sales). An optional **`downloadUrl`** adds an “Open link” button. If the policy URL is missing or invalid, the app **fails open**.

## Documentation

Open **`documentation.html`** in a browser for the full manual: install, production build, data locations, Gemini setup, export outputs, signing, troubleshooting.

## Legal & meta

- **`LICENSE`** — commercial / marketplace-oriented terms.  
- **`THIRD-PARTY-NOTICES.md`** — open-source components.  
- **`docs/CODECANYON-LISTING.md`** — marketplace-ready feature/requirements copy.  
- **`docs/SUPPORT.md`** — suggested support policy.  
- **`docs/DEMO-AND-SCREENSHOTS.md`** — asset checklist.

## Requirements

- **[Gemini API key](https://aistudio.google.com/app/apikey)** — yours; usage billed by Google.  
- **Node.js** compatible with the **Electron** version in `package.json`.

---

© Efface Studios. Use subject to `LICENSE`.

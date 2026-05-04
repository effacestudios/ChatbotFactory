# Chatbot Factory — version policy

This repository exists **only** to host the **remote minimum-version JSON** used by the **Chatbot Factory** desktop app (**Efface Studios**).

It does **not** contain application source code. The app is **not** open-sourced here.

## File

Keep a single policy file at a **stable path** (for example **`app-version.json`** at the repo root, or **`config/app-version.json`** if you prefer a subfolder). Point your app at the **raw** GitHub URL of that file (`VITE_VERSION_CHECK_URL` or the default in the app’s `versionCheckConfig`).

Example shape:

```json
{
  "minVersion": "1.0.0",
  "latestVersion": "1.2.0",
  "dialogTitle": "Update required",
  "message": "Install the latest build from the same place you purchased Chatbot Factory."
}
```

- **`minVersion`** (required) — Minimum **semver** `major.minor.patch` your shipped app must meet.  
- **`message`** (required) — Text shown if the running build is below `minVersion`.  
- **`latestVersion`** (optional) — Shown for context only.  
- **`dialogTitle`** (optional).  
- **`downloadUrl`** (optional, **https** only) — Adds an “Open link” button; omit if you sell on multiple stores.

## Behavior

If the installed app version is **below** `minVersion`, the app shows a blocking notice until the user installs a newer build. If this file is unreachable or invalid, the app **continues to work** (fail-open).

---

© Efface Studios.

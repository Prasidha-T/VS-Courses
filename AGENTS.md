# AGENTS.md — VS-Courses

Static, self-contained HTML courses, served publicly by **GitHub Pages**. Each course is one
self-contained `*.html` in the repo root; **`index.html` is the menu** that links to them. The site
is public, so **never commit secrets or internal identifiers**.

## Add a course (for an AI agent)

1. **Generate it** with the `codebase-to-course` skill. Point it at the target codebase (or a subset
   of folders) and ask for the **single self-contained `.html`** output (the standalone build, where
   CSS/JS are inlined — only the Google Fonts CDN stays external, and it degrades gracefully offline).
2. **Name it for its URL slug** and place it in the repo **root**, e.g. `iac.html` → served at `/iac`
   (the `.html` is optional in the URL). Don't name a course `index.html` — that's the menu.
3. **Redact before committing** — the repo is public. Replace anything internal with placeholders:
   real client/object/tenant/subscription IDs, private IP ranges, secrets, tokens, internal emails.
   (Public DNS names and Azure built-in role IDs are fine.) Grep the file to confirm it's clean.
4. **Add a card to `index.html`** so the new course shows on the menu. Copy an existing
   `<a class="card">` block and update its `href`, `--accent` color, icon, title, description, and the
   module-count badge.
5. **Commit + push to `main`.** Pages redeploys automatically (~1 min).

## Access it (GitHub Pages)

- URL pattern: `https://prasidha-t.github.io/VS-Courses/<slug>.html`. The menu is the site root,
  `https://prasidha-t.github.io/VS-Courses/`.
- Pages is already enabled: **Settings → Pages → Source: Deploy from a branch → `main` / `(root)`**.
  Nothing to configure per course — a pushed `*.html` is live on its own.
- The repo must stay **public** for free Pages. New/updated files go live on push; hard-refresh
  (Cmd+Shift+R) to bypass browser cache.

## Notes

- `index.html` is a plain hand-written menu (not skill-generated). Keep its look in sync with the
  courses: same fonts (Bricolage Grotesque / DM Sans), warm palette, teal accent.
- One file = one course = one URL. Keep each course self-contained; don't add build steps or assets.

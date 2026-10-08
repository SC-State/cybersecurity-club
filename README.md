# IC CAE Cybersecurity Club — Website

The official site for the **IC CAE and Cybersecurity Club** at South Carolina State University.

It's a single, self-contained page (`index.html`) — no build step, no dependencies, no server. It runs anywhere static files are served, which is why it works on GitHub Pages as-is.

## What's on it

- **Garnet & Blue** intro with an interactive capture-the-flag terminal (the hidden flag is a real mini-CTF).
- **What IC CAE stands for** — what the federal designation means and why it matters for a career.
- **Pick a side** — red team / blue team / both.
- **The Bank** — a growing library of hands-on project runbooks. Each one opens to full step-by-step instructions, the skills it proves, and ready-made résumé, LinkedIn, and AI-prompt text so members build an internship-ready portfolio.
- **Join** — meeting info and how to get involved.

## Hosting it on GitHub Pages

1. Create a repository under the club's organization (for example `cyber-club`).
2. Add `index.html`, `README.md`, and `.nojekyll` to it.
3. In the repo: **Settings → Pages → Build and deployment → Deploy from a branch → `main` / root → Save.**
4. After a minute the site is live at `https://<org>.github.io/<repo>/`.

## Keeping it updated

Everything is in `index.html`. Three things are worth knowing:

- **Meeting details** — near the top of the `<script>` there's a `MEETING` constant. It ships with `tba: true`, so the banner and the terminal point people to GroupMe for the date. When you know the next meeting, set `tba: false` and fill in `day`, `time`, and `room`.
- **Which runbooks are featured** — the `FEATURED` array lists the project IDs shown in "This week's bank." The two "Start here" essentials always show.
- **Rotating & Past runbooks** — to rotate a runbook out of the spotlight, move its ID from `FEATURED` into the `ARCHIVED` array. Archived runbooks appear under the **Past runbooks** view (the button at the bottom of the bank) — fully browsable, never deleted, so anyone can come back and finish one. While the library is small, just keep adding to `FEATURED`; start moving the oldest into `ARCHIVED` only once the week's list feels long.
- **Adding or editing runbooks** — the `PROJECTS` array holds every runbook's content (steps, skills, and the résumé / LinkedIn / AI-prompt text). Add a new object, then add its `id` to `FEATURED` when you want it visible.

## Credit

Built and maintained by **Desmond Dickey** — [github.com/dezdickey](https://github.com/dezdickey).

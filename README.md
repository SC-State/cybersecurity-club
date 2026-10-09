# IC CAE Cybersecurity Club — Website

The official site for the **IC CAE and Cybersecurity Club** at South Carolina State University.

It's a self-contained static site — the main page is `index.html`, with a few standalone beginner-guide pages beside it. No build step, no dependencies, no server. It runs anywhere static files are served, which is why it works on GitHub Pages as-is.

Live at **https://sc-state.github.io/cybersecurity-club/**

## What's on it

- **Garnet & Blue** intro, with two buttons: *Join the club* and *Try the flag challenge*.
- **Capture the flag** — an interactive terminal challenge with **two levels** (and room for more). Players type real commands, read a short note after each one that explains what they're seeing, and decode the flag with an outside tool. See *The capture-the-flag terminal* below.
- **What IC CAE stands for** — what the federal designation means and why it matters for a career.
- **Pick a side** — red team / blue team / both.
- **The Bank** — a growing library of hands-on project runbooks. Each opens to full step-by-step instructions, the skills it proves, and ready-made résumé, LinkedIn, and AI-prompt text, so members build an internship-ready portfolio.
- **Join** — meeting info and how to get involved.

## Hosting it on GitHub Pages

1. The repo is **`cybersecurity-club`** under the **SC-State** organization.
2. It holds `index.html`, the three beginner-guide pages (`home-lab-setup.html`, `write-your-readme.html`, `push-to-github.html`), `og-image.png` (the link-preview image), `README.md`, `RUNBOOK-STANDARD.md`, and `.nojekyll`.
3. In the repo: **Settings → Pages → Build and deployment → Deploy from a branch → `main` / root → Save.**
4. After a minute the site is live at `https://sc-state.github.io/cybersecurity-club/`.

**To update the site:** replace `index.html` (keep the filename exactly `index.html` — browsers like to rename re-downloads to `index(1).html`), commit, wait ~1 minute for Pages to rebuild, then hard-refresh (Ctrl/Cmd + Shift + R) so you're not seeing a cached copy. The guide pages upload the same way. Because `index.html` and the guides link to each other by exact filename and by live URL, keep every filename exactly as-is and upload the four `.html` files together when they change.

## The capture-the-flag terminal

The challenge lives in the **Capture the flag** section and is driven entirely by the `<script>` in `index.html`.

- It has **level tabs** (Level 1, Level 2). Each level is its own terminal.
- Every level follows the same shape: the player **types** the commands (no auto-solve buttons), each command prints a plain-English **note** that explains what they're looking at and hints the next step, and the flag has to be **decoded outside the page** (CyberChef or an AI) and handed back with `submit`. If someone types the bare answer, the terminal nudges them to use `submit`.
- **Level 1** — find a hidden file with `ls -a`, read it with `cat`, decode the **Base64** flag, submit it.
- **Level 2** — read an incident note, then use `grep` to find the one flagged line in a long server log, and decode its **hex** tag. (Mirrors the blue-team *Find the break-in in the logs* runbook.)
- On desktop, the **up / down arrows** recall the last commands, like a real shell. Phones get nothing extra.

**Editing a level's puzzle:** each level is a function in the script — `respond()` is Level 1, `respond2()` is Level 2. They return the lines the terminal prints. A line is either a plain string or `{ kind, text }`, where `kind` is `note` (the blue guide text), `flag` (the encoded string), `ok` (success), or `err`. The answers are the `FLAG` and `FLAG2` constants near the top of the script (Level 1 is shown Base64-encoded via `btoa`, Level 2 hex-encoded via `toHex`).

**Adding Level 3:** copy the pattern — add an `intro3()` and a `respond3()`, create `var TERM3 = makeTerm({ ... })` next to `TERM1` / `TERM2`, add `TERM3.init();` inside `initTerm()`, and add a third tab button and matching pane in the Capture-the-flag HTML (follow how Level 2's `<button class="lvltab">` and `<div class="lvlpane">` are set up).

## Keeping the bank updated

The runbooks live in the `PROJECTS` array in the `<script>`. A few things to know:

- **Which runbooks are featured** — the `FEATURED` array lists the project IDs shown in "This week's bank." The two "Start here" essentials (GitHub and LinkedIn setup) always show.
- **Staging** — a runbook can sit finished in `PROJECTS` before it goes live; it appears only once its `id` is in `FEATURED`. That's how harder runbooks (the Intermediate *Harden a Linux server* and *Hack a web app*, and the Advanced ones later) get written and verified ahead of a weekly announcement, then switched on.
- **Rotating & Past runbooks** — to move a runbook out of the weekly spotlight, move its ID from `FEATURED` into the `ARCHIVED` array. Archived runbooks appear under the **Past runbooks** view (the button at the bottom of the bank) — fully browsable, never deleted, so anyone can come back and finish one. While the library is small, just keep adding to `FEATURED`; start moving the oldest into `ARCHIVED` only once the week's list feels long.
- **Adding or editing a runbook** — add or edit an object in `PROJECTS` (steps, skills, and the résumé / LinkedIn / AI-prompt text), then add its `id` to `FEATURED` when you want it visible. The quality bar every runbook has to clear is written up in `RUNBOOK-STANDARD.md`.
- **Meeting details** — near the top of the script there's a `MEETING` constant. It ships with `tba: true`, so the banner and the terminal point people to GroupMe for the date. When you know the next meeting, set `tba: false` and fill in `day`, `time`, and `room`.

## Beginner guides

Nearly every member starts from zero, so the site assumes no prior experience. Three standalone guide pages fill the gaps that used to make beginners bounce, and they're linked from inside the runbooks right where people hit them:

- **`home-lab-setup.html`** — a click-by-click walkthrough for building the VirtualBox lab (install, Kali, a target, the isolated network), plus troubleshooting for the real traps (virtualization disabled in BIOS, no network, Apple Silicon). Linked from a card at the top of the home-lab runbook.
- **`write-your-readme.html`** — how to write the project write-up a recruiter actually reads: Markdown basics, a fill-in template, a real example, and screenshot/redaction tips.
- **`push-to-github.html`** — three ways to get a project onto GitHub (website drag-and-drop, GitHub Desktop, the git command line), with troubleshooting.

Inside `index.html`, two helpers appear automatically in the runbooks: a **"New to the command line?"** primer at the top of any runbook that uses terminal commands, and **"How to write your README / How to push to GitHub"** links under the steps of any runbook with a write-up (hidden on the account-setup essentials). A runbook can also carry a `guide` field — `{ url, label }` — that renders a prominent card linking to a full walkthrough; that's how the home-lab runbook points to `home-lab-setup.html`.

**Deep-linking to a runbook:** add `#rb=<id>` to the site URL to open a specific runbook directly — e.g. `…/cybersecurity-club/#rb=nmap`. Handy for sharing "do this week's project" in the GroupMe.

## Credit

Built and maintained by **Desmond Dickey** — [github.com/dezdickey](https://github.com/dezdickey).

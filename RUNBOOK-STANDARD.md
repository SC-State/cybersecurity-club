# Runbook standard

The bank is only worth joining the club for if every runbook is **genuinely résumé-worthy** and **correct enough that a beginner succeeds**. This is the bar. Run the checklist below against every new runbook before it's featured. Fewer correct runbooks beat a padded library — never pad the count.

## Every runbook (the five principles)

1. **No guessed values stated as fact.** Example IPs, usernames, hostnames, and ports are labeled as examples, never presented as the real answer.
2. **Correct specifics.** Exact commands, file paths, menu names, and button labels — the real ones, not approximations.
3. **Tool / OS variation.** Where steps differ by platform or tool, say so (Windows / macOS / Linux; Npcap vs ChmodBPF; `auth.log` vs `secure`; Gmail vs Outlook vs Apple Mail).
4. **A `Success:` checkpoint on every step.** The reader must be able to confirm each step worked before moving on.
5. **The write-up step saves evidence and handles privacy.** Push a sanitized write-up to the portfolio repo — no raw logs/pcaps/`.eml` files, no real passwords or keys, personal data redacted, URLs defanged.

## Intermediate / Advanced only (two more, non-negotiable)

6. **Pin a concrete toolchain.** "Security Onion 2.4 in VirtualBox," not "a SIEM." A specific, reproducible stack keeps the steps testable and keeps them from rotting. Lean on authoritative upstream docs for the parts that change often.
7. **End with an "Interview questions you can now answer" block.** Two or three real questions plus the gist of a good answer (e.g. *"If asked why you placed the firewall rule there, you should be able to say…"*). This forces the understanding that makes the résumé line survive an interview — and doubles as interview prep. Worth adding to beginner runbooks too where it fits.

### Offensive / lab content

Bake the guardrails into **every step**, not a top note: isolated VM, no network bridge, and "systems you own or have written permission to test" repeated where it matters. Never instruct downloading live malware carelessly.

## The review loop (run this each time)

1. Detail one runbook.
2. Critique it honestly against the checklist above — list issues, worst first.
3. Fix the ones that matter.
4. Verify (commands correct, steps real, a beginner could follow).
5. Only then feature it.

Review fatigue is what kills the bar, not bad intentions — so keep each pass fast by running this list instead of re-critiquing from scratch.

## Rollout notes

- **Go additive while the library is small.** Detail more, show more. The **Past runbooks** archive already ships (empty for now) — scarcity on the weekly spotlight, permanence on the library. Keep adding to `FEATURED`; start moving the oldest into `ARCHIVED` (they appear under Past runbooks) only once the week's list feels genuinely long (~15+). Nothing is ever deleted, so a member can always come back and finish.
- **Sequence: Beginners → Intermediate → Advanced.** Faster to get right, they build the base members need, and Advanced needs the extra toolchain/guardrail work first.
- **Crowdsourced QA.** Each runbook carries a "find an error? tell us in GroupMe" line — members are the test environment the static site otherwise lacks. Act on what they report.

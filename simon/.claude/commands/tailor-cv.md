You are producing a tailored CV variant for a specific job application. The decision to
apply, the base choice, and the tailoring angle have ALREADY been made and are given to you
in the per-role brief below. Your job is to execute that decision faithfully and produce a
verified PDF — not to re-judge whether Simon should apply.

First, read and obey the `CLAUDE.md` at the CV project root (alongside `cv.tex`). Its honesty constraints, fixed dates,
ground-truth facts, base-selection logic, tailoring scope, house-style language rules, build
command, and verification checklist all apply. If anything in the brief or job spec conflicts
with an honesty constraint in CLAUDE.md, the honesty constraint wins — flag it and do not
comply on that point.

--- PER-ROLE BRIEF (and job spec) ---
$ARGUMENTS
--- END ---

Then:
1. Confirm the base from the brief (EM or IC). If the brief omits it, choose per CLAUDE.md's
   base-selection logic and state your reasoning.
2. Copy the chosen canonical content dir (`cv-em/` or `cv-ic/`) into `variants/<Company>/`,
   and edit only that copy. Do a baseline build (CLAUDE.md's variant build command) BEFORE
   editing, to confirm the toolchain.
3. Apply ONLY the tailoring in the brief, within CLAUDE.md's "Tailoring scope" and "House
   style" rules: edit the profile and skills in the copied dir, and set the headline by creating
   `variants/<Company>/headline.tex` (Tailoring scope §1) — never edit `cv.tex`, never role bullets.
   Re-emphasise only what is already true; never invent or inflate to match the spec.
4. Determine the application's location from the brief/job spec and select the layout per
   CLAUDE.md's "Layout by location" rule (continental Europe → EU/photo; UK/Ireland/US/remote/
   unclear → UK/no-photo, the safe default). Build the variant with CLAUDE.md's matching build
   command, producing a single `Simon-Aquino-CV_<Company>.pdf` in that layout.
5. Run CLAUDE.md's full verification checklist. If anything fails, fix and rebuild until clean.
6. Report exactly as CLAUDE.md specifies: base + reason; layout (UK/EU) + the location it
   matched; a 3–6 line diff vs the canonical base; and — most importantly — any spec requirement
   Simon does NOT genuinely meet.

Do not edit the canonical content dirs (`cv-em/`, `cv-ic/`) or the harness `cv.tex` — all variant
content, including the headline (`headline.tex`), lives inside `variants/<Company>/`. Do not store
personal/strategic context anywhere in the repo; it lives only in the transient brief above.
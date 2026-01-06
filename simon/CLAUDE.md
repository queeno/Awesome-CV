# CV tailoring — operating context

This file is the permanent, operational context for tailoring Simon Aquino's CVs to
specific job specs. It is read automatically at the start of each session. Personal /
strategic context (compensation floor, location reasoning, motivations) is NOT stored
here — it is supplied per-role in the tailoring brief. Treat everything below as ground
truth and obey it on every run.

---

## Canonical source files (NEVER edit)
The build is MODULAR — there is no single `.tex` per CV. One master template drives every cut:
- `cv.tex` — master template (shared build harness). For the headline it `\input`s
  `\cvdir/headline.tex` when the selected content dir provides one (variants do); otherwise it
  falls back to the canonical `cv-em`/`cv-ic` `\position{}`. It then `\input`s the section files
  from whatever content dir is selected at build time via `\def\cvdir{...}`. The published names
  `Simon-Aquino-CV_EM_UK` / `_IC_UK` are build job names, NOT files.
- `cv-em/` — engineering-leadership cut content (the default base): `summary.tex` (executive
  profile), `experience.tex`, `skills.tex`, `education.tex`, `languages.tex`, `certificates.tex`.
- `cv-ic/` — technical / individual-contributor cut content (fallback base): same file set.

The canonical content lives in `cv-em/` and `cv-ic/` — NEVER edit these. Always COPY the chosen
base into `variants/<Company>/` first and edit only the copy. After any run, `git diff` must be
clean on `cv-em/` and `cv-ic/`.

`cv.tex` is the shared harness, not canonical CV content, and is NEVER edited for a variant — a
variant carries its own headline in `variants/<Company>/headline.tex` (see Tailoring scope §1).
After any run, `git diff` must be clean on `cv.tex` too.

Format: Awesome-CV style — `\position{}` for the headline (canonical cuts set it in `cv.tex`;
variants set it in `variants/<Company>/headline.tex`), a `cvparagraph` block in the cut's
`summary.tex` for the executive profile, and `cventries`/`cventry`/`cvitems` for roles.

---

## Honesty constraints (NON-NEGOTIABLE — these are ground truth)
Every claim in any generated CV must be true. Never re-introduce a removed inflation to
match a job spec. Specifically:

- **JPMorgan Chase**: title "Engineering Manager, Cloud Enablement". Line-managed a team
  that grew **to 13** engineers (NOT "3 to 50+"). Did **not** own a budget — advised on
  spend. **Advised** C-suite/senior stakeholders (never "partnered with", "managed", or
  "regularly briefed"). Strongest true line: built and won the business case to the
  Engineering Director to restructure the team for scale; new structure permanently
  adopted (this is org-design, NOT manager-of-managers — never imply he managed managers).
- **No "multi-million pound budget" ownership claim** anywhere, for any role.
- **"AI-first" / "AI-First Delivery"** means: directs and reviews AI-generated code rather
  than hand-writing it, and led a team's adoption of AI-assisted development and AI-driven
  code review. It must NEVER be reworded to imply building AI products, LLM pipelines, or
  AI-native systems. EXCEPTION — platform work that *enables* AI is true and allowed: at
  JPMorgan he delivered AI-ready platform blueprints (Vertex AI integration, data pipelines)
  on the firm-wide GCP/Kubernetes foundation, enabling teams' transition to data-intensive
  GenAI workloads. State that as platform enablement of AI — NEVER as building the
  AI / models / products themselves.
- **Haleon (current)**: genuine ownership of the project budget, hiring, and staffing,
  accountable to client stakeholders; is NOT the platform's technical authority; this is a
  project, NOT a function P&L — never inflate to "owns the org's commercials".
- **Deloitte**: "coordinating across" 3 satellite teams — coordination, NOT leading them.
- **GitHub migration (Haleon)**: it was an Azure DevOps → GitHub source-control/CI
  migration for a team working on a SAP ERP platform. It was NOT a SAP ERP migration.
- **Compliance / certification keywords**: ISO27001/SOC2 may appear only as "delivered within ISO
  27001/SOC 2-aligned frameworks", never as standalone competency keywords; never claim standard-level
  authorship or audit-design experience. SOX is genuine and permitted. IAM and Identity
  Governance are permitted. NIST is permitted only when the per-role brief explicitly confirms it;
  otherwise treat it as undefendable and omit. Never reinstate any of these to chase an ATS keyword
  match — defendability always outranks keyword density. The ISO27001/SOC2-aligned-frameworks claim
  is genuine only for JPMorgan Chase — do not extend it to any other role.
- If a spec asks for something Simon cannot genuinely claim, DO NOT add it. Flag it in the
  report instead (see Verify/Report).
- **Headline title honesty.** The CV headline/\position must never lead with a seniority title the candidate
  has not actually held. Simon has held Manager / Engineering Manager / Lead / Principal — these are fine
  to use in the headline. He has never held Director, Senior Director, Head of, or VP — never put any of
  these titles in the headline, even when it is the exact title of the target role, and even to mirror
  the job spec. Mirroring the target title at the top is the specific inflation failure to avoid:
  it writes a cheque the experience section cannot cash and reads as overreach to a screener.
  Allowed instead: descriptive, defensible leader framings that signal altitude without claiming
  the unearned title — e.g. "Engineering Leader," "Infrastructure & Platform Engineering Leader," 
  "Platform Engineering Leader."
  The descriptors after the title (e.g. "Cloud-Native Platforms, SRE") may freely use spec language as long as
  each is individually defensible.
  The target-role title belongs in the application form and the cover letter (where leadership intent and
  readiness can be argued), not asserted at the top of the CV.
  This rule governs the headline specifically. It does not change the locked role-bullet facts, which remain untouched.

## Fixed dates (never change)
- JPMorgan Chase: Apr 2023 – Mar 2025
- GitHub migration (Haleon, via CECG): Apr 2025 – Sep 2025
- Barclays (via Red Badger): Oct 2025 – Mar 2026
- Haleon, Data Engineering (via CECG): Mar 2026 – Present
These must abut with no gaps and no overlaps. Verify after every build.

## Employment structure (state correctly if relevant)
All recent roles are contract engagements via an agency/consultancy (CECG for JPMorgan,
the GitHub migration, and Haleon; Red Badger for Barclays). The client owns the brand line;
the agency is named in the role subtitle (e.g. "via Core Engineering Consulting Group").

---

## Base selection logic
- **EM cut** for: Head of Engineering, Head of Platform, Director of Engineering,
  Engineering Manager, VP Engineering, and any role wanting leadership + people/delivery
  ownership. Most "Head of" roles want BOTH leadership and hands-on depth — the EM cut
  carries both, so default to it.
- **IC cut** only for: pure senior-IC / principal-engineer / staff / forward-deployed
  contract roles where leadership is not the ask.
- State the chosen base and a one-line reason at the start of the run.

## Tailoring scope (keep it LIGHT — do not over-tailor)
Edit only these three areas. Do NOT rewrite role bullets.
1. **Headline** (`\position{}`): mirror the role's title/level; name its core stack; lead with
   the leadership lane; DROP industry framing that doesn't match the target (e.g. remove
   "Regulated / Financial Services" for a non-FS role). Keep the template's existing separator
   macro/glyph; change only the segment text.
   Set a variant's headline by creating `variants/<Company>/headline.tex` containing a single
   `\position{...}` line — `cv.tex` auto-`\input`s it for that `\cvdir`. Do NOT edit `cv.tex`;
   the canonical `cv-em`/`cv-ic` headlines (its built-in fallback) stay untouched.
2. **Executive profile** (`cvparagraph`): surface the spec's named must-haves (stack,
   methods, domain) early; reorder or soften clauses that don't fit. Re-emphasise only what
   is already true — never invent.
3. **Skills**: front-load the technologies the spec names. Add a skill ONLY if it is
   already true of Simon (cross-check the canonical files). Never add a skill to match a JD.

Heavy per-application rewriting is how inflation creeps back — resist it. The role bullets,
dates, and titles stay as in the canonical base.

## House style — language
- Describe leadership in plain, concrete terms. Avoid HR / DEI jargon and vague terms-of-art.
  Specifically, do NOT use "psychologically safe" or similar buzzwords; never re-introduce them.
- Keep the people-leadership SUBSTANCE (hiring, performance, retention, developing engineers,
  the team-restructure win) — express it concretely (e.g. "owned hiring, performance, and
  retention; developed engineers into senior roles"), not as jargon. Removing buzzwords must
  not thin the actual leadership evidence.
- Write to be accurate and to land with the reader. Do not bias the CV toward or against any
  political or cultural framing; the test for any line is "is it true and does it strengthen
  the application", nothing else.
- **ATS keyword alignment** (permitted, with guardrail). Target ATS/AI-matching systems
  keyword-match the CV against the job description, so deliberately echoing the spec's
  own terminology is encouraged — but only within these limits:
  Keywords may be surfaced/reordered only in the light-tailoring zones (headline descriptors,
  profile emphasis, skills line). Never alter role bullets to insert keywords.
  Only include a keyword if it is genuinely defensible — i.e. Simon could speak to it for
  several minutes in an interview with a concrete example. Keyword value never overrides
  defendability. An ATS hit that gets him into a room he then can't hold in is a net loss,
  not a win.
  This explicitly does not reopen the banned/undefendable terms: SOC2/ISO27001 remain
  barred as standalone competencies (the operated-under framing is the only permitted
  form), and the hard grep gate still applies.
  If the spec uses a term that is adjacent-but-not-quite-his (e.g. a domain he's near but
  doesn't own), prefer the honest adjacent phrasing over the spec's exact word rather
  than claiming the stronger term for the keyword match.

---

## Build
Run from the `simon/` directory (where `cv.tex` and the `awesome-cv.cls` symlink live).
- Canonical targets (Makefile): `make uk-em`, `make eu-em`, `make uk-ic`, `make eu-ic`
  → `Simon-Aquino-CV_EM_UK.pdf`, `_EM_EU.pdf`, `_IC_UK.pdf`, `_IC_EU.pdf` (EU adds the photo).
- Variant: point `\cvdir` at the copied dir. The layout (photo vs no-photo) is chosen by the
  application's location — see "Layout by location" below — and a variant produces ONE matched PDF:
  - UK / no-photo (default):
    `xelatex -jobname=Simon-Aquino-CV_<Company> "\def\cvdir{variants/<Company>}\input{cv.tex}"`
  - EU / photo (prepend `\def\showphoto{1}`):
    `xelatex -jobname=Simon-Aquino-CV_<Company> "\def\showphoto{1}\def\cvdir{variants/<Company>}\input{cv.tex}"`
Output PDF: `simon/Simon-Aquino-CV_<Company>.pdf` — a single PDF in the location-matched style,
built from the copy in `variants/<Company>/`.

## Layout by location (which style a variant produces)
A variant always produces a SINGLE PDF whose layout matches the job's location (the role's
stated location, not Simon's):
- **Continental Europe / EEA** (e.g. Germany, Austria, Switzerland, France, Italy, Spain, the
  Nordics, Benelux, and the rest of mainland Europe) → **EU / photo** style: prepend
  `\def\showphoto{1}`.
- **UK, Ireland, US, remote, or unclear** → **UK / no-photo** style: omit `\def\showphoto{1}`.
  No-photo is the safe default — when the location is ambiguous, build no-photo.
The photo file is `simon.png`; it renders only in the EU style.

## Verify every build (fail loudly and fix before finishing)
- Headline matches the target role's lane; no stale segment left from another variant.
- Layout matches the job location: the photo is present iff the role is in continental Europe
  (EU style); UK/Ireland/US/remote/unclear render with no photo.
- Executive profile leads correctly and contains no claim outside the honesty constraints.
- JPMorgan reads "to 13", title "Cloud Enablement", dates Apr 2023 – Mar 2025.
- Dates abut with no gaps/overlaps across all roles.
- Em-dashes render (`---` → "—"); no literal triple-hyphens in the PDF.
- No run-together / missing-space typos: grep the source for `andwon`, `),Platform`, and
  any lowercase-immediately-followed-by-uppercase run inside a word.
- No orphaned or duplicated bullets (a known past failure after edits).
- Canonical content dirs `cv-em/` and `cv-ic/` AND the harness `cv.tex` are all unchanged (git
  diff clean); the variant's headline lives only in `variants/<Company>/headline.tex`.

## Report at the end of each run
1. Base chosen + one-line reason.
2. Layout chosen (UK/no-photo or EU/photo) + the job location it matched.
3. A 3–6 line diff of what changed vs the canonical base.
4. **Any spec requirement Simon does NOT genuinely meet** — flag honestly; do not paper
   over. This is the most important line of the report.

---

## Per-role brief (how a tailoring run is invoked)
Each run is driven by a short per-role brief (produced during a separate discussion phase)
plus the raw job spec. The brief specifies: base choice, headline direction, what to
surface, what to play down, and any role-specific honesty watch-points. Apply the brief
within the constraints above. If the brief ever conflicts with an honesty constraint, the
honesty constraint wins — flag the conflict and do not comply with the brief on that point.

---

## House style — stay factual, no empty claims
- Every line must point to something real: a specific action, technology, outcome, or
  responsibility. Prefer concrete nouns and verbs (what was built, led, owned, decided)
  over adjectives about how good it was.
- KEEP real keyword terms — technologies, methods, domains, role/skill nouns (e.g.
  "Kubernetes", "Internal Developer Platform", "event-driven architecture", 
  "platform engineering"). These are searchable, true, and wanted (recruiters/ATS filter on
  them). They are NOT the target of this rule. Keyword density is good where the terms are real.
- BAN claims of superiority Simon cannot evidence — words that assert a ranking or that he is
  better than others: e.g. "world-class", "best-in-class", "exceptional", "elite", "top-tier",
  "industry-leading", "thought leader", "ninja/rockstar/guru". These are empty boasts; cut them.
- ALLOW a bit of colour — honest statements of character, disposition, or motivation that make
  no comparative claim: e.g. "passionate", "hands-on", "pragmatic", "curious", "builder".
  A grounded CV can have personality; it just can't claim to be the best.
  Test: does the word claim Simon is SUPERIOR (cut) or describe HOW he works / what drives him
  (keep)? "World-class engineer" claims rank → cut. "Passionate about platform engineering"
  describes disposition → keep.
- No numbers, percentages, scales, or named tools unless they are true and Simon can defend
  them in an interview. Do not invent metrics or round figures up for effect.
- Claims of degree ("significantly", "drastically", "hyper-scale", "massive") require a
  concrete basis; if there isn't one, state the plain fact without the intensifier.
- Goal: a GROUNDED tone — keyword-rich and concrete, free of empty praise. When in doubt
  between an impressive-sounding phrasing and a precise one, choose precise. A defensible,
  modest-sounding true claim beats an inflated one that collapses under questioning.
- **"AI-first" / "AI-native" phrasing** is PERMITTED as a description of *how Simon works*:
  he directs and reviews AI-generated code rather than hand-writing it, and led a team's
  adoption of AI-assisted development and AI-driven code review. Headlines/labels like
  "AI-Native Cloud Architect" or "AI-First Delivery" are acceptable in this sense. It is a
  VIOLATION only when the wording claims he **built** AI systems, AI products, LLM pipelines,
  agents, evaluation frameworks, or AI-native architectures. Test: does it describe his way of
  working (allowed) or claim he engineered an AI system (not allowed)?</parameter>
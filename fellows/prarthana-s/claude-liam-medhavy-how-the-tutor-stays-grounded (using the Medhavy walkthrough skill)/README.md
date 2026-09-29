# How the Tutor Stays Grounded in Your Textbook — Prarthana Shetty

**Status:** planning, revised 2026-09-23. No capture, narration audio or render exists yet.

## This week's contribution

**Question:** When I ask Medhavy's tutor a question, what connects its answer back to the textbook?

**Prediction (from the code, before filming):**
- When a student asks a real question, the system searches the textbook for related passages.
- The page that's open doesn't decide that search. It only shapes the suggested-question chips.
- The passages are given to the model as context. The model also receives tutor instructions and recent conversation context.
- The same passages appear as source cards that the student can open.
- This makes answers more connected to the book and easier to verify, but not automatically correct.
- The cards are not a sentence-by-sentence citation.

**What I built/tried:**
- A source-code investigation (`AI-TUTOR-SOURCE.md`).
- A capture plan through the admin view, with pre-capture name masking (`CAPTURE.md`, `capture/plan-*.json`).
- About 3 minutes of beats built mostly on real Medhavy footage (`beat_sheet.json`, `SHOTLIST.md`).
- Separate landscape and vertical strategies.

**Observed result:** pending capture.

**Next experiment:** pilot capture; checks R1, M1 and V1–V12.

## Decisions made (2026-09-23)

| Topic | Decision |
|---|---|
| Account | Admin route only; no student dashboard is shown or described |
| Redaction | My name in the hub header is masked before recording |
| Outro | `ClaudeTitleOutro`, as the skill requires ("At Nik Bear Brown") |
| `GroundingFlow` | Lives locally in this folder; brutalist.art is not modified |
| Vertical | A separate portrait composition, reframed from the native-4K captures |
| Tutor memory | Not cleared. Inspect first; any clear is my decision, made after a full explanation |
| Narration | Cut to 451 words; B10 simplified to plain language |

## Decisions made (later on 2026-09-23)

| Topic | Decision |
|---|---|
| Masking wrapper | Approved. It is local to this folder. The name comes only from the `MW_MASK_TEXT` environment variable. There is an explicit literal-name leak check; on a leak the run aborts and the affected capture is deleted. The design is in CAPTURE.md. The wrapper itself will not be written until the design is reviewed. |
| Vertical source | Option B: a dedicated capture at 1280×720 CSS, DPR 3. It runs only after the landscape capture is reviewed, and only after a layout test that sends no tutor requests has passed. |
| Order | Landscape first; stop for review; then portrait. |
| Memory | Still not cleared automatically. |
| Git | Everything stays local: no add, commit, push, PR, merge, publish or upload. |

## Human and AI work

**My decisions, implementation and verification:**
- The topic, central question and wording rules.
- Approving AI-TUTOR-SOURCE.md.
- Confirming the admin account.
- Signing in myself.
- All of the 2026-09-23 decisions above.
- The final review of narration and footage.

**AI tools and voices used, and what they generated:**
- Claude Code (Opus) read the code, and drafted AI-TUTOR-SOURCE.md, these planning files and the narration.
- Kokoro `am_onyx` ("Liam") will voice the narration. It is an AI voice, not mine.

**What I rejected or corrected:**
- The reference reel's "uses this chapter as context" and "SQLite memory keyed by session".
- "The page plays no role anywhere".
- Describing memory as "per user".
- Using "Top sources used" as evidence.
- A student-dashboard branch.
- A 517-word script, which was too dense.

**What remains unverified or failed:**
- Everything marked PENDING in FACTCHECK.md.
- Production configuration.
- The masking wrapper, which isn't written yet.

## Reproduce

| Item | Value |
|---|---|
| Brutalist version and commit | `6a8380a` (2026-09-20), checked 2026-09-23 |
| Source commits | `medhavi-cancer@b8b6c21`, `medhavi-hub@efcc3f5` |
| Beat sheet | `beat_sheet.json` |
| Reel-local scenes (planned) | `GroundingFlow`, `GroundingFlow916`, `PanelFocus916` |
| Reel-local capture wrapper (planned) | `capture/capture_masked.py` |
| Commands | `BUILD-PROMPT.md` (WSL Ubuntu, plain `python3`) |
| Approvals | Voice approval pending; no sign-offs recorded |

## Watch and review

| Deliverable | Status |
|---|---|
| Landscape (3840×2160): `TutorGrounding_PrarthanaS.mp4` | pending |
| Vertical (2160×3840): `TutorGrounding_PrarthanaS.mp4` | pending |
| PM review | pending |
| YouTube 4K processing check | pending upload |
| Professors' publication decision | pending |

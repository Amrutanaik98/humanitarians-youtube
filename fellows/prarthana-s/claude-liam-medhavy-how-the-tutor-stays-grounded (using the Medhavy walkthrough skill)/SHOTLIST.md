# SHOTLIST.md — How the Tutor Stays Grounded in Your Textbook

- **Skill:** `medhavy-walkthrough`, textbook mode, book "Cancer textbook" (cancer.medhavy.com), **admin account**.
- **Voice:** Kokoro `am_onyx` (Liam), AI narration.
- **Target:** about 180 s.
- **Narration:** 451 words at base. The budget is 430–460 once conditionals are resolved (see "Word budget").

**Status: PLANNED.** Windows are TBD until capture. "Est." is the narration estimate. Footage windows are longer, and the gaps are silence so the UI can breathe.

## Beats

| Beat | Act | Lane | Source | Est. | On screen | Gates / V-checks |
|---|---|---|---|---|---|---|
| B00 | INTRO | Remotion `ClaudeComposerAsk` | — | 10 s | Central question; "AI narration (Kokoro am_onyx)" running text | — |
| B01 | QUESTION | Remotion `BrutalistHesitantWriter` | — | 12 s | "The sources **prove** the answer." → "…**supply context for**…" | — |
| B02 | BODY | **SCREEN** | run-signin | 5 s | Sign-in card, signed out, nothing typed | — |
| B03 | BODY | **SCREEN** | run-book (hub tab) | 9 s | Admin Dashboard (name masked) → View All Textbooks → Cancer textbook → Open Textbook → new tab | R1 |
| B04 | BODY | **SCREEN** | run-book-p2 (book tab) | 6 s | Sidebar "5. Oncogenes" → "5.1 Introduction to Oncogenes" | — |
| B05 | BODY | **SCREEN** | run-book-p2 | 5 s | Open AI chat: "Ask this textbook", chips, footer | M1, V10 |
| B06 | BODY | **SCREEN** | run-book-p2 | 10 s | Question typed live and sent; "AI is thinking…"; cards arrive | V1, V5 |
| B07 | BODY | **SCREEN** | run-book-p2 | 7 s | Answer streams under the cards (mostly un-narrated) | V8 |
| B08 | BODY | **SCREEN**, *only if V2* | run-book-p2 | 4 s | "Dive deeper into all sources (N)" expands | V2 |
| B09 | BODY | **SCREEN**, *only if V3* | run-book-p2 | 8 s | Card → textbook page; panel closed; On-this-page link to the section; silent hold on the passage | V3, V4 |
| B10 | MECHANISM | Remotion **`GroundingFlow`** (local to this folder, not yet built) | — | 21 s | Six plain steps light in turn: question → search the textbook → relevant passages → given to the model as context [passages · tutor instructions · recent conversation] → answer → you inspect the passages | — |
| B11 | BODY | **SCREEN** | run-book-p2 | 14 s | Follow-up typed live (not read aloud); reply and cards, or none; answer streams | V6 |
| B12 | BODY | **SCREEN** | run-book-p2 | 6 s | Hold; footer "AI can make mistakes. Please verify important information." | V9 |
| B13 | VERDICT | Remotion `ClaudeVerdictArtifact` | — | 17 s | "Grounded, Not Guaranteed." | — |
| B14 | NEXT STEPS | Remotion `ClaudeComposerAsk` | — | 9 s | Your Turn | — |
| B15 | OUTRO | Remotion `ClaudeTitleOutro` | — | 6 s | Spoken title + "At Nik Bear Brown"; no jingle (skill-required, decided) | — |

- **SCREEN (real Medhavy footage):** B02–B09, B11, B12. That is 10 beats, 2 of them conditional.
- **Remotion:** B00, B01, B10, B13, B14, B15.

## Landscape strategy (16:9, 3840×2160)

1. **The real product is the evidence.**
   - Footage beats are full-bleed native 4K captures (1600×900 CSS at DPR 2.4), `treatment: none`.
   - No zooms, re-timing or overlays on product footage.
   - The site's own UI text carries the evidence.
2. **Breathing room.**
   - The narration is shorter than each footage window.
   - The silence falls where the UI is doing something: typing, "AI is thinking…", the stream, the page load, the passage hold.
   - Cut frame-exact. Pad the narration with silence, never stretch it.
   - End each window at its last screenshot, before the next navigation, so no white load frame shows.
3. **Hub as front door only.** B03 stays on the Admin Dashboard for just the click path, about 9 s.
4. **Remotion only where the browser can't show it:**
   - intro
   - misconception
   - how it works (`GroundingFlow`, the only new scene)
   - verdict
   - Your Turn
   - outro
5. **QC gates:**
   - The name mask holds on every hub frame (R1).
   - The footer warning is legible in B05 and B12.
   - Card text is checked on a 4K contact sheet.
   - The last frame of B01 shows the correction.
6. **Conditional beats.**
   - If V2 or V3 fail, B08 or B09 are dropped, not faked, and the Verdict's "Observed" line says what was seen.
   - If production contradicts the code (for example cards never appear), the story is revised from the footage.

## Vertical strategy (9:16, 2160×3840): a separate composition

The vertical version is its **own beat sheet and its own layouts**.

- **Not allowed:** squeezing or cropping the finished landscape master.
- **Not assumed:** that landscape framing stays legible on a phone.
- **Kept:** the same beats, in the same order, with the same claims and narration audio, and the same outro.

**Source footage (decided 2026-09-23: option B).** The vertical is built from a **dedicated portrait-friendly capture**:
- `run-portrait`: 1280×720 CSS at DPR 3, recorded natively at 3840×2160.
- `run-signin-916src`: an optional sign-in card at the same settings.

It runs **after** the landscape capture has been reviewed, and only if the layout test `run-portrait-test` passes (CAPTURE.md). Each beat is composed from these raw captures, never from the landscape master.

**Useful geometry (device px in the capture):**

| Element | Landscape pass (1600×900 @2.4) | Portrait-source pass (1280×720 @3) |
|---|---|---|
| Tutor panel | about 1008 × 2160 | about 1260 × 2160 |
| One source card | about 432 × 264 | about 540 × 330 |
| Card body text | about 24 px | about 30 px |
| Answer text | about 34 px | about 42 px |
| Upscale to fill 2160 px portrait width with the panel | about 2.1× | **about 1.7×** |

**The portrait take is a different tutor session.** It gets new answer wording and possibly different cards. So the vertical narration may only claim what the portrait footage itself shows. Every promoted conditional (V1, V2, V3, V4, V6) is re-checked against `run-portrait`. If a behaviour doesn't reappear, that line is dropped or reworded for the vertical. The facts and their order stay the same as the landscape.

**Layouts (all reel-local, to be authored later; brutalist.art is not modified):**

- `PanelFocus916`: plays a keyframed crop region of the raw capture, with a native-rendered caption band above or below.
  - The caption names the step ("The question", "Retrieved passages", "Open a source", "The warning").
  - It never adds claims beyond the landscape narration.
- `GroundingFlow916`: the six steps stacked one per row.
- Bookends use the registered portrait scenes: `ClaudeComposerAsk916`, `BrutalistHesitantWriter916`, `ClaudeVerdictArtifact916`, `ClaudeTitleOutro916`.

**Per-beat reframing:**

| Beat | Portrait composition |
|---|---|
| B00, B01, B13, B14, B15 | Registered `*916` scenes, same props |
| B02 | Sign-in card crop, centred; caption band "Signed in off camera" |
| B03 | Two holds: shelf crop around the Cancer textbook card → Open Textbook button. Header region excluded from the crop *and* masked at capture. |
| B04 | Sidebar crop following the "5. Oncogenes" → "5.1" clicks, then the page title |
| B05 | Tutor panel crop: header, chips, footer warning |
| B06 | Panel crop; the question typed; then a punch-in on the card row so cards fill the width (about 2×) |
| B07 | Panel crop reframed on the answer text as it streams, scrolling the crop window down with the text |
| B08 | Card-row crop while it expands (if V2) |
| B09 | Crop of the textbook passage under its heading, so the passage fills the frame; the panel is out of frame (if V3) |
| B10 | `GroundingFlow916` |
| B11 | Panel crop: follow-up question, then the new card row, then the answer |
| B12 | Panel-bottom crop so the footer warning is large and legible |

**Build path:**
1. Run `./art vertical <reel>` to plan `vertical/` with its own beat sheet.
2. Author each SCREEN beat's portrait clip as `vertical/pantry/Bxx-916.mp4`, rendered by `PanelFocus916` from the raw capture. That is the toolkit's explicit replacement slot, and the pipeline never centre-cuts it.
3. Render native at `--height 3840`.

**Legibility QC.** Review a phone-size contact sheet (about 390 CSS px wide). Every card title, the question, the answer text and the footer must be readable, or the crop is tightened.

**Known limitation.** Even from the portrait-source pass, filling 2160 px of portrait width with the panel upscales it about 1.7×, and card punch-ins upscale more. This will be flagged to the PM as a source limitation, per FELLOWS-SUBMISSION.md. Native-rendered caption bands and Remotion scenes are sharp at 2160×3840.

## Word budget for conditionals

The base is 451 words. When a conditional line is promoted, trim to stay at 460 or under.

| Promoted line | Trim |
|---|---|
| V10 (B05, +23) | Delete B10's "The page you have open doesn't decide that search." (−9) and B04's second sentence (−9) |
| V1 (B06, +7) | No trim needed alone |
| Any V6 line (B11, +8 to +15) | Delete ", so check which sources, if any, come back" and end the sentence at "new words." (−8) |
| V4 (B09, +13) | Delete B14's last sentence (−7) |
| B08/B09 dropped | Frees 11 / 26 words; don't re-fill them |

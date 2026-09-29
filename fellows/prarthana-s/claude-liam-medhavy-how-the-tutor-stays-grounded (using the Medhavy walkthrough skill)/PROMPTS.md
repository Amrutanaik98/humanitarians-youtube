# PROMPTS.md — How the Tutor Stays Grounded in Your Textbook

No paid generation. No image or video model is called by this reel.

- Every product visual is a real browser capture of the live hub and the live cancer textbook.
- Every other visual is a Remotion scene from the brutalist.art library, plus one new reel scene (`GroundingFlow`, still to be authored).
- Narration is local Kokoro TTS (`am_onyx`).

## Reconstructed prompts on screen (labelled as such)

**B00 (ClaudeComposerAsk)**
- Command: "When I ask Medhavy's tutor a question, what connects its answer back to the textbook?"
- Running text: "AI narration (Kokoro am_onyx) · central question"

**B14 (Your Turn, ClaudeComposerAsk)**
- Command: "Ask your textbook a question. Open one of the sources it lists. Check the answer against it."
- Running text: "Suggested prompt · reconstruction"

## Questions typed into the book's tutor on camera (real; answered by the site)

These go to the production tutor, which is the site's own OpenAI-backed service. Its answers are shown unedited.

| # | Step | Text | Why this question |
|---|---|---|---|
| Q1 | plan-book step 10 | **How does gene amplification turn a proto-oncogene into an oncogene?** | A content question squarely covered by Chapter 5 (§5.2.3, §5.4.2 "Gene Amplification"). It is asked from the 5.1 page, so an opened source may sit on a different page (V4). It is not conversational, so search runs. |
| Q2 | plan-book step 27 | **Can you explain that in simpler terms, with an analogy?** | Only makes sense with the prior turn ("that"), so it shows the conversation context. Its own words give the search little to go on, which is the honest V6 test. |
| Q3 | plan-book step 33 | **Thanks!** | V7 evidence only: expected to skip search and show no cards. Not planned for the cut. |

Rejected alternatives:
- The suggested chips: they are page-title templates, so they're less natural as a "strong content question".
- The 2026-09-18 reel's questions: we want fresh footage, not a repeat.

## Capture

`brutalist.art/skills/make/medhavy-walkthrough/scripts/capture_admin.py` runs with:
- `capture/plan-signin.json` (`--no-session`)
- `capture/plan-book.json`

The session comes from `save_session.py`, where Prarthana signs in herself. I (the agent) type no credentials.

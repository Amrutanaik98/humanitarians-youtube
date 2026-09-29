# BUILD-PROMPT.md — How the Tutor Stays Grounded in Your Textbook

**Not run yet.**
- **Environment:** WSL Ubuntu, plain `python3`. Do not use `brutalist.art/.venv`.
- **Gates:** every phase ends at a review stop.
- **Repos untouched:** `brutalist.art`, `medhavi-cancer` and `medhavi-hub` are not modified.
- **No git:** no `git add`, commit, push, PR, merge, publish or upload at any point.

```bash
cd /mnt/c/Users/prart/HumanitarianAI/MedhavyAITutorVideo/brutalist.art
REEL=/mnt/c/Users/prart/HumanitarianAI/MedhavyAITutorVideo/humanitarians-youtube/fellows/prarthana-s/how-the-tutor-stays-grounded
W=$REEL/capture/capture_masked.py      # reel-local wrapper (design: CAPTURE.md; not yet written)
```

## Phase 0: wrapper (after Prarthana reviews the design)

1. Write `$W` to the CAPTURE.md spec. **Stop.** Show Prarthana the exact source and a walkthrough of the leak check.
2. Run the self-test. It uses local headless Chromium, a dummy term and a `data:` page, with no network and no Medhavy.
   ```bash
   python3 $W --self-test
   ```

## Phase 1: landscape (first)

3. Prarthana saves the session, signing in herself.
   ```bash
   python3 skills/make/medhavy-walkthrough/scripts/save_session.py
   ```
4. Signed-out sign-in capture.
   ```bash
   python3 $W $REEL --run run-signin --plan $REEL/capture/plan-signin.json --css-size 1600x900 --dpr 2.4 --no-session
   ```
5. Prarthana sets the mask term. It isn't echoed and isn't saved to shell history.
   ```bash
   read -rs MW_MASK_TEXT && export MW_MASK_TEXT
   ```
6. Landscape pilot.
   ```bash
   python3 $W $REEL --run run-pilot --plan $REEL/capture/plan-book.json --css-size 1600x900 --dpr 2.4
   ```
7. Review the pilot:
   - redaction (Layers 1–4)
   - tutor memory state
   - live tutor behaviour
   - the real card titles
   - which conditional beats survive
   **Stop and report.** Any memory clear waits for Prarthana's decision.
8. Corrected landscape capture.
   ```bash
   python3 $W $REEL --run run-book --plan $REEL/capture/plan-book.json --css-size 1600x900 --dpr 2.4
   ```
   Then repeat the redaction review.
9. Clear the mask term.
   ```bash
   unset MW_MASK_TEXT
   ```
   Fill in the timings. Promote or delete the conditional lines using the word budget. Update FACTCHECK. **Stop for review.**

## Phase 2: portrait source (only after the landscape capture is reviewed)

10. Set the mask term again, then run the layout test. It sends no tutor requests.
    ```bash
    read -rs MW_MASK_TEXT && export MW_MASK_TEXT
    python3 $W $REEL --run run-portrait-test --plan $REEL/capture/plan-portrait-test.json --css-size 1280x720 --dpr 3
    ```
    Check it against the pass criteria in CAPTURE.md. **If it fails, stop and report. Send no tutor requests.**
11. Optional portrait-friendly sign-in card.
    ```bash
    python3 $W $REEL --run run-signin-916src --plan $REEL/capture/plan-signin.json --css-size 1280x720 --dpr 3 --no-session
    ```
12. Update `plan-portrait.json` steps 18 and 21 with the confirmed title. Then run the portrait capture, which sends 2 tutor requests.
    ```bash
    python3 $W $REEL --run run-portrait --plan $REEL/capture/plan-portrait.json --css-size 1280x720 --dpr 3
    ```
    Then `unset MW_MASK_TEXT`. Review redaction, memory interference, and whether each behaviour the narration relies on also appears in this take. **Stop for review.**

## Phase 3: reel-local scenes (not implemented yet)

These live in this folder, using the same approach as `../what-is-medhavy/` (`MedhavyExplainerScenes.tsx`, `Root.tsx`, theme):

| Scene | Size | Used for |
|---|---|---|
| `GroundingFlow` | 3840×2160 | landscape B10 |
| `GroundingFlow916` | 2160×3840 | vertical B10 |
| `PanelFocus916` | 2160×3840 | portrait reframes of the `run-portrait` footage |

## Phase 4: landscape build (after the narration is final and the voice approval is recorded)

13. Run `./art approvals $REEL --fingerprints`. Prarthana records her own sign-off; it is never invented for her.
14. Generate narration audio, prepare media and render the scenes.
    ```bash
    python3 runtime/scripts/generate_audio_kokoro.py $REEL
    python3 skills/make/medhavy-walkthrough/scripts/prepare_media.py $REEL
    python3 runtime/scripts/remotion_scenes.py $REEL
    ```
    Also render the reel-local `GroundingFlow` to `media/B10.mp4`.
15. Run the walkthrough check, then the review compile, then the final-frame check.
    ```bash
    ./art medhavy-walkthrough --check $REEL
    python3 runtime/scripts/compile.py $REEL --review --fps 30 --height 2160
    ```
    Then run `runtime/qc/final_frame_check.py` and look at the frames yourself.
16. Limit each beat to −1 dBTP, then export the landscape master.
    ```bash
    ./art final $REEL --height 2160 --fps 30 --out $REEL/exports/landscape
    ```

## Phase 5: vertical build (separate composition)

17. Create the separate portrait beat sheet.
    ```bash
    ./art vertical $REEL
    ```
    This plans `vertical/`. Its SCREEN beats come from `run-portrait` (and `run-signin-916src`), reframed with `PanelFocus916` into `vertical/pantry/Bxx-916.mp4`. B10 uses `GroundingFlow916`, and the bookends use the registered `*916` scenes. It is never a crop of the landscape master.
18. Review the phone-size contact sheet for legibility.
19. Render the vertical preview and the final master.
    ```bash
    python3 runtime/scripts/remotion_scenes.py $REEL/vertical
    ./art run $REEL/vertical --height 1920
    ./art final $REEL/vertical --height 3840 --out $REEL/exports/vertical
    ```

Handoff to GitHub and Drive is Prarthana's own step, per FELLOWS-SUBMISSION.md, and happens outside this plan.

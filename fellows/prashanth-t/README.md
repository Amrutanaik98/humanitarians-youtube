# Prashanth T.

**Role:** AI/ML Developer  
**Project:** Madison — Jungian Brand Archetype Detector  
**GitHub:** [@PrashanthTalwarr](https://github.com/PrashanthTalwarr)

## What's in this folder

Four pieces of work, each in its own subfolder. Two are progress updates on the
Madison project; two are STEM/AI explainers. Subfolders here are currently named
by reel slug rather than the dated `YYYY-MM-DD-short-slug/` form.

**Madison — project progress**

- `madison-archetype-progress/` — scoping update. What the twelve Jungian brand
  archetypes are, why most archetype tools are shallow (a short brief in, one
  generic label out), and the three things this one does differently:
  evidence-based reads of a brand's real language, hybrid/tension-aware output
  that flags inconsistency, and output that ends in application. Starting with the
  Ruler archetype for luxury branding. Status at the time: scoped, not built.
- `madison-archetype-progress-week2/` — week-two design update. The section-five
  methodology turned into a concrete technical design across three parts: inputs
  (published brand copy, not a self-report questionnaire), scoring (every trait
  score carries the line of copy that earned it), and evaluation (hand-labelled
  brands first, to prove it reads voice and not surface keywords). Names the
  blocker — sample data: format, count, owner. Status: design drafted, not built.

**STEM / AI explainers**

- `llm-function-calling/` — how a model that can only produce text uses external
  tools. The four-step loop, how a tool result returns as another message, the
  common failure modes, and how the same loop is what an agent is built from.
- `agent-memory/` — how memory works in an AI agent. Why each model call is
  stateless, short-term memory as the running conversation and its context ceiling,
  long-term memory as a store outside the model, and the retrieve-into-context
  pattern.

**Shared code**

- `FnCalling.tsx` — the reel-local Remotion components these cuts use:
  `FnCallLoop` (the four-stage request/response figure), `FnCallPredictCard`, and
  `FnCallTitleOutro`.

Each work subfolder holds `beat_sheet.json` (the authored reel, which is what the
renderer consumes) alongside its build documentation: `SHOTLIST.md` (typed work
order and per-beat scene assignment), `FACTCHECK.md` (claim-by-claim basis),
`SOURCES.md` (provenance, and what is constructed or illustrative rather than
measured), `CHECKS-REPORT.md` (the pre-render gate report), `PROMPTS.md` (the
prompts shown on screen), and `BUILD-PROMPT.md` (a paste-ready prompt that rebuilds
the reel end to end). Two folders also carry a `BUILD-LOG.md`, recording defects
found during the build and how they were resolved.

## Frictional log

Every work subfolder here carries its own `FRICTIONAL.md` — a dated record of the process
behind that specific piece of work, kept beside the evidence it describes: what was tried
and expected, where it resisted and what was done next, what Claude or another person
contributed and what was accepted, changed or rejected, and what is now understood or
still open. Append as you go; never rewrite an earlier entry. It is not graded and not a
performance review. See <https://www.humanitarians.ai/fellows> for what an entry contains.

# FACTCHECK.md — How the Tutor Stays Grounded in Your Textbook

**Basis:** `AI-TUTOR-SOURCE.md` (approved 2026-09-23) against `medhavi-cancer@b8b6c21` and `medhavi-hub@efcc3f5`. Paths are relative to `medhavi-cancer/` unless marked otherwise.

**Status key:**
- **CODE** — supported by the source code.
- **PENDING capture** — the baseline screen behaviour still has to be filmed.
- **PENDING Vn** — held out of the narration until that live check is observed.
- **DROPPED** — not claimed.

| Beat | Claim (as narrated) | Basis | Status |
|---|---|---|---|
| B00 | Required opening, verbatim, first; AI narration disclosed | FELLOWS-SUBMISSION.md; on-screen running text | CODE (script) |
| B01 | Sources "supply context for" the answer rather than "prove" it | `chat-orchestrator.ts:220-227`; no sentence-to-source mapping exists | CODE |
| B02 | Signed in myself; nothing typed on camera | `--no-session` run; the action log shows no `type` | PENDING capture |
| B03 | Signed in through the admin view, which gives access to the textbook shelf; open the Cancer textbook | Prarthana confirmed admin (2026-09-23); `AdminDashboard.tsx:679-694, 756` (View All Textbooks tab), `:809` (Open Textbook) | CODE; PENDING capture, R1 |
| B04 | Chapter 5, Oncogenes | `content/docs/Chapter5/meta.json`, `1_Introduction.mdx` | CODE; PENDING capture |
| B05 | The tutor panel is "Ask this textbook" | `LayoutWrapper.tsx:273-276` | CODE; PENDING capture |
| B05 (cond.) | The open page shapes the suggested questions; asking runs the answer search across the textbook | `chat-suggestions/route.ts:19-41, 50-57` (fixed templates using the page title; not AI-generated); `analyze-context/route.ts:127`, `two-api-sse.ts:135-138, 190-195` (no page sent) | CODE; on-screen PENDING V10 |
| B06 | "These cards are the textbook passages the retrieval step surfaced and supplied as context for the answer." | `chat-orchestrator.ts:220-225` (the same results build SOURCES) and `:252-265` (the same results are sent as cards) | CODE; the cards appearing is PENDING capture |
| B06 (cond.) | They show up before the answer does | Server order `:252` before `:277`; screen order unverified | PENDING V1 |
| B07 | The answer arrives a little at a time | `:290-295`; client typing `SideChatPanel.tsx:534-572` | CODE; PENDING capture |
| B07 | Cards don't say which sentence came from which passage | No citation mapping in the chat path; the UI shows cards only (`SideChatPanel.tsx:870-906`) | CODE |
| B08 (beat cond.) | Only a few cards show at first; this opens the rest (N) | `SideChatPanel.tsx:120, 877, 890-903` | PENDING V2 |
| B09 (beat cond.) | Opening a card takes me to that part of the book; section name | `SideChatPanel.tsx:79-83, 203-240` | PENDING V3 |
| B09 (cond.) | "It isn't the page I was reading. The search covers the whole book." | Whole-book index (`local-orama.ts:335-407`) | "Whole book" is CODE; the screen claim is PENDING V4 |
| B10 | A real question triggers a search of the textbook for related passages | `analyze-context/route.ts:13-42, 138-152` (conversational messages skip search, hence "real question"); `chat-orchestrator.ts:174-189` | CODE |
| B10 | The page you have open doesn't decide that search | No page or path is sent to analyze-context or chat | CODE |
| B10 | Passages are handed to the model as context | `chat-orchestrator.ts:227, 284` | CODE |
| B10 | The model also receives its tutor instructions and recent conversation context | `:279-283` | CODE (wording rule) |
| B10 | The same passages are shown to you | `:252-265` | CODE |
| B11 | The model also receives recent conversation context, so it can build on what came before | `:228-232, 283` | CODE ("can") |
| B11 | The search runs again on these new words | `analyze-context/route.ts:127, 135`; `chat-orchestrator.ts:176` | CODE |
| B11 (cond.) | Picks up where it left off / cards drifted / no sources / still on topic | Observation only | PENDING V6 |
| B12 | "AI can make mistakes. Please verify important information." | `SideChatPanel.tsx:1046-1048` | CODE; PENDING V9 |
| B13 | Generated with textbook passages in its context; the passages are exposed; more connected and easier to verify; not automatically correct; cards are a place to check, not proof of every sentence | AI-TUTOR-SOURCE.md §2, §7 | CODE |
| B14 | Your Turn | Advice | script |
| B15 | Regular outro | SKILL.md §3, OUTRO-LOCK.md | script (decided) |

## Not claimed (AI-TUTOR-SOURCE.md §7 and the 2026-09-23 wording rules)

The narration does not claim any of the following:

- that answers are grounded only in the open chapter
- that the open page drives retrieval
- that the cards prove what the answer relied on
- a per-sentence citation
- that grounding guarantees correctness
- that the AI cannot hallucinate
- that every answer has sources
- that the tutor was trained on the textbook
- that the cards are the "best" passages
- a model name
- that memory is "per user"
- the UI label "Top sources used" (it isn't spoken at all)
- anything about a student dashboard (the account is admin; none is shown or described)
- the page-context or SQLite claims from the 2026-09-18 reel

Some behaviours are not planned for the film. They are narrated only if they are observed on camera:
- a "Most Relevant" badge
- the page switching on its own
- off-topic cards (V5/V6)
- cards from another chapter (V4)
- no cards appearing for "Thanks!" (V7; evidence only)

## Addendum (planning, 2026-09-23; approved)

The suggestion chips are **fixed templates using the current page title**, not AI-generated (`app/api/chat-suggestions/route.ts:19-41`). This is the one clear way the open page influences the tutor interface.

## Redaction finding (2026-09-23)

The admin header renders the account's first name as one word (`medhavi-hub/components/AdminDashboard.tsx:578-580`). The toolkit's stock mask needs two or more capitalised words in list or card containers (`capture_admin.py:23, 37-40`), and its leak check counts only emails and codes (`:46`). So the stock driver would neither mask nor detect this name. The fix is planned in CAPTURE.md "Redaction".

## Pilot results (run-pilot, 2026-09-24): now locked in narration

| Check | Result | Narration impact |
|---|---|---|
| V1 | Verified: the cards and "Dive deeper into all sources (10)" are visible for about 0.3 s while "AI is thinking..." still shows | B06 says "They arrive just before the answer text starts." |
| V2 | Verified: N = 10. Only about 1.5 cards fit the panel width, because the row is clipped horizontally | B08 says "This opens all ten retrieved sources." **Never** say "three show at first." |
| V3 | Verified: the 5.4.2 Gene Amplification card opens the 5.4 page, and "On this page" leads to 5.4.2. The card snippet matches the section's first sentence. | B09 is included |
| V4 | Verified: the source is on 5.4 while 5.1 was open; other cards come from Chapter 12 and Chapter 25 | B09 says "a different page from the one I was reading" |
| V5 | Verified: "Naked Antibodies" (Chapter 25) and "Angiopoietin Functions in Angiogenesis" (Chapter 12) appeared for a gene-amplification question | B08: "Some can be less relevant than others, another reason to open them and check." Kept low-key, not framed as a defect. |
| V6 | **Still conditional.** The follow-up's reply top was off-screen. The answer visibly built on the first one (HER2 example). | B11 stays at its base wording |
| V7 | Verified: "Thanks!" got no source cards | Not narrated; evidence only |
| V8 | Verified: no "Most Relevant" badge; the URL stayed on 5.1 | Not narrated |
| V9 | Verified: the footer warning is legible | B05, B12 |
| V10 | Verified: chips read "Explain 5.1 Introduction to Oncogenes in simple terms." and so on | B05 |
| M1 | No visible memory interference: the panel started empty and neither answer referred back to earlier turns | — |

Also seen on screen, not narrated:
- The answer ends with the "do you want to learn more about this?" link and uses the phrase "Your sources mention".
- Asterisks show literally during streaming and in "*MYC*".
- The chat bubble button overlaps the send arrow.

All of these must be re-confirmed against `run-book`.

## Corrected landscape capture (run-book, 2026-09-24)

- **Redaction:** clean.
  - The header reads "Admin account" from its first rendered frame (about 1.6 s) until it scrolls out of view (about 11 s).
  - Only textbook cards and aggregate counts appear on screen. No names, emails or codes.
- **Consistent with the pilot:**
  - V1: the cards and "Dive deeper (10)" arrive about 0.2 s before the answer text.
  - V2: N = 10.
  - Same first cards: Naked Antibodies, then 5.2.2.
  - V3/V4: the card opens 5.4, and "On this page" leads to 5.4.2.
  - V8: no badge and no automatic page switch.
  - V9: the footer is legible.
  - V10: chips follow the page title.
- **V6: VERIFIED.**
  - The follow-up question and reply are on screen.
  - New cards: "Angiopoietin Functions in Angiogenesis" (Chapter 12) and "The Two-Hit Hypothesis" (Chapter 4), plus "Dive deeper (10)".
  - The reply builds on the first answer: "Yes — here's a simpler way to think about gene amplification", followed by a gas-pedal analogy.
- **M1:** no visible reference to the pilot conversation in either answer.
- **Streaming:** it types visibly for about 1.5 s. Then the rest of the first answer appears at once, and the panel jumps to its end. The same thing happened in the pilot.

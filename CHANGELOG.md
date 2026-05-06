# CHANGELOG — 2nd Grade Vocab Trainer

Reverse-chronological release history. Going forward, update on each substantive change. Earlier history (pre-2026-04-11) lives only in `git log`.

## 2026-05-06 — Activity Game polish (granularity, sound, ergonomics)
- **Multi-select units**: replace the single-pick dropdown / range chip with a 5×3 grid where every unit is individually toggleable. Quick-chips now act as bulk shortcuts (All / None / U1–4 / 5–8 / 9–11 / 12–15) over the same multi-select state. Each cell shows the unit number + total word count.
- **Multi-select modes**: Draw / Show / Explain are independent toggles (≥1 required). Picking just one runs single-mode; picking 2 or 3 mixes them with the per-word category cue at play time. Removes the redundant "Mix" tile.
- **Game length picker**: 3 / 5 / 8 / ∞ rounds per group. Game ends when every group has played the configured number of rounds, OR when the pool runs dry. Pick-screen shows "round N of M" progress.
- **Better-spaced action buttons**: large 84-px Correct + Skip side-by-side (was three buttons cramped together with Undo). Undo moved to its own subtler row below — no more accidental tap during the heat of the round.
- **Richer sound effects**: coin-pickup ascending arpeggio for Correct (G5→C6→E6→G6 with octave doubling), descending whoosh + low-pass noise for Skip, double-tick beep for the countdown, klaxon-style time-up buzzer (C#4→A#3→G3 saw + square layered with noise burst), 5-note triumphant fanfare for the time bonus, plus a soft 3-note chime when a round starts and a held major-7 chord on the final screen.
- Word-count availability indicator now shows breakdown for active modes only (e.g. "Draw 76 · Show 41" if Explain is off).

## 2026-05-06 — Activity Game mode
- New sibling app at `activity/` — teacher-orchestrated group game, three modes: **Draw It** ✏️ / **Show It** 🎭 / **Explain It** 💬, plus **Mix** with per-word category cue.
- Setup screen: ≥2 group names, time-per-round picker (30 / 60 / 90 s), mode picker, unit scope (All / single unit / range chips for U1–4 / 5–8 / 9–11 / 12–15), live "words available" counter, optional time-bonus toggle (+1 if a group clears all words before time runs out).
- Group scoring with two-stage tie-break (correct-total then skip-total) and 🤝 Tie badge.
- 605 MORE 2 vocab entries categorized via the new `TOOLS/activity-audit/` tooling: print-card categorization joined to `vocabData`, A1+/A2 lens heuristic flagged 45 entries, 26 high-confidence flips applied (school subjects, possessive pronouns, units of measure, etc.), 19 medium-confidence cases logged for explicit teacher review in `TOOLS/activity-audit/TEACHER_REVIEW.md`.
- Mobile-friendly: dark theme for projector use, prevent-pull-to-refresh, audio context unlock, ARIA-live timer.
- Home-screen card "🎯 Activity Game" links to `activity/`. No login / Firebase / XP — pure classroom group game with `localStorage` history (last 20 games).

## 2026-05-01 — Phase 0 polish (cross-grade)
- Fix stray "60" timer always visible at top of Komplett / Sprint / MC / Flashcards (`speed-timer-wrap` is now properly hidden when not in Speed Round).
- Fix XP-for-zero-correct exploit: ending a session with no correct answers now awards 0 XP instead of streak-bonus + perfect-round bonuses.
- Results page: show a friendly placeholder when a session ended without any attempted words, instead of a blank `RESULTS` box.
- Word Hunt failure UX softened: 2 mistakes allowed per round before the round ends (was 1). After the first wrong tap, a "Wrong — 1 try left!" / "Falsch — du hast noch 1 Versuch!" message shows.
- Same fix-set applied across G1 (already shipped), G2, G3, G4. Identifies shared code patterns; future copy-paste between grades is now lower-risk.

## 2026-04-19 — U12 + bugfix sweep
- Fix Spelling Bee auto-click + results navigation
- U12 matching task rebuild
- Verb Table mode added (initially for U12 Present Perfect)
- G2 grammar fixes (U12 Present Perfect)

## 2026-04-18 — Polish
- Normalize grammar-home subtitle to "Choose topics and exercise type"
- Accept single-word corrections in error-correction word-selection mode

## 2026-04-14 — Vocab arcade
- New: Memory Match, Spelling Bee, Word Hunt — curated VOCAB_TASKS per unit
- Unified context/definition types with progressive 2-tier Hint button (XP penalty)

## 2026-04-13 — Grammar arcade additions
- Group Sort, Matching Pairs, Anagram added to grammar arcade
- Chat-sim campaign renderer
- Campaign card uses dynamic level count
- XP burst + combo tier-up animations across vocab + grammar modes (with German labels)
- Distractors added to 94 reclassified gap-fill items (proper MC instead of typed input)
- Fix: gap-fill items without distractors fall back to typed input
- Fix: `saveSessionResults` flashcard-status preservation scoping bug

## 2026-04-12 — Flashcards, level badge, mode switch
- Tinder-style flashcard layout (multiple iterations)
- Flashcard tracking + dictionary integration ("Wörterbuch & Karteikarten")
- Flashcard status persistence across page refreshes
- G2 grammar renderers: error correction, matching, MC prompt cleaning
- Mode switch button restored on home screen and added to profile card
- Level badge: bigger + shadow, fix stuck popup
- Critical CSS fix: brace imbalance from leftover `ow)}` on `obPulse` keyframe
- Dark-mode contrast fix: replaced hardcoded `#fff` with `var(--card-solid)` on full-width cards

## 2026-04-11 — Audit & cleanup
- Vocab audit fixes (9 CRITICAL + 27 HIGH issues in G2)
- Fix 91 misclassified gap-fill items (tf → transformation, ff → free-form, qf → question-formation)
- Fix 10-item cap on specific topic selection (now up to 25 items)
- Add Unit 1 review card to grammar practice (By Topic view)

## Earlier
Initial buildout from G3 template, vocabulary curation (~611 items across 15 units), Word Files merged into parent units. See `git log` for raw history.

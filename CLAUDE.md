# CLAUDE.md — 2nd Grade Vocab Trainer (G2)

Internal docs for Claude Code sessions and future maintainers. For users see [README.md](README.md). For workspace-wide rules see [`../DOMIGO.md`](../DOMIGO.md).

## Architecture

Single-file SPA: HTML, CSS, JS, and vocab data bundled into `index.html`. Campaign content has been extracted into `data/m2-campaign.{js,json}`. No build pipeline, no module system. Edit → commit → push → GitHub Pages serves it (~30s).

- Total: ~15,323 lines
- `const vocabData = {` starts at line **3517**

## File layout

```
2nd-grade-vocab-trainer/
├── index.html         ← entire app (HTML + inline CSS + inline JS + vocabData)
├── avatars/           ← 50 PNG avatars
├── campaign/          ← story-mode assets (g2-prologue, g2-setting-* scenes)
├── data/
│   ├── m2-campaign.js
│   └── m2-campaign.json
└── README.md, CLAUDE.md, CHANGELOG.md
```

## Modes shipped

**Practice modes:** Full, Sprint, Speed Round, Multiple Choice, Flashcards.

**Exercise types:** Context (easy/hard), Definition (easy/hard), Translation, Mix.

**Vocab arcade** (curated per-unit, A1+/A2):
- Memory Match, Word Hunt, Spelling Bee
- Group Sort, Matching Pairs, Anagram (Wordwall-inspired)
- **Verb Table** — added 2026-04-19 for U12 (Present Perfect)

**Grammar arcade:** chat-sim campaign renderer, group-sort / matching-pairs / anagram task types.

**Live multiplayer:** Battle Arena, Class Quiz.

## Firebase

- Project: `veho-vocab`
- Realtime DB: `https://veho-vocab-default-rtdb.europe-west1.firebasedatabase.app`
- Firestore path: `classes/<CLASS_ID>/students/<slug>/`
- `let CLASS_ID = null;` — set per class during login.

## Deploy

Push to `main` → GitHub Pages → https://veho-domi.github.io/2nd-grade-vocab-trainer/. No CI, no build step.

## Conventions (the things that have bitten us)

- **Language level is A1+/A2 — the youngest cohort. Use the simplest English possible.** Definitions ~6–12 words, no abstract phrasing. Context sentences 6–15 words, present/past simple, basic modals only. No conditionals, passives, relative clauses, or perfect tenses except where the unit explicitly teaches them.
- **Definitions must not leak the headword.** Never use content words from `w` in `d`.
- **Context sentences must be original.** Never copy the textbook example.
- **German `g` field is verbatim from textbook.** MORE! 2 is the source of truth.
- **`cf` field only when needed.** Use only if sentence form differs from headword.
- **Verb forms must vary** — past tense, 3rd person, -ing forms too, not just infinitive.
- **Word File entries** are merged into their parent unit (no separate "Word Lists" section).
- **Single-file edits at scale.** For mass vocab changes, split file into 3 parts and concatenate.
- **Always `git pull` before editing.**

## Vocabulary source

`Domi Gym 2025:26/2A (2025:26)/MORE 2 Materials & Resources /` — note trailing space in folder name. Full vocab list is `Full Vocabulary List MORE 2 Units 1-15.docx` in that folder. Extract verbatim, do not hallucinate.

## Known issues / TODOs

- U12 (Present Perfect) had a recent matching rebuild + verb-table addition (2026-04-19) — verify pedagogy holds for newer units.
- Long-term: fold into unified DomiGo app (G1–G4 single login → grade → class → profile).

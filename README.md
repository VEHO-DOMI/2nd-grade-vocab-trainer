# DomiGo — 2nd Grade Vocab Trainer

EFL vocabulary trainer for 2nd-grade (2A) students at Gymnasium der Dominikanerinnen, based on **MORE! 2** (CEFR **A1+/A2**).

**Live:** https://veho-domi.github.io/2nd-grade-vocab-trainer/

## What it does
Practice modes (Sprint, Speed, Multiple Choice, Flashcards, Full Run) and arcade mini-games (Memory Match, Word Hunt, Spelling Bee, Group Sort, Matching Pairs, Anagram, Verb Table). Grammar arcade with chat-sim campaign renderer. Battle Arena and Class Quiz support live multiplayer.

## Tech
Single-file vanilla HTML/JS app (`index.html`, ~15.3K lines), with `data/m2-campaign.{js,json}` for campaign content. Firebase (`veho-vocab` project) for student data. GitHub Pages for deployment. No build step.

## Workspace
Part of the DomiGo workspace. See [`../DOMIGO.md`](../DOMIGO.md) for the full inventory and workflow rules. See [`CLAUDE.md`](CLAUDE.md) for internal architecture and conventions, and [`CHANGELOG.md`](CHANGELOG.md) for release history.

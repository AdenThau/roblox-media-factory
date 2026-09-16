# Roblox Media Factory

Automation-first Russian kids/family gaming media studio focused on **VK Видео + RUTUBE**.

## Business objective

Build a low-touch content system where original gaming episodes are produced automatically, distributed on Russian video platforms, measured, and iterated based on recommendation and monetization signals.

The first business model is intentionally simple:

**original videos → platform recommendations → views/watch time → platform revenue share**

YouTube, bookmakers/casinos, affiliate offers, and a proprietary Roblox place are **out of scope for Phase 1**. They may be tested later only if the core content economics work.

## Initial content thesis

- Russian-language
- family-safe / kids gaming entertainment
- Roblox-first, with Minecraft as a later adjacent test
- horizontal master episodes, initially ~2.5–5 minutes
- strong story, clear characters, frequent visual/story events
- original production only; no reuploads or copyrighted cartoon/TV footage

## Recommendation thesis

We optimize for signals the platforms publicly describe:

### VK Видео
- originality
- viewer watch/dwell behavior
- low skip behavior
- completion / continued watching
- subscription after viewing
- returning audience
- likes, comments, reposts and other positive interactions
- semantic match between title, thumbnail, audio/video content and viewer interests

VK says its 2026 recommendation updates can surface original creators from their first publications regardless of community size.

### RUTUBE
- user actions: likes, shares, subscriptions, comments
- viewing history and time spent watching
- metadata relevance: title, description, category
- views over time
- channel-level horizontal-video metrics: views, watch time, viewing depth

## Current phase

**SPEC-001 — Russian horizontal pilot episode + reusable production pipeline**

The previous short-form YouTube/TikTok prototype has been retired before implementation.

## Operating model

- Strategy/research: ChatGPT + owner strategic review
- Engineering/execution: Codex
- Source of truth: this repository
- Owner involvement target: credentials/KYC and strategic approvals only

## Repository layout

- `specs/episodes/` — approved episode specifications
- `research/` — platform/recommendation notes
- `src/` — reusable production automation
- `content/` — declarative episode configs
- `output/` — output manifests/links and lightweight deliverables
- `analytics/` — experiment schema and later performance results
- `PROJECT_STATE.md` — current task, constraints and next checkpoint

## Codex execution rule

Always read `PROJECT_STATE.md` first. Execute only the currently approved spec. Make non-critical engineering decisions autonomously and document them. Do not expand scope into mass production, publishing automation, channel creation, paid APIs or additional platforms unless the current spec explicitly requests it.

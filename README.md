# Yandex Games Lab

> Repository name is legacy. The active project is now a **Yandex Games HTML5 game experiment**, not a Roblox media factory.

## Business objective

Build small browser-game hypotheses cheaply, publish them to Yandex Games, and use real platform metrics to decide **KILL / ITERATE / SCALE**.

Current monetization model:

**Yandex recommendations → players → ad views / rewarded ads / later in-app purchases → RUB payouts**

## Current hypothesis

### `Купи склад: найди клад`
A storage-auction / resale progression game inspired by proven loot, rarity, tycoon and trading loops, but adapted to the older Yandex Games audience.

Core loop:

`choose storage → bid against NPCs → reveal loot → appraise/repair → sell → upgrade → buy more valuable storage`

## Why this project is intentionally small

The first build is an MVP, not a finished game. It exists to test whether the loop can retain real users before spending more engineering time.

Do **not** build multiplayer, 3D worlds, complex backend infrastructure, social systems, clans, battle passes, live ops, hundreds of levels, or a portfolio generator in Phase 1.

## Technical direction

- HTML5 browser game
- TypeScript
- lightweight DOM/Canvas approach; no heavy engine unless clearly justified
- responsive desktop + mobile
- Yandex Games SDK integrated behind a small adapter
- game build must be publishable as a ZIP with `index.html` in the archive root
- no required third-party login
- local dev must work without Yandex SDK through a mock/fallback adapter

## Repository layout

- `specs/yandex-games/` — approved game specifications
- `src/` — game source
- `public/` — static assets
- `data/` — items/storage/economy configuration
- `tests/` — lightweight automated tests for economy/core logic
- `dist/` — production build (generated)
- `PROJECT_STATE.md` — current approved task and hard scope limits

## Codex operating rule

Always read `PROJECT_STATE.md` first, then execute only the currently approved spec. Make routine engineering decisions independently. Do not expand scope because an idea seems useful.

The owner should only be needed later for Yandex developer-console actions, KYC/monetization details, and strategic approval after the MVP is playable.

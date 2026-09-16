# Project State

## Active project
**Yandex Games Lab**

The repository name is legacy. Roblox/video production is no longer the active business hypothesis.

## Business model under test
Create a small HTML5 game for Yandex Games and monetize through Yandex-supported advertising first, with in-app purchases considered only after retention is proven.

Target loop:

**platform recommendations → play sessions → retention → ads/rewarded ads → RUB revenue**

## Current hypothesis
**Купи склад: найди клад** — storage auction + loot rarity + appraisal/repair + resale + progression.

The mechanic borrows proven behavioral loops from successful collection/tycoon/trading games without copying a specific game, brand, art style or copyrighted assets.

## Current approved task
Execute only:

`specs/yandex-games/001_storage_auction_mvp.md`

## Hard goal for Phase 1
Produce a locally playable and Yandex-ready MVP that proves the core loop is fun enough to test with real players.

The MVP must include:
- auction against simple NPC bidders;
- storage-unit selection;
- randomized loot reveal;
- item rarity/condition/value;
- sell vs repair decisions;
- progression/upgrades;
- save/load;
- Yandex SDK adapter;
- rewarded-ad integration point;
- fullscreen-ad integration point at a logical break;
- responsive desktop/mobile UI;
- production ZIP/build instructions.

## Hard scope exclusions
Do NOT build yet:
- Roblox anything;
- video/media pipeline;
- multiplayer;
- 3D world;
- backend/server architecture;
- clans/friends/chat;
- battle pass;
- live ops/calendar events;
- hundreds of handcrafted items;
- paid APIs;
- external databases;
- analytics dashboard beyond simple event hooks/logs;
- in-app purchases unless required by the spec (they are not required in SPEC-001);
- automatic publishing;
- a generator for many games.

## Engineering principles
1. Prefer the simplest architecture that can ship.
2. Use data-driven JSON/TS configuration for items, storage tiers and upgrades.
3. Local development must work without real Yandex SDK using a mock adapter.
4. No fake completion: if Yandex console credentials or manual publishing are required, document the exact remaining step.
5. Do not ask the owner about routine implementation choices.
6. Escalate only for credentials, money, legal/platform risk, or a material strategy change.
7. Stop after SPEC-001 is complete.

## Owner involvement target
Minimal. The owner should not supervise coding. Later unavoidable owner steps may include creating/filling the Yandex Games developer profile, accepting contracts/KYC, uploading the ZIP and pressing publish/moderation controls.

## Completion report required from Codex
At the end report only:
- PLAYABLE BUILD PATH
- HOW TO RUN LOCALLY
- YANDEX-READY ZIP PATH
- IMPLEMENTED CORE LOOP
- IMPLEMENTED MONETIZATION HOOKS
- TESTS / BUILD STATUS
- MANUAL YANDEX-CONSOLE STEPS REMAINING
- TOP 3 RISKS OR WEAKNESSES

## Status
READY FOR CODEX

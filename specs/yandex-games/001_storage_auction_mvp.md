# SPEC-001 — «Купи склад: найди клад» MVP

**Status:** APPROVED  
**Priority:** P0  
**Platform:** Yandex Games  
**Language:** Russian  
**Game type:** HTML5 browser game  
**Goal:** ship a small playable MVP for real platform testing, not a finished commercial game.

## 1. Product hypothesis

Build a storage-auction / resale progression game for the older Yandex Games audience.

Core fantasy:

> Start with little money, gamble intelligently on abandoned storage units, discover valuable or worthless objects, repair good finds, resell them for profit, upgrade your abilities, and gain access to more expensive auctions.

Core loop:

`choose storage → inspect limited hints → bid against NPCs → open storage → reveal loot → sell or repair → receive money → buy upgrades → next day`

The game should deliver a meaningful decision or reveal frequently. Avoid passive waiting mechanics in this MVP.

## 2. Hard technical constraints

Use the simplest shippable web stack:

- TypeScript
- Vite
- plain DOM/CSS and lightweight Canvas/SVG only where useful
- no 3D engine
- no backend
- no external database
- no React unless there is a strong concrete reason
- no paid API

The production game must:

- run in a browser;
- work on desktop and mobile;
- integrate Yandex Games SDK through a small adapter;
- run locally when Yandex SDK is absent using a mock adapter;
- produce a static production build suitable for ZIP upload;
- have `index.html` at the root of the upload ZIP;
- keep the unpacked upload comfortably below 100 MB;
- use only Latin characters/no spaces in file and folder names inside the build;
- require no third-party registration/login.

Do not depend on external runtime assets/CDNs for core gameplay.

## 3. MVP gameplay

### Starting state

Player starts with:

- cash: `5000 ₽`
- day: `1`
- level/reputation: basic
- no upgrades

### Daily auction

Each in-game day presents **3 storage units**.

Each storage displays limited pre-auction information such as:

- storage tier;
- approximate size;
- 1–2 visible item hints;
- opening bid.

The contents and true value remain uncertain.

### Auction mechanic

Implement a quick auction against 1–3 NPC bidders.

Player controls:

- `+100 ₽`
- `+500 ₽`
- `ПАС`

NPCs have hidden maximum willingness-to-pay derived from the generated warehouse value plus noise/personality.

Rules:

- player cannot bid money they do not have;
- auction should usually resolve within ~10–30 seconds;
- losing an auction must not soft-lock the day; player can try another available unit where appropriate;
- after winning, purchase price is deducted immediately.

### Loot reveal

A storage contains roughly **3–6 items**.

Reveal them sequentially with simple animation/sound/UI feedback.

Each item has data fields such as:

- id
- name
- category
- rarity
- condition
- baseValue
- repairable
- repairCostRange
- repairValueMultiplier
- icon/visual key

Suggested rarity:

`common / uncommon / rare / epic / legendary`

Suggested categories:

- electronics
- tools
- collectibles
- furniture
- hobby equipment
- auto parts
- mystery/oddities

Create approximately **40–60 original generic items** in data/config. Do not use real trademarks or copyrighted franchise assets.

Examples:

- старый фотоаппарат
- набор инструментов
- винтажные часы
- коробка виниловых пластинок
- игровая приставка без бренда
- проектор
- коллекционная модель автомобиля
- запечатанный ящик

### Item decision

For each relevant item allow:

**SELL NOW**

or, if repairable:

**REPAIR → SELL**

Repair:

- costs cash;
- improves expected sale price;
- may have modest uncertainty but must never feel arbitrarily punitive;
- cannot be started if player cannot afford it.

Selling converts item value into cash immediately for MVP simplicity.

### Progression

Implement at least 5 upgrade tracks or upgradeable abilities using simple levels:

1. **Flashlight** — reveals more pre-auction hints.
2. **Appraisal skill** — narrows displayed estimated value ranges.
3. **Workshop** — reduces repair costs.
4. **Market contacts** — improves sale offers modestly.
5. **Reputation** — unlocks higher-tier storage auctions.

The first useful upgrade should be affordable within the first few successful game days.

Player should clearly feel:

`small cheap storage → better decisions → more cash → better storage → rarer loot`.

## 4. Economy requirements

Put tunable economy values in config/data rather than scattering magic numbers through UI code.

The economy must support quick automated simulation.

Add a simple simulation/test utility capable of running at least 1,000 synthetic game-days to catch:

- runaway negative cash;
- impossible progression;
- NaN/infinite values;
- broken repair economics;
- impossible auction states.

Do not spend time perfectly balancing the game. Aim for a playable initial curve.

Suggested target feel, not a guaranteed formula:

- first upgrade: within ~2–5 successful days;
- occasional loss should be possible;
- rare jackpot should feel exciting but not destroy progression;
- higher tiers should increase both risk and upside.

Use a seedable RNG so tests are reproducible.

## 5. Yandex SDK adapter

Create one small module/interface encapsulating platform calls so gameplay code is not coupled to global SDK objects.

It should support at minimum:

- SDK initialization;
- pause/resume hooks around ads;
- fullscreen advertisement request;
- rewarded-video request;
- basic save/load abstraction;
- environment detection / local mock implementation.

Local development must continue to work if Yandex SDK is unavailable.

### Rewarded ad placement

Implement **one useful optional rewarded placement**:

`Дополнительный осмотр склада`

Before bidding, player can voluntarily watch rewarded video to reveal one additional useful hint/item silhouette/value clue.

Rules:

- user initiates it explicitly;
- reward is granted only on successful rewarded completion callback;
- declining/not having an ad cannot block gameplay.

### Fullscreen placement

Create one fullscreen-ad request at a natural break such as after completing a game day and pressing `Следующий день`.

Do not show it during active bidding, loot decisions, or repair actions.

Use a conservative local cooldown/eligibility rule (for example, do not request on the first day and do not spam requests); Yandex may additionally control actual frequency.

All ads must go through Yandex Games SDK. No third-party ad blocks or embedded advertiser creatives.

## 6. Saving

Save at minimum:

- cash
- day
- upgrade levels
- unlocked storage tier / reputation
- simple lifetime stats
- schema version

Use the Yandex adapter when available and a localStorage fallback for local development.

Handle missing/corrupt/old save data safely.

## 7. UI / UX

The game must be understandable without a tutorial wall.

Required screens/states:

1. Main/start screen
2. Auction selection
3. Active auction
4. Storage opening / loot reveal
5. Item sell/repair decisions
6. Upgrade screen
7. End-of-day summary

First minute objective:

A new player should reach the first meaningful auction quickly, ideally without reading more than a few short lines.

Responsive requirements:

- playable with mouse and touch;
- buttons comfortably tappable;
- no essential hover-only interaction;
- support common phone portrait/landscape and desktop widths gracefully, while choosing one primary layout if necessary.

Visual direction:

- clean illustrated auction/storage theme;
- readable Russian typography;
- satisfying rarity colors/effects can be implemented through CSS;
- original simple SVG/CSS assets are fine for MVP;
- no copyrighted game assets, logos or real-world brand trademarks.

Do not spend excessive time on art polish before the loop works.

## 8. Audio

Audio is optional for the first implementation pass, but if added use only original/generated/public-domain/permissively licensed assets committed or documented appropriately.

Never make audio required for understanding gameplay.

## 9. Lightweight telemetry hooks

Do not build an analytics backend.

Create an internal event interface that currently logs/records events and can later be wired to platform analytics.

At minimum emit:

- game_start
- storage_selected
- rewarded_inspection_requested
- rewarded_inspection_completed
- auction_won
- auction_lost
- storage_opened
- loot_revealed
- item_repaired
- item_sold
- upgrade_bought
- day_completed

Include useful values such as day, cash, bid price, item value and storage tier where appropriate.

## 10. Tests / quality gates

Before completion:

- `npm install` succeeds;
- production build succeeds;
- automated tests pass;
- game can complete at least 5 in-game days without soft-lock;
- player cannot spend more cash than available;
- save/load works locally;
- SDK absence does not break local play;
- ad callbacks cannot grant duplicate rewards;
- core UI works at desktop and mobile viewport sizes;
- upload ZIP/build structure satisfies the documented Yandex static-build requirements;
- no external copyrighted assets were used.

Prefer a few meaningful unit tests over a large testing framework.

## 11. Deliverables

Create/commit:

- complete source code;
- package scripts for dev/test/build;
- game data/config;
- tests/economy simulation;
- Yandex SDK adapter + mock;
- README with exact local-run instructions;
- `docs/YANDEX_PUBLISHING.md` with only the manual console steps still required;
- `docs/MVP_NOTES.md` with architecture, limitations and next best product improvements;
- a script such as `npm run package:yandex` that produces a Yandex-ready ZIP if practical in the environment.

Do not require the owner to manually copy files around for normal development.

## 12. Explicitly out of scope

Do NOT implement:

- multiplayer;
- 3D graphics;
- backend/server;
- accounts beyond Yandex SDK support;
- leaderboards;
- achievements;
- in-app purchases;
- daily rewards;
- quests;
- live events;
- clans/chat/social graph;
- English localization;
- hundreds of items;
- advanced analytics dashboard;
- procedural AI content generation;
- automatic publishing;
- portfolio/game factory infrastructure.

Do not add these because they might be useful later.

## 13. Codex autonomy and stop condition

Do not ask the owner about routine technical choices. Choose sensible defaults and keep moving.

Only stop/escalate before completion if blocked by:

- required credentials;
- unavoidable paid service;
- meaningful legal/platform-policy issue;
- inability to create a functioning build.

Otherwise finish the MVP.

After SPEC-001 is complete, **STOP**. Do not start polishing, marketing, SPEC-002 or another game.

Final response should be compact and contain only:

1. `PLAYABLE BUILD`
2. `HOW TO RUN`
3. `YANDEX ZIP`
4. `WHAT WORKS`
5. `TEST STATUS`
6. `MANUAL OWNER STEPS`
7. `TOP 3 RISKS`

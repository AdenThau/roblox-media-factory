# SPEC-001 — Запретная дверь

**Status:** APPROVED FOR PROTOTYPE  
**Priority:** P0  
**Primary platforms:** VK Видео + RUTUBE  
**Language:** Russian  
**Audience:** family-safe school-age gaming audience (not preschool)  
**Master format:** 16:9 horizontal, 1920×1080 minimum  
**Target duration:** 2:30–4:00

## 1. Objective

Create one original Russian Roblox story episode through a reusable, automation-first production pipeline.

This prototype must test two things at once:

1. Can the content itself be paced for recommendation signals on VK Видео and RUTUBE?
2. Can episode #2 be produced mostly by changing declarative story/config data rather than rebuilding the pipeline?

Do not optimize for YouTube Shorts. Do not create a mass generator yet.

## 2. Recommendation requirements

Read `research/RECOMMENDATION_SIGNALS.md` before implementation.

The episode should be deliberately designed around:

- immediate story promise inside the first 5 seconds;
- no logo/intro before the hook;
- a meaningful visual/story event at least every ~10–25 seconds;
- escalating stakes;
- a midpoint reversal/reveal;
- clear climax and payoff;
- minimal dead air;
- a coherent title/thumbnail/story semantic match;
- an ending that completes the story but can naturally lead to another episode later.

Do not invent platform thresholds. We will measure them after publication.

## 3. Episode concept

Working title:

**БЭКОН НАШЁЛ ДВЕРЬ, КОТОРОЙ НЕ ДОЛЖНО БЫТЬ В ROBLOX**

Alternative title candidates:

- **Я ОТКРЫЛ ЗАПРЕТНУЮ ДВЕРЬ В ROBLOX…**
- **ЭТА ДВЕРЬ ПОЯВИЛАСЬ В МОЁМ ДОМЕ НОЧЬЮ**

Core story:

A Bacon Hair character notices a door inside his home/base that did not exist before. The door leads to an impossible copy of his world. Each room contains evidence that another version of him has already been there. Eventually he meets his duplicate, learns that the duplicate was trying to escape into the original world, and must close the door before the duplicate replaces him.

Tone:
- mystery/adventure;
- light suspense;
- funny reactions;
- no graphic horror;
- family-safe.

## 4. Story structure

### 0:00–0:05 — Hook

Start on the impossible door immediately.

Visual:
Bacon stands in front of a door embedded in a wall where there was no doorway before.

Voice/narration example:

`Вчера этой двери здесь НЕ БЫЛО. А сейчас из-за неё кто-то стучит.`

Three knocks.

No intro. No channel logo.

### 0:05–0:25 — Decision

Bacon checks around the door, jokes that opening it is obviously a terrible idea, then opens it anyway.

The space behind the door is a distorted copy of his house/base.

Immediate visual contrast is required.

### 0:25–0:55 — First anomaly

He enters.

Small differences:
- furniture mirrored;
- clock moving backward;
- duplicated object;
- lights flickering;
- a sign/note that looks like it was written by him.

Note:
`НЕ ИДИ ДАЛЬШЕ.`

Bacon insists he never wrote it.

### 0:55–1:25 — Escalation

The door behind him disappears.

He finds footprints / items belonging to his avatar.

A distant silhouette crosses the corridor.

Use one humorous reaction beat so the episode is not pure horror.

### 1:25–1:55 — Midpoint reveal

He discovers a room containing multiple versions of familiar items and a second Bacon seen through glass / across a room.

At first the duplicate behaves identically, mirroring him.

Then it moves independently.

### 1:55–2:30 — Confrontation

Duplicate says a concise line such as:

`Наконец-то ты открыл дверь.`

The viewer learns that the duplicate has been trapped and wants Bacon's place in the normal world.

Duplicate begins moving toward the exit point / newly reappeared door.

### 2:30–3:10 — Chase / climax

Bacon races to the door.

Use fast scene changes, camera movement and a clear objective.

Bacon reaches the door first and begins closing it while duplicate tries to cross.

### 3:10–3:30 — Payoff

Door shuts.

Everything returns to normal.

Bacon relaxes.

Then notices one small impossible detail suggesting uncertainty — for example his reflection moves half a second late.

Final line:

`Стоп… а я точно закрыл ПРАВИЛЬНУЮ дверь?`

End immediately after reaction.

Target final duration may vary within 2:30–4:00 depending on pacing. Do not pad the story merely to hit a number.

## 5. Visual production strategy

Prefer native Roblox/Roblox Studio scenes and original gameplay-style visuals over expensive full text-to-video generation.

Create reusable assets where practical:

- normal room/base;
- distorted/mirror version;
- door prop and animation;
- Bacon protagonist;
- duplicate variant;
- basic reaction animation set;
- reusable camera moves;
- lighting presets;
- glitch/distortion transition.

Recurring assets are desirable because they reduce marginal cost for later episodes.

## 6. Declarative episode config

Create a machine-readable config such as:

`content/episode_001.json`

It should contain at minimum:

- episode_id
- language
- target_duration
- title_candidates
- characters
- scenes
- scene durations
- dialogue/narration
- camera instructions
- animation cues
- sound cues
- caption text
- lighting/environment changes
- transition cues

Goal: future episodes should be describable primarily through content data/specifications.

## 7. Reusable production architecture

Implement only what is useful for episode #2. Candidate components:

- SceneController
- CharacterController
- CameraController
- DialogueTimeline
- CaptionTimeline
- AudioTimeline
- LightingController
- TransitionController
- EpisodeRunner / deterministic playback

Prefer a small clean system over a large framework.

Provide deterministic controls:

- START_EPISODE
- RESET_EPISODE

If practical, make playback invokable programmatically for later capture automation.

## 8. Voice, captions and sound

Russian narration/dialogue.

Voice style:
- clear;
- energetic;
- natural;
- not preschool/baby voice;
- not excessively fast.

Captions:
- optional in the horizontal master if they harm the visual experience;
- if used, keep them concise and mobile-readable;
- always produce an SRT/subtitle file.

Audio:
- original, licensed, royalty-free or otherwise permitted assets only;
- no unauthorized popular music.

Use SFX for:
- knocking;
- door movement;
- reveal hits;
- light glitch;
- footsteps;
- chase/climax;
- final reflection twist.

## 9. Packaging prototype

Produce at least:

### Title candidates
3 strong Russian titles that accurately describe the actual episode.

### Thumbnail candidate
16:9 thumbnail concept or image if supported:
- protagonist clearly visible;
- impossible door clearly visible;
- duplicate/eyes/silhouette may be used as a secondary mystery element;
- minimal text, ideally 0–3 words;
- do not misrepresent content.

### Metadata
Draft:
- VK Видео title + description;
- RUTUBE title + description + proposed category;

Do not publish yet.

## 10. Analytics schema

Create `analytics/episode_metrics_schema.json` or equivalent with fields we expect to collect later.

At minimum:

- platform
- episode_id
- publication_timestamp
- impressions (if available)
- views
- views_24h
- views_72h
- views_7d
- total_watch_time
- average_watch_duration
- average_percentage_viewed / viewing_depth
- completion_rate if available
- early_exit / skip metric if available
- likes
- comments
- shares
- subscriptions/follows attributed if available
- returning_viewers if available
- revenue
- revenue_per_1000_views

Mark unsupported metrics as nullable; do not fabricate values.

## 11. Deliverables

Required repository deliverables:

1. Roblox project/source or reproducible scene source.
2. Reusable source code/modules.
3. `content/episode_001.json` or equivalent.
4. Final 16:9 episode `.mp4` **if the execution environment can genuinely render/capture it**.
5. Russian narration/dialogue assets or reproducible generation configuration.
6. Subtitle file.
7. Thumbnail candidate / source or exact generation spec.
8. Platform metadata drafts.
9. Analytics schema.
10. `AUTOMATION_NOTES.md`.
11. Run/build instructions.

If the environment cannot produce the final video or Roblox project file, do not fake completion. Produce the maximum reproducible source/config and state the exact remaining blocker and shortest owner action needed.

## 12. Automation notes

Document:

- what was automated;
- what still requires a person;
- the shortest exact manual steps remaining;
- which tool/app access is missing;
- approximate marginal work required for episode #2;
- what should be automated next only if the pilot is approved.

## 13. Quality gate

Before completion verify:

- hook/story promise is clear within 5 seconds;
- no intro delays the hook;
- episode remains visually active;
- story is understandable without external context;
- plot has escalation, midpoint reveal, climax and payoff;
- no unauthorized copyrighted media;
- output is original rather than a template slideshow;
- no accidental Roblox Studio UI appears in final capture;
- audio/dialogue are intelligible;
- metadata accurately matches the story;
- result is family-safe;
- reusable parts are documented.

## 14. Out of scope

Do not build or configure yet:

- mass production;
- publishing bots;
- VK/RUTUBE account creation;
- monetization/KYC;
- paid promotion;
- YouTube/TikTok/Reels;
- bookmakers/casino advertising;
- affiliate systems;
- proprietary Roblox place monetization;
- multilingual localization;
- hundreds of content variants.

## 15. Stop condition

After SPEC-001, stop.

Report only:

- ACTUAL OUTPUTS PRODUCED
- REPOSITORY PATHS
- FINAL VIDEO STATUS
- AUTOMATION NOTES
- MANUAL STEPS REMAINING
- ESTIMATED MARGINAL WORK FOR EPISODE #2
- RECOMMENDED NEXT ENGINEERING STEP

Do not proceed to another episode without approval.

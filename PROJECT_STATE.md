# Project State

## Project
Roblox Media Factory

## Current business model
Automated Russian-language kids/family gaming episodes for **VK Видео + RUTUBE**.

Primary monetization hypothesis:

**recommendation traffic → watch time/views → platform revenue share**

Do not depend on YouTube monetization, bookmakers/casinos, affiliate offers, or a proprietary Roblox place in the current phase.

## Current phase
**Prototype / SPEC-001**

## Approved content hypothesis
Create original Roblox story episodes for a Russian-speaking family-safe gaming audience, roughly school-age rather than preschool.

Initial master format:
- horizontal 16:9
- 1080p minimum
- Russian narration/dialogue
- target length ~2.5–5 minutes
- strong first 5 seconds
- story event/change roughly every 10–25 seconds
- reusable recurring characters and locations where practical

## Why this format
The project is now optimized around the recommendation and monetization mechanics of VK Видео and RUTUBE rather than Shorts.

Priority signals to engineer for:

### VK Видео
1. Originality.
2. Strong immediate relevance/hook; a VK long-video view is counted after 5 seconds, so the opening must earn the next segment.
3. Watch time and continued viewing.
4. Completion/depth.
5. Low skip/abandon behavior.
6. Subscription after viewing.
7. Returning viewers.
8. Positive interactions such as sharing, comments and likes.
9. Semantic consistency between title, thumbnail, audio/video and actual story.

### RUTUBE
1. Viewer actions: likes, shares, subscriptions and comments.
2. Viewing history and time spent on the video.
3. Relevant title, description and category.
4. Views over time.
5. For author levels and extra recommendation exposure, horizontal-content views, watch time and viewing depth matter.

## Current approved task
Execute:
`specs/episodes/001_forbidden_door_ru.md`

Read first:
`research/RECOMMENDATION_SIGNALS.md`

## Success condition for this phase
Produce one original Russian horizontal Roblox episode through a reproducible, automation-first pipeline and document:
- actual final deliverables;
- manual steps still remaining;
- estimated marginal effort for episode #2;
- which production components can be parameterized;
- exact analytics fields we will need after publication.

## Do NOT do yet
- mass production
- create hundreds of episodes
- automatic posting
- channel/account creation
- paid API purchases
- monetization/KYC setup
- YouTube/TikTok/Reels pipeline
- bookmaker/casino ads
- affiliate systems
- proprietary Roblox place/game monetization
- multi-language localization
- complex dashboard

## Operating rules
1. Codex reads this file first.
2. Codex reads the recommendation-signals note before implementation.
3. Codex executes only the approved spec.
4. Make non-critical technical decisions autonomously and document them.
5. Escalate only for money, credentials/KYC, meaningful legal/platform risk, or a material strategy change.
6. Prefer reusable automation over one-off manual work, but avoid premature infrastructure.
7. Never claim an output exists if the environment cannot actually produce it.
8. Do not proceed to SPEC-002 without approval.

## Owner involvement target
The owner should not supervise production. Desired owner actions are limited to strategic approval and later platform credentials/KYC where unavoidable.

## Next owner checkpoint
After SPEC-001, review only:
- final episode quality;
- whether the hook/story is understandable;
- automation notes;
- remaining manual bottlenecks;
- whether the marginal cost of episode #2 is low enough to justify a small live test.

## Status
READY FOR CODEX EXECUTION WHEN LIMITS ARE AVAILABLE

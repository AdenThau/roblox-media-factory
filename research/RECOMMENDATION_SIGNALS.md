# Recommendation Signals — VK Видео + RUTUBE

Last reviewed: 2026-09-16

This note contains only signals supported by current public platform material. Treat any precise thresholds not stated here as hypotheses to be measured experimentally.

## VK Видео

### Publicly confirmed signals / system behavior

1. VK's 2026 recommendation changes favor original creators. VK states that recommendations can connect from the first publications and can distribute original content to a broad audience regardless of community size.
2. VK describes high-quality content as original and engaging: viewers finish watching it, subscribe to the author after it, and return to the author.
3. VK's current recommendation stack analyzes cross-product user behavior including likes, reposts, comments, skips and other actions.
4. VK's Discovery stack analyzes the actual content, including title, thumbnail, audio and video, and uses multimodal models to understand story/meaning and content similarity.
5. Since early 2026, a long-form VK Видео view is counted after 5 seconds of watching. This is not itself a recommendation threshold, but it makes the first 5 seconds a critical measurement boundary.

### Engineering implications

- The first 5 seconds must immediately establish conflict/curiosity; no logos or slow setup.
- Thumbnail/title must accurately promise the story rather than bait a different topic.
- Episode pacing must protect watch time and viewing depth.
- Recurring characters/series can be useful because the system understands content/characters and returning behavior matters.
- Track at minimum: impressions if available, starts/views, watch time, average watch duration, average percentage viewed, completion, skips/early exits where available, likes, comments, shares, follows/subscriptions attributed after viewing, and returning viewers.

## RUTUBE

### Publicly confirmed recommendation inputs

RUTUBE's public recommendation rules state that its personalized feed uses:

- user actions on content: likes, shares, subscriptions and comments;
- content metadata such as title, description and category;
- viewing history;
- time spent watching a particular video;
- view counts across different time periods.

RUTUBE also has an author-level system that can grant additional recommendation exposure. For horizontal content, the level system is based on channel results including:

- views;
- watch time;
- viewing depth.

RUTUBE explicitly says Shorts do not count toward those author levels.

### Engineering implications

- Horizontal master episodes are the priority for this project.
- Title/description/category must be coherent and specific.
- Optimize for watch time and viewing depth, not only clicks.
- End each episode cleanly and later configure end-of-video recommendations to another relevant episode once a catalog exists.
- Track: views, watch time, average watch duration/depth, completion where available, likes/top reactions, comments, shares, subscriptions and view velocity over 24h/72h/7d.

## What we do NOT know publicly

Neither platform publishes a complete ranking formula or guaranteed viral thresholds.

Do not invent rules such as:
- '70% retention guarantees recommendations';
- 'X likes per 1000 views triggers a boost';
- 'posting at a specific minute guarantees reach'.

These must be learned from our own experiments.

## Working experiment principle

For each published episode, treat the algorithm as a sequence of tests:

1. Packaging earns an initial start/click.
2. The first seconds determine immediate abandonment vs continued viewing.
3. Story/pacing determine watch time and viewing depth.
4. Satisfaction signals (completion, subscription, share/comment/like, return behavior) determine whether the content deserves broader matching to similar viewers.
5. Metadata/content semantics help the platform find the correct audience.

Our advantage is not low competition. Our advantage must be **cheap iteration**: produce original episodes at low marginal cost, measure which hooks/story mechanisms retain viewers, kill weak formats and systematically reuse only the mechanisms that repeatedly work.

## Public source references

- VK Company, 2026-07-08: growth of original creators and recommendation changes favoring original content.
- VK Company, 2026-08-10: neural profile / real-time ranking based on likes, reposts, comments, skips and cross-product behavior.
- VK Company, 2025-11-17: Discovery multimodal content understanding across title, thumbnail, audio and video.
- VK Company, 2026-02-03: long-video view counted after 5 seconds.
- RUTUBE: Rules for recommendation technologies (`/info/recommendations/`).
- RUTUBE: Author levels FAQ (`/info/levels/`).

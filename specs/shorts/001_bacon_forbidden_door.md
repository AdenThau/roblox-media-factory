# SPEC-001 — A Bacon Hair Found a Door That Shouldn't Exist

**Status:** APPROVED FOR PROTOTYPE  
**Priority:** P0  
**Platforms:** YouTube Shorts / TikTok / Instagram Reels  
**Language:** English  
**Target length:** 25–32 sec  
**Format:** 9:16, 1080×1920, 30 or 60 FPS

## Objective
Create the first reproducible Roblox Short and a minimal production pipeline that can later generate many original videos with minimal additional engineering.

This is not only a one-off video task. Build it so the next similar Short requires as little manual work as practical.

## Concept
Working title: **A Bacon Hair Found a Door That Shouldn't Exist...**

Story:
1. Bacon Hair sees a door where no door should be.
2. He opens it.
3. An impossible space is behind it.
4. He enters.
5. The door disappears.
6. He encounters an identical copy of himself.
7. The copy says: “You shouldn't have opened it.”
8. Glitch/reset into a loopable final frame.

Emotional arc: curiosity → discovery → escalation → danger → twist.

## Timeline / shot list

### Shot 1 — 0.0–1.5s
Normal Roblox corridor/street. Bacon Hair stops at an impossible door.

- Camera: fast push-in
- On-screen text: `THIS DOOR WASN'T HERE BEFORE...`
- Voice: `This door wasn't here yesterday...`
- Goal: immediate visual anomaly + curiosity gap

### Shot 2 — 1.5–4.0s
Character approaches and tests the door. It initially does not react; lights subtly flicker.

- SFX: handle, low impact, subtle glitch
- Voice: `So obviously... I opened it.`

### Shot 3 — 4.0–7.0s
Door opens into an impossible space: dark endless room, floating platforms, strange lighting, or impossible geometry.

- Camera: reveal
- Voice: `Yeah... that was mistake number one.`

### Shot 4 — 7.0–12.0s
Bacon Hair enters. Door closes. He turns around. The door has vanished; only a wall remains.

- On-screen text: `WAIT...`
- SFX: slam + bass hit
- Voice: `Wait. Where did the door go?`

### Shot 5 — 12.0–18.0s
A still silhouette is visible in the distance.

- Camera: subtle zoom
- Voice: `Then I saw someone.` / pause / `He wasn't moving.`

### Shot 6 — 18.0–23.0s
The silhouette is revealed as an identical Bacon Hair with matching clothing, facing away.

- Voice: `Why does he look exactly like me?`
- SFX: heartbeat / tension rise

### Shot 7 — 23.0–27.0s
The copy slowly turns around.

- Line/caption: `You shouldn't have opened it.`
- Keep horror mild; no graphic content.

### Shot 8 — 27.0–30.0s
Hard glitch. Main character disappears. Camera returns to the original door composition.

- SFX: three knocks
- On-screen text: `WOULD YOU OPEN IT?`
- Make final composition loop naturally back to Shot 1.

## Editing rules
- First 3 seconds must contain movement, visual anomaly, text, and voice.
- No intro, logo animation, or early subscribe CTA.
- Avoid static shots longer than roughly 2–3 seconds without motion/event/caption change.
- Captions must be large and readable on mobile.
- Keep screen text concise.

## Audio
Use only original, licensed, royalty-free, or platform-permitted audio.

Required cues:
- narration
- door sound
- low impact
- glitch
- slam
- subtle tension ambience
- three knocks

No unlicensed popular copyrighted music.

Voice style: energetic general-gaming narration, not preschool/hyper-childish.

## Roblox production architecture
Create a reusable project/template, not a fully hardcoded single scene.

Suggested structure:

```text
Workspace/
  Scene_Normal/
  Scene_Impossible/
  Characters/
  Cameras/
  Lighting/
ReplicatedStorage/
  Assets/
  Animations/
ServerScriptService/
  SceneController
```

Where reasonable, parameterize:
- camera paths
- character spawn
- door animation
- lighting changes
- teleport
- scene reset

## Declarative content requirement
Create a config such as:

`content/video_001.json`

It should describe at least:
- video_id
- title
- characters
- scenes
- dialogue
- camera sequence
- duration
- captions
- sound cues

Goal: later Shorts should mainly require changing declarative content/spec data rather than rewriting the whole system.

## Reusable components
Create reusable modules only where they add clear value. Candidate responsibilities:
- CameraController
- CharacterController
- SceneController
- DoorController
- CaptionTimeline
- AudioCueTimeline
- LightingController
- ResetController

Prefer fewer clean modules over unnecessary abstraction.

## Deterministic playback
Prepare the scene so it can replay consistently.

Provide at minimum:
- START VIDEO
- RESET VIDEO

If practical without major overengineering, make playback invokable programmatically for future automation.

## Deliverables
1. Roblox Studio project/source.
2. Source scripts.
3. `content/video_001.json` or equivalent declarative config.
4. Final vertical video if the execution environment supports reliable capture/render.
5. Caption/subtitle asset.
6. Voice/audio asset or reproducible generation instructions.
7. Thumbnail/frame candidate.
8. README/run instructions.
9. `AUTOMATION_NOTES.md`.

If the environment cannot directly produce a final playable `.mp4` or `.rbxl/.rbxlx`, do not fake completion. Produce the maximum reproducible project/source/config and explicitly list the exact remaining execution step.

## Automation notes requirement
Document:
- what is already automated;
- what still needs a human;
- the exact manual steps remaining;
- bottlenecks discovered;
- what should be automated next;
- how much work a second video would require compared with the first.

## Quality gate
Before marking complete, verify:
- story works without extra context;
- hook occurs within ~1.5 seconds;
- plot is understandable on a phone without headphones;
- captions are readable;
- no unauthorized copyrighted material;
- no watermarks or accidental Studio UI in final media;
- twist is clear;
- loop is intentional;
- output is not a static/template slideshow;
- the video has an original story.

## Scope exclusions
Do not build yet:
- channel/account creation
- auto-posting
- 100-video generator
- monetization system
- multi-language system
- complex analytics dashboard

## Stop condition
After implementing SPEC-001, stop and report only:

- FINAL OUTPUT / what was actually produced
- SOURCE PROJECT / relevant paths
- AUTOMATION NOTES
- MANUAL STEPS REMAINING
- RECOMMENDATION FOR THE NEXT ENGINEERING STEP

Do not autonomously proceed to SPEC-002.

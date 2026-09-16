# Roblox Media Factory

Automation-first media experiment for building original Roblox gaming content with minimal owner involvement.

## Current objective

Prove that one high-quality Roblox Short can be produced through a repeatable, increasingly automated pipeline before attempting scale.

## Operating model

- Strategy/research: ChatGPT + owner review
- Execution/engineering: Codex
- Source of truth: this repository
- Owner involvement target: strategic approvals only

## Repository layout

- `specs/shorts/` — approved production specifications
- `src/` — reusable automation/source code
- `content/` — declarative content configs
- `output/` — generated deliverables metadata/links (do not commit huge raw media unless needed)
- `analytics/` — experiment results and performance data
- `PROJECT_STATE.md` — current status, decisions, blockers, next action

## Current phase

**SPEC-001 prototype** — `A Bacon Hair Found a Door That Shouldn't Exist`.

Do not build mass posting, monetization, multi-language scaling, or a 100-video generator yet. First prove the repeatable production pipeline and identify manual bottlenecks.

## Execution rule for Codex

When instructed to work on the project, read `PROJECT_STATE.md` first, then execute only the currently approved spec. Do not advance to the next spec without explicit approval.

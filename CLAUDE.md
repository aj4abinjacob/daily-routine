# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Single-page static HTML application — a **4-Day Upper/Lower Cutting Programme** for a ~91 kg male in a caloric deficit. Everything lives in one file: `index.html` (~1990 lines) with inline CSS and vanilla JavaScript. No build tools, no dependencies, no package manager.

**Hosted on GitHub Pages:** https://aj4abinjacob.github.io/daily-routine/

## Programme Goals (shown in header meta tags)

- **Lose 0.5–0.7 kg/week** (500–700 kcal/day deficit)
- **Retain muscle & strength** during the cut
- **180–200g protein / 2,100–2,300 kcal daily**
- **8,000–10,000 steps daily** (NEAT target for desk worker)
- **8 hours sleep** (critical for muscle retention in deficit — Nedeltcheva 2010)
- **Fix desk posture** (upper/lower crossed syndrome from WFH)

## How to Run

Open `index.html` directly in a browser. No server required.

## Deployment

Push to `master` branch — GitHub Pages auto-deploys from `/` on `master`.

## Architecture

The file is structured in three inline sections:

1. **`<style>` block (lines 9–220)** — CSS custom properties in `:root`. Dark theme with semantic color coding: amber=primary, green=working sets/positive, blue=warmup/info, purple=cooldown/rest/cognitive, orange=tips/nutrition, red=warnings. Responsive breakpoint at 640px.

2. **`<body>` HTML (lines 222–1708)** — Nine tab-based sections controlled by `data-tab` attributes on nav buttons:
   - `upper-a` (Mon — Strength), `lower-a` (Tue — Quad emphasis), `upper-b` (Thu — Hypertrophy), `lower-b` (Fri — Hypertrophy) — workout days with exercises, set/rep tables, warm-up/cooldown protocols, and volume audits
   - `cardio` — LISS protocol (Wed/Sat), step count targets, sedentary office tips, nutrition targets (protein, calories, macro split)
   - `daily` — full daily schedule, sleep protocol, egg guide, supplements (creatine/whey), dinner timing, posture protocol, brain training / cognitive fitness
   - `route` — visual timeline maps for training day and rest day (toggleable), showing meals with protein/calorie stats at each time slot
   - `volume` — weekly volume summary table per muscle group across all 4 days
   - `rpe` — RPE/RIR reference chart

3. **`<script>` block (lines ~1930–1987)** — Vanilla JS: tab navigation, exercise card expand/collapse (`toggleExercise`), protocol block expand/collapse (`toggleProtocol`), step counter bar animation (`animateStepBar`), route map day-type toggle (`switchRoute`).

## Key Patterns

- Exercises use `.exercise.open` class toggle for expand/collapse (CSS `max-height` transition)
- Protocol blocks (warm-up/cooldown) use separate `.open` class on both header and body
- Set tables use badge classes: `.badge-warmup`, `.badge-feeler`, `.badge-working`
- RPE values are color-coded: `.rpe-low` (green), `.rpe-mid` (amber), `.rpe-high` (orange), `.rpe-max` (red)
- Route section uses `switchRoute('train'|'rest')` to toggle between two timeline maps
- Volume audit divs appear at the end of each workout section with per-muscle-group set counts
- Research notes (`.research-note`, blue) on each exercise cite specific studies (SBS, RP, Helms, Maeo, etc.) justifying rep ranges
- Form tips (`.form-tip`, green) on each exercise provide 2-3 science-backed technique cues with study citations (Schoenfeld, Contreras, Escamilla, Signorile, Lehman, Caterisano, Bourne, Reinold, Marcolin, etc.)
- Progression rules appear in `.tip-row` elements (orange, e.g., "when you hit 8-8-8, go to 45 kg")
- Fonts: Outfit (body text), JetBrains Mono (numeric/data values)

## Exercise Structure

Each exercise card contains (in order):
1. **Research note** (`.research-note`, blue) — rep range justification with study citations
2. **Set table** (`.set-table`) — weight, reps, rest, RPE, type badge, notes per set
3. **Form tip** (`.form-tip`, green) — 2-3 technique cues from peer-reviewed EMG/biomechanics papers
4. **Progression tip** (`.tip-row`, orange, optional) — when/how to increase weight

26 exercises total: Upper A (8), Lower A (7), Upper B (8), Lower B (6).

## Content Context

- All weights are in **kg**, all nutrition in **grams/kcal**
- Research citations throughout — rep range justifications (Helms, Schoenfeld, Garthe, Maeo, etc.) and form cues (Contreras, Escamilla, Signorile, Lehman, Caterisano, Bourne, Reinold, Marcolin, etc.)
- Nutrition examples use Indian food sources (dal, paneer, curd, roti)
- Schedule assumes WFH with 9:30–6:30 work hours, gym at 7:30 AM
- The programme is designed for an advanced natural trainee — RPE targets are conservative (compounds at RPE 7–8, only safe isolations go to RPE 9–10)

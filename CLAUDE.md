# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Single-page static HTML application — a **4-Day Upper/Lower Cutting Programme** for gym training. Everything lives in one file: `index.html` (~1770 lines) with inline CSS and vanilla JavaScript. No build tools, no dependencies, no package manager.

## How to Run

Open `index.html` directly in a browser. No server required.

## Architecture

The file is structured in three sections:

1. **`<style>` block (lines 9–220)** — All CSS using CSS custom properties defined in `:root`. Dark theme with color-coded elements (amber=primary, green=working sets, blue=warmup, purple=cooldown/rest, orange=tips). Responsive breakpoint at 640px.

2. **`<body>` HTML (lines 222–1708)** — Tab-based content sections controlled by `data-tab` attributes on nav buttons. Sections: `upper-a`, `lower-a`, `upper-b`, `lower-b` (workout days), `cardio`, `daily` (daily routine/steps), `route` (walking route maps with training/rest day toggle), `volume` (weekly volume summary table), `rpe` (RPE/RIR reference guide). Each workout day contains collapsible exercise cards with set/rep tables and collapsible warm-up/cooldown protocol blocks.

3. **`<script>` block (lines 1710–1767)** — Vanilla JS for: tab navigation (show/hide sections), exercise card expand/collapse (`toggleExercise`), protocol block expand/collapse (`toggleProtocol`), step counter bar animation (`animateStepBar`), route map day-type toggle (`switchRoute`).

## Key Patterns

- Exercises use `.exercise.open` class toggle for expand/collapse (CSS `max-height` transition)
- Protocol blocks (warm-up/cooldown) use separate `.open` class on both header and body
- Set tables use badge classes for set types: `.badge-warmup`, `.badge-feeler`, `.badge-working`
- RPE values are color-coded: `.rpe-low` (green), `.rpe-mid` (amber), `.rpe-high` (orange), `.rpe-max` (red)
- Route section uses `switchRoute('train'|'rest')` to toggle between training and rest day maps
- Fonts: Outfit (body text), JetBrains Mono (numeric/data values)

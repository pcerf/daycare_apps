# Notbetreuungs-Planer

## Purpose

A single-file, offline-first browser application for kindergarten management to plan emergency childcare (Notbetreuung) fairly and transparently — for situations like strikes, staff shortages, or pandemics.

## Architecture

- **One file**: `notbetreuung.html` — all HTML, CSS, and JavaScript in a single file.
- **No dependencies**: No CDN, no external scripts, no external fonts. Works offline by opening the file directly in a browser.
- **Privacy**: All data stays in the browser (`sessionStorage`). No server requests, no cookies, no tracking.
- **Persistence**: State is exported/imported as a human-readable `.md` file. No auto-save — users must export manually.

## Core Data Model (`state` object)

| Field | Type | Description |
|---|---|---|
| `kinder` | array | Child records: `{id, name, gruppe, vertragH, email, kumulH}` |
| `bedarfeStamm` | object | Permanent baseline needs per child (annual school-year survey) |
| `bedarfe` | object | Current active needs for the ongoing situation |
| `tage` | array | Per-day opening times (Mon–Fri, default 07:15–16:00) |
| `maxKinderProTag` | number | Max children per day cap |
| `plan` | object | Current weekly assignment: `kindId → {day → {von, bis}}` |
| `standardplaene` | array | Reusable plan templates with embedded needs + assignments |
| `history` | array | Accepted plans with cumulative hour snapshots |

## Tabs & Workflow

1. **Kinder** — Register children once (name, group, weekly contract hours, parent email, cumulative emergency hours).
2. **Bedarfsabfrage** — Generate a structured email template to query parents for their care needs. Sends via `mailto:` with all parents in BCC.
3. **Antworten importieren** — Import `.msg` files from Outlook (or paste text). Parses the structured reply block `[NOTBETREUUNG-ANTWORT v1]` and matches responses to children by name. Manual override available.
4. **Planer** — Weekly drag-and-drop planner. Auto-generates a fairness-weighted proposal. Children with lower cumulative care percentage (relative to contract hours) are prioritized. Color coding: green = need + allocation, yellow = need but no slot, salmon = slot but no reported need.
5. **Standardpläne** — Save reusable plan templates for recurring scenarios (e.g., "Full care", "Core hours only", "Half staffing"). Applying a template does not affect cumulative hours.
6. **Historie** — Log of accepted plans. Each accepted plan adds hours to each child's `kumulH`, which feeds the fairness algorithm in future proposals.
7. **Datei** — Export full state as `.md` / import from `.md`. Also a full reset button.

## Key Algorithms

- **Fairness score**: `kumulH / vertragH` — lower ratio = higher priority in auto-plan proposals.
- **Coverage**: `intersected hours(need, allocation) / need hours` — shown per child as a progress bar (green ≥85%, yellow 50–84%, red <50%).
- **Stamm-Bedarfe vs. aktuelle Bedarfe**: Baseline needs (annual) are stored separately from current-situation needs. Either can be loaded into the planner independently.

## Language

The UI is entirely in **German**. Variable names and code comments are in English.

## Development Notes

- Edit only `notbetreuung.html`. There are no build steps, no package manager, no bundler.
- Test by opening the file directly in a browser (`file://`).
- The `.md` export format is both human-readable and machine-parseable — the import parser relies on specific Markdown section headers.

# Case Study — Hotel Maintenance Tracking System

**One Google Apps Script that generates an entire maintenance workbook for a small hotel team: dashboard, work orders, room inspections, parts inventory, and preventive-maintenance schedules — with no paid software.**

> Personal portfolio project. Built for a ~90-room select-service hotel in Central Texas. Property details, room data, and supplier information in the working system are private and are not reproduced here — this case study describes the design and the build only.

## The problem

A small maintenance team was tracking preventive maintenance, guest-room defects, inspections, and parts across paper notes and memory. Things slipped: rooms went past their inspection cycle, carpet-shampoo rotations were guesswork, and nobody could answer "what's open, what's overdue, and what parts are we low on?" in one place.

## The build

A single Apps Script file (`google-apps-script/Code.gs`) generates the whole workbook on demand — 11 sheets from one menu click:

- **Dashboard** — live counts and charts: open work orders, inspections due, low-stock parts
- **Active Work Orders** — ticket tracking with automatic IDs, priority, and status formatting
- **Room Inspections** — a 30-day preventive-maintenance cycle per room, with a 7-day "coming due" warning window
- **Room Inspection PM** — a printable, brand-standard inspection checklist organised by system (general readiness, HVAC, electrical, plumbing, walls, life safety)
- **Parts Inventory** — stock levels with reorder points and critical-spares flags
- **Daily / Weekly / Monthly Tasks** — recurring cadence checklists
- **Carpet Shampoo** — a 90-day rotation per room with a 14-day warning window
- **FLUSHMATE SNs** — a per-room log for serialized in-room assets, so a specific unit's history can be found in seconds
- **Lists** — hidden validation data powering the dropdowns

## Design decisions that mattered

- **Non-destructive refresh.** Re-running the generator rebuilds structure, formulas, and formatting *without wiping data the team already entered* — the feature that made the team willing to trust and keep using it.
- **Thresholds, not noise.** Inspections warn at 7 days out, carpet at 14 — early enough to schedule, late enough to ignore safely until then.
- **Dropdowns and colour-coded status everywhere**, so a new hire can run the workbook with no training doc.
- **Zero cost.** Sheets + Apps Script only — no subscription tool a small property would never approve.

## Development story

- Shipped in iterations through mid-2026. A later update added the serialized-asset log and the refresh-preserves-data behaviour after real use showed both were needed.
- A real bug found in production — a dashboard formatting call using a non-existent method (`setFontWeight` instead of the correct API) — was diagnosed from the error, fixed, and shipped the same cycle. Small, but it's the loop that matters: use it daily, find the friction, fix it.

## Skills demonstrated

Google Apps Script (V8) · Google Sheets architecture · formula and validation design · iterative development from daily operational feedback · technical documentation

## What's next

- A sanitised demo copy with fictional rooms and parts, so anyone can install and try it
- A generic version other small properties could adopt (see the productised tracker idea in my GitHub profile)

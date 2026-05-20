# LifeHorizon — Project Brief

> Personal Development Web App สำหรับคนไทย ที่ต้องการเห็นภาพรวมชีวิต, ตั้งเป้าหมาย, และจัดการเวลา

---

## Overview

| | |
|---|---|
| Project Name | LifeHorizon |
| Version | 1.0 (V1) |
| Owner | แดง (@dsc2903) |
| Type | Single-file React Web App |
| Entry Point | `index.html` |

---

## Tech Stack

| Layer | Technology |
|---|---|
| UI Framework | React 18 (via CDN + Babel Standalone) |
| Styling | Tailwind CSS (Play CDN) |
| Font | Sarabun (Google Fonts) — Thai-first |
| Storage | Browser LocalStorage (no backend, no login) |
| Notifications | Web Notifications API |
| Build Tool | None — zero build step, open in browser directly |

---

## Features

### 1. Life Progress Calculator — Memento Mori
- Input: ชื่อ + วันเกิด (onboarding screen)
- Formula: `spentPct = (ageYears / 77) * 100` (77 = Thailand avg life expectancy)
- Display: Circular SVG progress ring + collapsible 52×77 weeks grid
- Stats: % spent, % remaining, days remaining, weeks remaining

### 2. North Star — True Happiness & Core Desires
- Two pinned text areas: ความสุขที่แท้จริง + เป้าหมายสูงสุด
- Auto-save to localStorage on every keystroke (debounced)

### 3. Live Countdown Timers
- Add countdowns: name + datetime deadline
- Live ticking DD:HH:MM:SS display (updates every second)
- Color urgency: red < 1 day, amber ≤ 3 days, teal = safe
- Web Notification when deadline < 24 hours (opt-in)

### 4. SMART Goal Wizard
- 5-step interactive wizard: Specific → Measurable → Achievable → Relevant → Time-bound
- Progress bar per step
- Compiles into expandable goal card with days-remaining badge

### 5. Daily Notes & Reflection
- Free-form textarea with guided prompts
- Auto-save with debounce (800ms) + last-saved timestamp
- Character count display

---

## Design System

| Token | Value |
|---|---|
| Primary Accent | `#22d3ee` (cyan-400 / teal) |
| Dark Background | `#030712` (gray-950) |
| Dark Card | `#111827` (gray-900) |
| Light Background | `#f9fafb` (gray-50) |
| Font | Sarabun, 300–700 weight |
| Border Radius | 16px (cards), 12px (inputs), 999px (pills) |
| Dark Mode | CSS class strategy (`<html class="dark">`) |

---

## LocalStorage Keys

| Key | Type | Content |
|---|---|---|
| `lh_user` | Object | `{ name: string, dob: string }` |
| `lh_theme` | String | `'dark'` or `'light'` |
| `lh_northstar` | Object | `{ happiness: string, goals: string }` |
| `lh_countdowns` | Array | `[{ id, name, deadline }]` |
| `lh_goals` | Array | `[{ id, specific, measurable, achievable, relevant, timebound, createdAt }]` |
| `lh_notes` | String | Daily notes content |

---

## Navigation (Bottom Bar — Mobile-first)

| Tab ID | Label | Icon |
|---|---|---|
| `life` | ชีวิต | ⧗ |
| `north` | ดาวเหนือ | ✦ |
| `count` | นับถอยหลัง | ◷ |
| `goals` | เป้าหมาย | ◎ |
| `notes` | บันทึก | ◻ |

---

## UI Language Policy

- **UI text, labels, placeholders, buttons** → ภาษาไทย ทั้งหมด
- **Code, variables, comments, function names** → English only

---

## Privacy Model

- Zero server — all data stays in browser LocalStorage
- No login, no account, no network requests (except CDN assets on first load)
- Reset option clears all localStorage keys

---

*Updated: 2026-05-20*

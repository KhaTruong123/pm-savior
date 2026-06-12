---
name: slides
description: "Create an HTML slide deck for stakeholder presentations, sprint reviews, pitch decks, or product demos. Use when asked to 'create a deck', 'make a slide deck', 'stakeholder presentation', 'N-slide deck', 'sprint review slides', 'pitch this to leadership', or 'build a slide deck'."
license: MIT
attribution: "Adapted from ClaudeKit Engineer's slides skill — https://github.com/claudekit/claudekit-engineer (MIT)"
argument-hint: "[topic] [slide-count] [audience]"
metadata:
  author: kelvin
  version: "1.0.0"
---

# Slides — Stakeholder Presentations

Generate a self-contained HTML slide deck with Chart.js data visualization, keyboard navigation, and clean design. Opens directly in any browser — no install, no server.

## Your mission

<task>
$ARGUMENTS
</task>

## When to Use

- Stakeholder update or QBR
- Sprint review or demo day
- Product pitch or fundraise deck
- Competitive analysis or strategic brief
- Workshop or onboarding session

---

## Output

Produces a **single `.html` file**:
- Saves to `./docs/slides/` by default (or user-specified path)
- Opens in browser — use arrow keys or click to navigate
- Charts rendered with Chart.js (CDN, no install)
- Print-to-PDF via browser's print dialog (Ctrl+P / Cmd+P)

---

## Deck Structures

Choose the structure that matches the goal:

| Structure | Slides | Best For |
|-----------|--------|----------|
| **Stakeholder Update** | 8–12 | QBR, monthly review |
| **Product Pitch** | 10–12 | Investor, leadership buy-in |
| **Sprint Review** | 6–8 | Team demo, delivery summary |
| **Problem-Solution** | 5–7 | Quick persuasion, proposal |
| **Competitive Brief** | 6–10 | Internal strategy |
| **Workshop** | 15–25 | Teaching, onboarding |

### Stakeholder Update (default)
1. Title + date + presenter
2. Agenda / What we'll cover
3. Key metrics (Chart.js — bar or line)
4. Progress against plan (phase status table)
5. Highlights / wins
6. Risks + mitigations
7. Decisions needed
8. Next steps + owners

### Product Pitch
1. Hook (problem statement)
2. Market opportunity
3. Solution
4. How it works (diagram or screenshot)
5. Traction / proof
6. Business model
7. Roadmap
8. Team
9. Financials / ask
10. The ask + next step

### Sprint Review
1. Sprint goal
2. Delivered (demo list)
3. Key metric moved
4. What didn't make it (and why)
5. Retrospective highlight
6. Next sprint preview

---

## Design Defaults

Inline CSS only — no external design token files required.

```
Color palette (dark theme):
  Background:   #0D0D0D
  Slide bg:     #1A1A1A
  Primary:      #6C63FF  (purple-blue)
  Accent:       #FF6B6B  (coral)
  Text:         #FFFFFF
  Muted text:   #888888
  Border:       #2A2A2A

Typography:
  Font:         Inter, system-ui, sans-serif
  Heading:      2.8rem bold
  Subheading:   1.4rem medium
  Body:         1rem / 1.6 line-height

Layout:
  Aspect ratio: 16:9 (letterboxed)
  Padding:      60px
  Max width:    1280px
```

To override, describe your preference in the argument: `"use a light theme"`, `"use brand colors #FF6B00 and #1A1A2E"`.

---

## Chart.js Integration

For data slides, describe the data and chart type:

**Supported chart types:**
- `bar` — comparisons (revenue by region, feature adoption)
- `line` — trends over time (MAU growth, churn rate)
- `doughnut` / `pie` — proportions (market share, budget split)
- `radar` — multi-dimensional comparison (competitor matrix)

**Example prompt:**
```
/slides "Q2 merchant growth deck — include a line chart showing monthly active merchants Jan-Jun 2026: 12, 18, 24, 31, 40, 52"
```

---

## HTML Template Structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Presentation Title</title>
  <script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.1/dist/chart.umd.min.js"></script>
  <style>
    /* Inline CSS — no external deps */
    :root { --primary: #6C63FF; --bg: #0D0D0D; }
    body { background: var(--bg); color: #fff; font-family: Inter, sans-serif; }
    .slide { position: absolute; width: 100%; height: 100%; display: flex;
             flex-direction: column; justify-content: center; align-items: center;
             padding: 60px; opacity: 0; transition: opacity 0.4s; }
    .slide.active { opacity: 1; }
    /* ... */
  </style>
</head>
<body>
  <div class="slide-deck">
    <div class="slide active"> <!-- Slide 1 --> </div>
    <div class="slide"> <!-- Slide 2 --> </div>
  </div>
  <script>
    // Keyboard navigation + Chart.js initialization
  </script>
</body>
</html>
```

---

## Example Invocations

```
/slides "Q2 stakeholder update — 3 KPIs, Indonesia expansion status, risks"
/slides "Fundraise pitch deck — 10 slides — Series A audience"
/slides "Sprint 14 review — demo summary and next sprint goals"
/slides "Competitor analysis: Gaian vs Alchemy Pay vs Fizen — 8 slides"
/slides "Workshop: how to write a good PRD — 20 slides"
```

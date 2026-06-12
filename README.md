# PM Savior — Product Management Skills, inspired by ClaudeKit

A personal collection of Claude Code skills for Product Managers and Business Analysts. Port and adaptation of select skills from [ClaudeKit Engineer](https://github.com/claudekit/claudekit-engineer) (MIT), rewritten in PM language — no coding knowledge required.

**Attribution:** Skills adapted from ClaudeKit Engineer by claudekit — https://github.com/claudekit/claudekit-engineer (MIT License)

---

## Who is this for?

- Product Managers and Business Analysts using [Claude Code](https://claude.ai/code)
- Non-technical practitioners who want structured AI-assisted workflows for requirements, planning, research, and stakeholder deliverables
- No coding. No compilers. No deployments.

**Prerequisites:** Claude Code installed and authenticated. That's it.

---

## Setup (3 steps)

1. Clone this repo:
   ```bash
   git clone https://github.com/KhaTruong123/pm-savior ~/pm-savior
   ```
2. Follow **[install.md](install.md)** to copy skills to Claude Code.
3. Open Claude Code in any working directory. Skills are ready.

---

## Where to Start

You don't need all 10 skills on day one. Install the core 3 first:

| Tier | Skills | When to add |
|---|---|---|
| **Core (start here)** | `pm-plan`, `pm-cook`, `pm-brainstorm` | Day 1 — the plan→cook loop covers most PM work |
| **Task skills** | `pm-test-case-generator`, `pm-requirement-risk-review`, `pm-diagrams-mermaid`, `pm-slides` | Add when you need QA scenarios, spec stress-testing, diagrams, or stakeholder decks |
| **Power user** | `pm-research`, `pm-sequential-thinking`, `pm-progress-tracker` | Add for deep research, complex reasoning, or multi-session plan tracking |

Or just install all 10 at once — they're markdown files, the footprint is negligible.

---

## Skill Catalog

| Skill | What it does | Example prompt |
|---|---|---|
| `pm-brainstorm` | Explore options with trade-off analysis and honest challenge | "Explore options for our onboarding process redesign" |
| `pm-plan` | Break an initiative into phases with clear deliverables | "Plan this initiative: launch a new B2B pricing tier" |
| `pm-cook` | Execute a plan phase, producing PM artifacts (docs, tables, analysis) | "Execute phase-01 of the market research plan" |
| `pm-research` | Structured market, vendor, or domain research with a cited report | "Research competitor pricing models in fintech APAC" |
| `pm-sequential-thinking` | Step-by-step reasoning for complex decisions | "Think through step by step: should we delay the launch?" |
| `pm-test-case-generator` | Generate acceptance criteria and requirement gap analysis | "Write test cases for this requirement: users can export reports" |
| `pm-requirement-risk-review` | 5-persona stress-test of a spec before committing | "Review this requirement before we commit to the sprint" |
| `pm-diagrams-mermaid` | Create Mermaid diagrams: user journeys, flows, Gantt, state | "Draw the user journey for onboarding a new enterprise client" |
| `pm-slides` | Build stakeholder presentation slides | "Create a deck for the Q3 initiative review" |
| `pm-progress-tracker` | Track plan progress across sessions, sync checkboxes | "Check plan status for the pricing launch plan" |

---

## Output Conventions

| Artifact | Where it lands |
|---|---|
| Multi-phase plans | `./plans/{YYYY-MM-DD}-{slug}/` |
| Research, brainstorm, scenario reports | `./outputs/{YYYY-MM-DD}-{slug}.md` |
| Diagrams | `./outputs/diagrams/{YYYY-MM-DD}-{slug}.md` |
| Presentation slides | `./outputs/slides/{YYYY-MM-DD}-{slug}.html` |

---

## License

MIT — see [LICENSE](LICENSE).

Portions adapted from ClaudeKit Engineer (MIT) — https://github.com/claudekit/claudekit-engineer.
pm-test-case-generator and pm-requirement-risk-review patterns also adapted from autoresearch by Udit Goenka (MIT).

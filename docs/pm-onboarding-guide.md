# PM Savior — Onboarding Guide

Get from zero to your first AI-assisted PM deliverable in under 10 minutes.

---

## Prerequisites

- [Claude Code](https://claude.ai/code) installed and authenticated
- This repo cloned: `git clone https://github.com/KhaTruong123/pm-savior ~/pm-savior`

---

## Step 1 — Install Skills

Copy all skills into Claude Code's skills directory:

```bash
for skill in ~/pm-savior/skills/*/; do
  skill_name=$(basename "$skill")
  if [ -d ~/.claude/skills/"$skill_name" ]; then
    echo "SKIP $skill_name — already exists"
  else
    cp -r "$skill" ~/.claude/skills/
    echo "INSTALLED $skill_name"
  fi
done
```

**Verify:** Open Claude Code in any directory, type `/` — you should see `pm-plan`, `pm-cook`, `pm-brainstorm`, etc.

---

## Step 2 — Try It (3-Minute Quickstart)

Open Claude Code in any directory (doesn't need to be a code repo). Type:

```
Plan a 3-phase rollout for a new onboarding checklist feature
```

Claude will trigger `pm-plan` and produce a phased plan directory with a `plan.md` and phase files.

Then:

```
Execute the plan — work through phase 1
```

Claude will trigger `pm-cook` and produce the phase 1 deliverable (document, table, or analysis).

---

## Prompt Cookbook

### Planning

| What you want | What to type |
|---|---|
| Create a phased plan | `Plan this initiative: [describe it]` |
| Plan from a document/brief | `Create a plan for: [paste the brief]` |
| Break an epic into phases | `Break this into phases: [epic description]` |
| Validate an existing plan | `Validate this plan: [paste plan or path to plan.md]` |
| Quick plan (no deep research) | `/pm-plan fast [initiative description]` |
| Hard problems (thorough) | `/pm-plan hard [complex initiative]` |

### Executing a Plan

| What you want | What to type |
|---|---|
| Execute one phase | `Execute phase 2 of the plan at [path]` |
| Work through the whole plan | `Cook this plan — produce all deliverables: [plan path]` |
| Continue where you left off | `Continue the plan — work on the next pending phase` |
| Skip review gates | `Execute the plan automatically: [plan path]` |

### Requirements & Risk

| What you want | What to type |
|---|---|
| Write test cases from a requirement | `Write test cases for this requirement: [paste requirement]` |
| Find risks in a spec | `Review this spec, what could go wrong? [paste spec]` |
| Stress-test a feature idea | `Stress test this feature: [describe it]` |
| Find gaps in a PRD section | `Find the risks in this PRD section: [paste section]` |

### Brainstorming

| What you want | What to type |
|---|---|
| Compare two directions | `Compare option A vs option B for [topic]` |
| Explore approaches | `What are the options for [problem/initiative]?` |
| Get honest trade-off analysis | `Brainstorm how to approach [challenge]` |
| Debate a decision | `Should we [option 1] or [option 2]? Stress-test both.` |

### Research

| What you want | What to type |
|---|---|
| Market or competitor research | `Research the market for [topic]` |
| Vendor/tool evaluation | `Research vendors for [need] — compare their features` |
| Deep analysis | `Deep research on [topic] — I need a comprehensive report` |

### Diagrams

| What you want | What to type |
|---|---|
| User journey | `Draw the user journey for [process]` |
| Process or approval flow | `Draw the process flow for [process]` |
| Gantt / roadmap timeline | `Draw a roadmap timeline for [initiative]` |
| Sequence diagram | `Draw the sequence diagram for [interaction]` |

### Presentations

| What you want | What to type |
|---|---|
| Stakeholder slide deck | `Make a 5-slide stakeholder deck from this summary: [paste]` |
| Sprint review | `Create sprint review slides for [sprint summary]` |
| Pitch to leadership | `Pitch this to leadership: [idea or proposal]` |

### Utilities

| What you want | What to type |
|---|---|
| Track plan progress | `Show progress on the plan at [plan path]` |
| Update a phase status | `Mark phase 2 complete in the plan at [plan path]` |
| Step-by-step reasoning | `Think through this step by step: [complex problem]` |

---

## The Plan→Cook Workflow (Core PM Loop)

This is the highest-value workflow in the pack. Use it for any initiative that spans more than one session.

```
1. Plan:   "Plan this initiative: [describe it]"
           → Claude creates plans/{date}-{slug}/ with plan.md + phase files

2. Validate: "Validate this plan: plans/{date}-{slug}/plan.md"
             → Claude stress-tests scope, gaps, dependencies

3. Execute: "Execute the plan at plans/{date}-{slug}/plan.md"
            → Claude works through phases, produces deliverables, updates statuses

4. Resume:  "Continue the plan — work on the next pending phase"
            → Claude picks up from where it left off
```

**Each phase produces a concrete artifact** — a document, table, test case set, risk matrix, or stakeholder brief — stored in the plan directory alongside the phase file.

---

## What This Pack Does NOT Do

- **No code**: does not write, review, or deploy software
- **No repo operations**: no git commits, no CI/CD, no pull requests
- **No terminal commands**: no shell scripts, no package installs
- **No external integrations**: no Jira tickets, no Confluence pages (copy-paste manually)
- **No live data**: cannot query your databases or dashboards

If you need any of the above, use the [ClaudeKit engineer stack](https://github.com/claudekit/claudekit-engineer) instead.

---

## Troubleshooting

**Skill doesn't trigger:** Type `/pm-plan` (or the full slash command) directly instead of natural language.

**Wrong skill triggers:** Add more context — e.g. "Write TEST CASES for this requirement" is more explicit than "check this requirement."

**Plan not found:** Always use the full path — `plans/260612-1326-my-initiative/plan.md` — not just the directory name.

**Deliverable missing after cook:** Check the phase file — it describes what artifact should have been produced. If Claude wrote it inline instead of to a file, ask: "Save the deliverable to a file in the plan directory."

---

## Updating

```bash
cd ~/pm-savior && git pull
# Re-copy changed skills (overwrite existing):
rm -rf ~/.claude/skills/pm-plan && cp -r ~/pm-savior/skills/pm-plan ~/.claude/skills/
```

---

*PM Savior — adapted from [ClaudeKit Engineer](https://github.com/claudekit/claudekit-engineer) (MIT license)*

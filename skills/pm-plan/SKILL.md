---
name: pm-plan
description: "Break a product initiative or document effort into a phased plan with clear deliverables and TODO tracking. Use when asked to 'plan this initiative', 'create a plan for the PRD', 'plan how to launch X', 'break this into phases', or 'validate this plan'."
license: MIT
attribution: "Adapted from ClaudeKit Engineer's plan skill — https://github.com/claudekit/claudekit-engineer (MIT)"
argument-hint: "[quick|deep|validate] [initiative or plan path]"
metadata:
  author: kelvin
  version: "1.0.0"
---

# Plan — Phased Plans for Product Initiatives

Create structured, phase-by-phase plans for PM/BA work: PRDs, launch checklists, research series, test suites, stakeholder programs — any initiative that benefits from being broken into trackable phases with statuses.

## Your mission

<task>
$ARGUMENTS
</task>

## Pre-Creation Check (reuse before create)

Before creating a new plan, look in `./plans/` for an existing plan directory covering the same initiative:
- If one exists → ask the user: "Found existing plan: {path}. Continue with it or create a new one?"
- Otherwise → create a new plan at `./plans/{YYYY-MM-DD}-{slug}/` (today's date + short descriptive kebab-case slug).

## Workflow

1. Analyze the initiative. If goals, audience, constraints, or deadlines are unclear, use the `AskUserQuestion` tool to clarify (max 4 questions).
2. Pick depth: `quick` for small, well-understood work; `deep` when the initiative needs research or has open questions. If the user named a subcommand, respect it.
3. Load the matching reference file below and follow it.

## Subcommands

| Subcommand | Description | Reference |
|------------|-------------|-----------|
| `quick` | No research. Analyze the inputs and produce a phased plan directly | `references/quick.md` |
| `deep` | Research first, then produce a phased plan | `references/deep.md` |
| `validate` | Interview the user with critical questions to validate an existing plan | `references/validate.md` |

## Routing

1. Parse the subcommand from the request (first word: `quick`, `deep`, or `validate`)
2. Load the corresponding `references/{subcommand}.md`
3. Execute with the remaining arguments
4. If no subcommand was given: choose quick vs deep yourself based on complexity, and tell the user which you chose and why.

## Important Notes

- **IMPORTANT: Do not** start producing the deliverables — planning only. Execution belongs to the `pm-cook` skill ("execute this plan").
- Keep plans concise; sacrifice grammar for the sake of concision.
- List unresolved questions at the end of every plan.

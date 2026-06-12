---
name: diagrams-mermaid
description: "Create text-based diagrams using Mermaid.js v11 syntax. Use when asked to 'draw the user journey', 'process flow', 'approval flow', 'roadmap timeline', 'sequence diagram', or 'flowchart'. Outputs inline Mermaid code blocks ready for GitHub, Notion, or any markdown viewer."
license: MIT
attribution: "Adapted from ClaudeKit Engineer's mermaidjs-v11 skill — https://github.com/claudekit/claudekit-engineer (MIT)"
argument-hint: "[diagram type or description]"
metadata:
  author: kelvin
  version: "1.0.0"
---

# Diagrams — Mermaid.js v11

Create text-based diagrams using Mermaid.js v11 declarative syntax. Outputs inline markdown code blocks — no tool installation needed for GitHub, Notion, or Confluence rendering.

## Your mission

<task>
$ARGUMENTS
</task>

## When to Use

- User journey maps — visualize end-to-end customer experience
- Business process flowcharts — document how a process works
- Approval flows — show who approves what, in sequence
- Roadmap timelines — Gantt-style phase/milestone view
- Meeting facilitation — live diagram generation during a discussion

---

## Quick Start

Wrap any diagram in a fenced code block:

````markdown
```mermaid
flowchart TD
    A[Start] --> B{Decision}
    B -->|Yes| C[Action]
    B -->|No| D[End]
```
````

---

## PM Diagram Patterns

### User Journey Map
Show the customer experience across touchpoints with satisfaction scores.

```mermaid
journey
  title Customer Onboarding Journey
  section Discover
    Sees ad: 4: Customer
    Visits landing page: 3: Customer
  section Sign Up
    Fills registration form: 2: Customer
    Verifies email: 3: Customer, System
  section First Use
    Completes profile: 4: Customer
    Makes first transaction: 5: Customer, System
```

### Business Process Flowchart
Document how a process flows, including decision points and actors.

```mermaid
flowchart TD
    A([Merchant submits KYC docs]) --> B{Docs complete?}
    B -->|No| C[Request missing docs]
    C --> A
    B -->|Yes| D[Compliance review]
    D --> E{Approved?}
    E -->|Yes| F[Activate account]
    E -->|No| G[Send rejection notice]
    F --> H([Merchant live])
    G --> H2([Case closed])
```

### Approval Flow (Sequence Diagram)
Show who sends what to whom, and what decisions are made.

```mermaid
sequenceDiagram
    participant PM as Product Manager
    participant Legal as Legal Team
    participant CEO as CEO
    PM->>Legal: Submit contract draft
    Legal-->>PM: Request changes (3 items)
    PM->>Legal: Revised draft
    Legal-->>CEO: Approved, forwarding for sign-off
    CEO-->>PM: Signed ✓
```

### Roadmap (Gantt)
Show phases, milestones, and timelines.

```mermaid
gantt
  title Product Roadmap Q3-Q4 2026
  dateFormat YYYY-MM-DD
  section Foundation
    KYC redesign          :done,    kyc,  2026-07-01, 2026-07-21
    API v2 launch         :active,  api,  2026-07-15, 2026-08-15
  section Growth
    Indonesia expansion   :         indo, 2026-08-01, 2026-09-30
    Widget SDK            :         sdk,  2026-09-01, 2026-10-15
  section Fundraise
    Series A prep         :crit,    fund, 2026-09-15, 2026-10-31
```

---

## Diagram Type Reference

### Flowchart
```
flowchart {direction}   — TD (top-down), LR (left-right), BT, RL
  nodeId[label]         — rectangle
  nodeId(label)         — rounded
  nodeId{label}         — diamond (decision)
  nodeId([label])       — stadium (start/end)
  A --> B               — solid arrow
  A -.-> B              — dotted arrow
  A -->|label| B        — labelled arrow
```

### Sequence Diagram
```
sequenceDiagram
  participant A as Actor Name
  A->>B: Message
  B-->>A: Response
  Note over A,B: Annotation
  loop Retry logic
    A->>B: Retry
  end
  alt Happy path
    B-->>A: Success
  else Error
    B-->>A: Error
  end
```

### Gantt (Roadmap)
```
gantt
  title Title
  dateFormat YYYY-MM-DD
  section Phase Name
    Task name :status, id, start-date, duration
    — status: done | active | crit | milestone
    — duration: 7d or end-date
```

### User Journey
```
journey
  title Title
  section Section Name
    Task description: score(1-5): Actor1, Actor2
```

### Quadrant (Prioritization)
```
quadrantChart
  title Priority Matrix
  x-axis Low Effort --> High Effort
  y-axis Low Impact --> High Impact
  Feature A: [0.2, 0.8]
  Feature B: [0.7, 0.5]
```

### Mindmap (Brainstorm Output)
```
mindmap
  root((Central Topic))
    Branch 1
      Sub-item
    Branch 2
      Sub-item
```

### Timeline (Milestones)
```
timeline
  title Key Milestones
  2026 Q1 : Soft launch : First tenant live
  2026 Q2 : Indonesia expansion
  2026 Q3 : Series A
```

---

## Configuration (Optional)

Add a frontmatter block to customize theme:

````markdown
```mermaid
---
theme: neutral
---
flowchart LR
  A --> B
```
````

**Themes:** `default`, `neutral`, `dark`, `forest`, `base`
**Look:** `classic` (default), `handDrawn` (sketchy style)

---

## Rendering

| Environment | How to render |
|-------------|---------------|
| GitHub / GitLab | Paste the fenced block — auto-rendered |
| Notion | `/code` block → select Mermaid |
| Confluence | Mermaid plugin |
| VS Code | Markdown Preview Mermaid Support extension |
| Browser | `https://mermaid.live` — paste and export PNG/SVG |

---

## Example Invocations

```
/diagrams-mermaid "User journey for merchant onboarding"
/diagrams-mermaid "Approval flow for payment exception review"
/diagrams-mermaid "Roadmap Q3-Q4 with Indonesia expansion and fundraise milestone"
/diagrams-mermaid "Business process: refund request handling"
```

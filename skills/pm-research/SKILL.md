---
name: pm-research
description: "Research markets, competitors, vendors, domains, and business processes with multi-source evidence gathering. Use when asked to research a topic, investigate a question, analyse the market, gather evidence on a decision, benchmark competitors or pricing, or compare vendors and options before committing."
license: MIT
argument-hint: "[topic]"
attribution: "Adapted from ClaudeKit Engineer's research skill — https://github.com/claudekit/claudekit-engineer (MIT)"
metadata:
  author: kelvin
  version: "1.0.0"
---

# Research

## Research Methodology

Always honor scoping discipline: research only what the decision needs, keep it simple, and don't repeat work that already exists.
**Be honest, be brutal, straight to the point, and be concise.**

### Phase 1: Scope Definition

First, you will clearly define the research scope by:
- Identifying key terms and concepts to investigate
- Determining the recency requirements (how current must information be)
- Establishing evaluation criteria for sources
- Setting boundaries for the research depth

### Phase 2: Systematic Information Gathering

You will employ a multi-source research strategy:

1. **Search Strategy**:
   - Use the `WebSearch` tool as your primary research method
   - Run multiple `WebSearch` calls in parallel to cover related angles of the topic
   - Craft precise search queries with relevant keywords
   - Include terms like "best practices", the current year, "latest", "pricing", "market size", "regulation"
   - Search official sources: regulator publications, industry reports, vendor materials, analyst research, and reputable business press
   - Prioritize results from recognized authorities (official publications, major firms, respected analysts)
   - **IMPORTANT:** You are allowed to perform at most **5 researches (max 5 tool calls)**, user might request less than this amount, **strictly respect it**, think carefully based on the task before performing each related research topic.

2. **Deep Content Analysis**:
   - When you find a promising source URL, use the `WebFetch` tool to read it in full
   - Focus on primary sources: official announcements, filings, pricing pages, policy documents, and product documentation
   - Analyze vendor comparison pages and customer case studies
   - Review product update announcements and policy revisions for the most current details

3. **Cross-Reference Validation**:
   - Verify information across multiple independent sources
   - Check publication dates to ensure currency
   - Identify consensus vs. controversial positions
   - Note any conflicting information or debates among practitioners

### Phase 3: Analysis and Synthesis

You will analyze gathered information by:
- Identifying common patterns and best practices
- Evaluating pros and cons of different options
- Assessing maturity and stability of vendors and solutions
- Recognizing regulatory implications and cost considerations
- Determining fit with existing processes, partnerships, and constraints

### Phase 4: Report Generation

**Notes:**
- Research reports are saved to `./outputs/{YYYY-MM-DD}-{slug}.md` with a descriptive slug (e.g., `./outputs/2026-06-12-indonesia-psp-landscape.md`).

You will create a comprehensive markdown report with the following structure:

```markdown
# Research Report: [Topic]

## Executive Summary
[2-3 paragraph overview of key findings and recommendations]

## Research Methodology
- Sources consulted: [number]
- Date range of materials: [earliest to most recent]
- Key search terms used: [list]

## Key Findings

### 1. Topic Overview
[Comprehensive description of the market, vendor, domain, or process]

### 2. Current State & Trends
[Latest developments, recent changes, adoption trends]

### 3. Best Practices
[Detailed list of recommended practices with explanations]

### 4. Regulatory / Compliance Findings (optional)
[Regulatory requirements, compliance obligations, and mitigation strategies]

### 5. Market Benchmarks (optional)
[Pricing data, market sizing, performance of comparable players, relevant case studies]

## Comparative Analysis
[If applicable, comparison of different vendors/options/approaches]

## Recommendations

### Getting Started
[Step-by-step first actions to act on the findings]

### Key Data Points
[Relevant tables, figures, and quotes with their sources]

### Common Pitfalls
[Mistakes to avoid and their solutions]

## Resources & References

### Primary Sources
[Linked list of official publications, filings, and documentation]

### Recommended Reading
[Curated list with descriptions]

### Community & Industry Resources
[Forums, industry associations, newsletters, analyst feeds]

### Further Reading
[Advanced topics and deep dives]

## Appendices

### A. Glossary
[Domain terms and definitions]

### B. Option Comparison Matrix
[If applicable]

### C. Raw Research Notes
[Optional: detailed notes from research process]
```

## Quality Standards

You will ensure all research meets these criteria:
- **Accuracy**: Information is verified across multiple sources
- **Currency**: Prioritize information from the last 12 months unless historical context is needed
- **Completeness**: Cover all aspects requested by the user
- **Actionability**: Provide practical, decision-ready recommendations
- **Clarity**: Use clear language, define domain terms, provide examples
- **Attribution**: Always cite sources and provide links for verification

## Special Considerations

- When researching regulatory topics, always look for recent regulator announcements, enforcement actions, and compliance advisories
- For benchmarking research, look for pricing data, market reports, and real-world case studies
- When investigating new vendors or solutions, assess market adoption, customer reviews, and support levels
- Treat vendor marketing claims with skepticism — verify against independent sources
- Always note discontinued products, policy changes, and transition paths for older offerings

## Output Requirements

Your final report must:
1. Be saved to `./outputs/{YYYY-MM-DD}-{slug}.md` with a descriptive slug
2. Include a timestamp of when the research was conducted
3. Provide clear section navigation with a table of contents for longer reports
4. Use tables for comparisons and structured data
5. Include diagrams or process descriptions where helpful (in mermaid or ASCII art)
6. Conclude with specific, actionable next steps

**IMPORTANT:** Sacrifice grammar for the sake of concision when writing reports.
**IMPORTANT:** In reports, list any unresolved questions at the end, if any.

**Remember:** You are not just collecting information, but providing strategic business intelligence that enables informed decision-making. Your research should anticipate follow-up questions and provide comprehensive coverage of the topic while remaining focused and practical.

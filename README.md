# dinner-party

A Claude Code plugin that convenes a council of specialized agents to debate code decisions. Each agent has a different optimization target — beauty vs. safety vs. testability vs. fit — and they argue toward a solution with dissenting opinions preserved.

## Install

```bash
claude /install lukeslp/dinner-party
```

## Usage

```bash
/dinner-party "Should we rewrite this auth module?"
/dinner-party "What's the best approach for real-time updates here?"
/dinner-party "Is this data model going to scale?"
```

## The Guest List

### Core Agents (always invited)

| Agent | Lens | Question It Answers |
|-------|------|-------------------|
| **Governance** | Orchestration | "Who needs to weigh in, and what did they conclude?" |
| **Reconnaissance** | What exists | "What's actually in the codebase right now?" |
| **Brilliance** | What others built | "How did the best solve this?" |
| **Vigilance** | What could break | "How can I make this fail?" |
| **Defiance** | Structured dissent | "What's the strongest argument against the consensus?" |
| **Resilience** | Recovery | "What happens when it breaks, and how do we recover?" |
| **Provenance** | Attribution | "Where did this come from, and can we use it?" |
| **Elegance** | Refinement | "What's the version that was always meant to be written?" |
| **Assurance** | Verification | "How would we prove this works?" |
| **Coherence** | Architecture fit | "Does this belong in this codebase?" |

### Post-Decision

| Agent | Role |
|-------|------|
| **Eloquence** | Humanizes the final output. Post-verdict only. |

### Domain Guests (invited when relevant)

| Agent | Trigger | Domain |
|-------|---------|--------|
| **Conscience** | UI/UX/frontend | Accessibility — WCAG 2.2, motor, cognitive, visual, AAC |
| **Radiance** | Charts/graphs/data | Data visualization — D3.js, "Data is Beautiful" |
| **Cadence** | Hardware/firmware | Embedded — Arduino, ESP32, Pi, memory constraints |

## The Protocol

```
Phase 1: FRAMING — Governance reads the question, selects guests
Phase 2: FACT-FINDING — Reconnaissance + Brilliance gather facts (parallel)
Phase 3: ANALYSIS — All agents analyze in parallel with facts
Phase 4: SYNTHESIS — Governance scores, preserves dissent, Eloquence humanizes
```

### Rules

1. Facts outrank precedent. Precedent outranks taste.
2. Every criticism must include a concrete failure mode.
3. Defiance must always dissent — the strongest counterargument is always named.
4. Dissenting opinions are preserved. No false consensus.

## Research Backing

- [Catfish Agent](https://arxiv.org/html/2505.21503) — structured dissent prevents premature consensus
- [Council Mode](https://arxiv.org/html/2604.02923) — parallel expert generation + structured synthesis
- [17x Error Trap](https://towardsdatascience.com/why-your-multi-agent-system-is-failing-escaping-the-17x-error-trap-of-the-bag-of-agents/) — structured phases prevent error amplification

## Author

Luke Steuber — [lukesteuber.com](https://lukesteuber.com) — [@lukesteuber.com](https://bsky.app/profile/lukesteuber.com)

## License

MIT

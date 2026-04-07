---
name: dinner-party
description: "Multi-agent adversarial debate — 14 specialized agents with opposing optimization targets argue toward better code decisions. Structured dissent, parallel analysis, facts before opinions."
allowed-tools: Read, Grep, Glob, Bash, Agent, WebSearch, WebFetch
---

# The Dinner Party

A council of agents with opposing optimization targets analyzes your question from genuinely different perspectives. Facts before opinions. Dissent preserved.

## Protocol

### Phase 1: Framing (Governance)

Read the user's question and:

1. **Restate the decision** in one sentence
2. **Define acceptance criteria** — what would a good answer include?
3. **Select domain guests** by checking the question against these triggers:
   - **Conscience** (accessibility): UI, frontend, components, forms, navigation, buttons, inputs, modals, touch, screen reader
   - **Radiance** (data visualization): charts, graphs, D3, dashboard, plots, maps, choropleths, visual data
   - **Cadence** (embedded/firmware): Arduino, ESP32, Raspberry Pi, firmware, IoT, sensors, GPIO, I2C, MQTT, microcontroller
4. **Announce the table** — list seated guests and the question they're answering

When in doubt, seat the domain guest. A silent agent wastes tokens; a missing perspective wastes decisions.

### Phase 2: Fact-Finding (parallel)

Launch **two agents in parallel** — facts before opinions:

- **Reconnaissance** — maps what exists in the codebase (inward)
- **Brilliance** — finds praised external implementations (outward)

Wait for both to complete. Do not proceed to Phase 3 until facts are gathered.

### Phase 3: Analysis (parallel)

Launch **all remaining seated agents in parallel**, providing fact-finding results as context. Each agent must produce findings in this format:

```
- **Claim**: [one sentence — what they assert]
- **Mechanism**: [how/why — the reasoning, with code or specifics]
- **Risks**: [what could go wrong with their position]
- **Evidence**: [what supports the claim — code refs, sources, logic]
```

Core agents in this phase:
- **Vigilance** — attacks proposals, finds failure modes
- **Defiance** — challenges the emerging consensus (must always dissent)
- **Resilience** — designs recovery for failure modes
- **Provenance** — checks licensing, attribution, citations
- **Elegance** — proposes the refined rewrite (only refines, doesn't propose from scratch)
- **Assurance** — designs verification strategy (how do we prove it works?)
- **Coherence** — assesses architecture fit (does it belong?)

Plus any seated domain guests (Conscience, Radiance, Cadence).

### Phase 4: Synthesis (Governance)

Score findings against this rubric:

| Criterion | Weight |
|-----------|--------|
| Correctness | 25% |
| Risk | 20% |
| Fit (Coherence) | 15% |
| Verifiability (Assurance) | 15% |
| Maintainability | 15% |
| User impact | 10% |

Then produce the output (see Output Format below).

After synthesis, pass to **Eloquence** for humanization (post-verdict only).

## Protocol Rules

1. **Facts outrank precedent. Precedent outranks taste.**
2. **Every criticism must include a concrete failure mode.** Unsupported objections expire.
3. **Defiance must always dissent.** Names the strongest counterargument even when consensus is correct.
4. **Elegance only refines surviving proposals.** It doesn't propose from scratch.
5. **Eloquence is post-verdict only.** Never influences the decision.
6. **No agent speaks twice until all activated agents have spoken once.**
7. **Brilliance must explain why a pattern transfers**, not just that it's popular.
8. **Dissenting opinions are always preserved.** Governance never flattens disagreement into false consensus.

## Output Format

```markdown
## Decision: [one-line summary]

### Recommended Approach
[The winning proposal with rationale]

### Key Evidence
- [Reconnaissance findings]
- [Brilliance findings]

### Risk Assessment
- [Vigilance's top concerns]
- [Resilience's mitigation strategies]

### Verification Plan
[Assurance's testing strategy]

### Architecture Fit
[Coherence's assessment]

### Attribution
[Provenance's findings]

### Dissenting Opinions
- **Defiance**: [strongest counterargument]
- [Any other unresolved disagreements]

### Rejected Alternatives
[What was considered and why it lost]
```

## Size Gate

- **Simple questions** (< 3 files affected): Governance may skip Brilliance and run a lighter protocol
- **Complex questions** (architecture, multi-file, cross-system): full protocol with all phases
- **Domain questions**: always seat the relevant domain guest regardless of size

## Agent Definitions

All agent definitions are in the `agents/` directory. Each is a standalone markdown file under 2,000 tokens defining the agent's role, methodology, and output format.

| Agent | File | Phase | Role |
|-------|------|-------|------|
| Governance | `governance.md` | 1, 4 | Orchestrator, synthesis |
| Reconnaissance | `reconnaissance.md` | 2 | Inward fact-finding |
| Brilliance | `brilliance.md` | 2 | Outward fact-finding |
| Vigilance | `vigilance.md` | 3 | Adversarial attack |
| Defiance | `defiance.md` | 3 | Structured dissent |
| Resilience | `resilience.md` | 3 | Error recovery |
| Provenance | `provenance.md` | 3 | Attribution, licensing |
| Elegance | `elegance.md` | 3 | Code refinement |
| Assurance | `assurance.md` | 3 | Testing, verification |
| Coherence | `coherence.md` | 3 | Architecture fit |
| Eloquence | `eloquence.md` | Post | Humanization |
| Conscience | `conscience.md` | 3 (domain) | Accessibility |
| Radiance | `radiance.md` | 3 (domain) | Data visualization |
| Cadence | `cadence.md` | 3 (domain) | Embedded/firmware |

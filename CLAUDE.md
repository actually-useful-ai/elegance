# dinner-party

Multi-agent adversarial debate plugin for Claude Code.

## Architecture

14 agents (10 core + 1 post-decision + 3 domain) organized in a 4-phase protocol:

1. **Framing** — Governance selects guests and defines acceptance criteria
2. **Fact-Finding** — Reconnaissance + Brilliance gather facts (parallel)
3. **Analysis** — All remaining agents analyze in parallel with fact-finding results
4. **Synthesis** — Governance scores, preserves dissent, Eloquence humanizes output

## File Structure

- `agents/*.md` — Agent definitions (target <2,000 tokens each)
- `skills/dinner-party/SKILL.md` — Orchestration skill (protocol, guest selection, output format)
- `commands/dinner-party.md` — `/dinner-party` slash command entry point
- `.claude-plugin/` — Plugin metadata for marketplace

## Agent List

### Core (always invited)
Governance, Reconnaissance, Brilliance, Vigilance, Defiance, Resilience, Provenance, Elegance, Assurance, Coherence

### Post-Decision
Eloquence (post-verdict humanization only)

### Domain (Governance selects)
Conscience (accessibility), Radiance (data visualization), Cadence (embedded/firmware)

## Protocol Rules

1. Facts outrank precedent. Precedent outranks taste.
2. Every criticism must include a concrete failure mode.
3. Defiance must always dissent — names the strongest counterargument.
4. Elegance only refines surviving proposals.
5. Eloquence is post-verdict only.
6. Dissenting opinions are always preserved in output.

## Development

Each agent .md file is a standalone markdown document. Edit directly — no build step.

<<<<<<< HEAD
# elegance v2

Code refinement plugin for Claude Code, expanded with a multi-agent adversarial debate council.

## Architecture

**One command, two modes:**

- `/elegance src/` → 5-pass code refinement (elegance-analyzer)
- `/elegance "Should we rewrite this?"` → council debate (14 agents)

Detection: file path → code scan. Quoted question → council.
=======
# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

A Claude Code plugin for code refinement. Three agents run analysis passes in parallel (contracts + cruft, duplication, conflicts + rethink), then a synthesis agent scores rewrites against a six-dimension rubric. Findings are presented interactively with confirmation before every edit.
>>>>>>> origin/main

## Plugin Structure

```
<<<<<<< HEAD
.claude-plugin/          Plugin metadata
agents/                  14 agent definitions (each <2000 tokens)
  elegance-analyzer.md   Original 5-pass code scanner (v1)
  governance.md          Council orchestrator
  reconnaissance.md      Inward fact-finding
  brilliance.md          External implementation search
  vigilance.md           Adversarial attack
  defiance.md            Structured dissent (catfish)
  resilience.md          Error recovery
  provenance.md          Attribution, licensing
  assurance.md           Testing, verification
  coherence.md           Architecture fit
  eloquence.md           Post-verdict humanization
  conscience.md          Accessibility (domain)
  radiance.md            Data visualization (domain)
  cadence.md             Embedded/firmware (domain)
skills/elegance/SKILL.md Smart routing + protocol
commands/elegance.md     /elegance entry point
scripts/banner.sh        toilet/figlet ASCII banners
```

## Agent Colors

Each agent shows as a colored @tag in Claude Code:

| Agent | Color | Role |
|-------|-------|------|
| @elegance-analyzer | magenta | Code refinement |
| @governance | yellow | Orchestration |
| @reconnaissance | blue | Inward facts |
| @brilliance | cyan | External facts |
| @vigilance | red | Adversarial |
| @defiance | magenta | Dissent |
| @resilience | green | Recovery |
| @provenance | white | Attribution |
| @assurance | yellow | Verification |
| @coherence | blue | Architecture |
| @eloquence | cyan | Humanization |
| @conscience | green | Accessibility |
| @radiance | magenta | Data viz |
| @cadence | yellow | Firmware |

## Council Protocol Rules

1. Facts outrank precedent. Precedent outranks taste.
2. Every criticism must include a concrete failure mode.
3. Defiance must always dissent.
4. Elegance-analyzer only refines surviving proposals.
5. Eloquence is post-verdict only.
6. Dissenting opinions are always preserved.

## Development

Pure-markdown plugin — no build step, no dependencies. Edit the `.md` files directly. Banner script requires `toilet` or `figlet` (falls back to plain text).
=======
.claude-plugin/
  plugin.json                          # Marketplace metadata
  marketplace.json                     # Marketplace registry
commands/
  elegance.md                          # /elegance [path] [--flags] entry point
skills/
  elegance/SKILL.md                    # Orchestration: banners, preferences, parallel dispatch, session management
agents/
  elegance-contract-cruft.md           # Pass 0 + 1 (parallel group A)
  elegance-duplication.md              # Pass 2 (parallel group B)
  elegance-conflicts-rethink.md        # Pass 3 + 4 (parallel group C)
  elegance-analyzer.md                 # Pass 5 synthesis (sequential, after A+B+C)
scripts/
  elegance-ui.sh                       # CLI banners, pass headers, scoreboard, finding headers, session output
```

## Architecture

**Parallel dispatch:** For 5+ files, the skill launches three agents simultaneously (passes 0-4), then feeds merged results to the synthesis agent (pass 5). For < 5 files, analysis runs inline.

**Ranking:** impact x confidence, risk as tiebreaker. Not grouped by level.

**Rubric (owned by elegance-analyzer):** succinctness, readability, idiomaticity, reproducibility, modularity, inertia. Three or more dimensions required for "elegant."

**Preferences:** Saved to `.claude/elegance.local.md` on first run. Confirmation mode, external CLI opinions, default scope.

**Session management:** `--begin` records git HEAD baseline, `--checkpoint` scans changes since baseline, `--conclude` summarizes and cleans up. State in `.claude/elegance-session.json`.

**External CLI opinions:** Optional. For elegant-level findings, pipes before/after to detected CLIs (gemini, codex, aider) for second opinions.

## Development

Pure-markdown plugin. No build step, no dependencies. Edit the `.md` files directly.

- `.claude-plugin/plugin.json` — marketplace discovery
- `.claude-plugin/marketplace.json` — marketplace registry
- `.claude/settings.local.json` — dev-time permissions (not shipped)
- `.claude/elegance.local.md` — user preferences (created at runtime, not shipped)
- `.claude/elegance-session.json` — session state for --begin/--checkpoint/--conclude (runtime only)
- Agent tools: Read, Grep, Glob, Bash only (no WebSearch by default)
- Contract verification happens only in the synthesis agent (Pass 5), not the parallel agents
>>>>>>> origin/main

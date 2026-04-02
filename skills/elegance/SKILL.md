---
name: elegance
description: "Code refinement that goes past cleanup to find the version that feels inevitable. Use when reviewing code quality, refactoring, cleaning up, or when someone asks to simplify, deduplicate, or improve code. Confirms before every change."
---

# Elegance

Find the version of the code that was always meant to be written.

<HARD-GATE>
NEVER make changes without presenting them first and getting explicit user confirmation. Show the before, show the after, explain WHY the new version is better. Every proposed change must be confirmed.
</HARD-GATE>

## Philosophy

When you read good code, you don't think "that's clever." You think "of course." Your job is to find that version.

Three levels:
- **Cruft** -- shouldn't be here (dead code, unused imports, orphan files)
- **Simplify** -- works, but working too hard (duplication, over-engineering, CSS fights)
- **Elegant** -- the rewrite that makes you pause (a 50-line function that's really a 3-line reduce, three components that want to be one)

## Process

Run six passes over the target code. Use the elegance-analyzer agent for the heavy scanning, then present findings interactively.

### Pass 1: Cruft Scan
- Dead code (unreachable branches, commented-out blocks)
- Unused imports, variables, functions, files
- Orphan files (not imported or referenced anywhere)
- Stale dependencies
- TODO/FIXME/HACK comments that are actually done or obsolete

### Pass 2: Duplication Audit
- Copy-pasted logic (functions or blocks that do the same thing with minor variations)
- Near-identical components (React/Vue/Svelte components that differ by < 20%)
- Repeated CSS patterns (same color values, spacing, shadows declared multiple times)
- Repeated JS patterns (same fetch/error-handling/transform logic)
- Config or constants duplicated across files

### Pass 3: Conflict Detection
- CSS specificity wars (styles overriding each other unnecessarily)
- Competing JS event handlers on the same elements
- Duplicate or conflicting CSS class names
- Z-index battles
- Multiple sources of truth for the same state
- Competing animation/transition definitions
- Tailwind + custom CSS doing the same thing

### Pass 4: First-Principles Rethink
For any complex logic (> 15 lines doing one conceptual thing):
- What is this ACTUALLY trying to do? State it in one sentence.
- Is there a built-in language feature, standard library function, or well-known pattern that does exactly this?
- Can the control flow be simplified? (nested ifs → early returns, loops → map/filter/reduce, switch → object lookup)
- Are there unnecessary intermediate variables or transformations?
- Would inverting the logic make it clearer?

### Pass 5: Shared Component Opportunities
- 2+ components/functions with the same structure but different data
- UI elements that appear in multiple places with slight visual variations
- API call patterns that could be a shared hook or utility
- Error handling that could be centralized
- Layout patterns that repeat across pages/views

### Pass 6: Elegance Search
The interesting part. For each significant finding from passes 1-5:
- Search for well-regarded solutions to the same problem (look for "elegant", "idiomatic", "clean" alongside the pattern)
- Check if the language or framework already has a way to do this
- Look for design patterns that fit naturally
- Consider whether a library solves this exactly
- The test: does it make the reader think "of course"?

## Presenting Findings

Group findings by file or area. For each finding:

```
### [area/file] — [finding title]

**Level:** cruft | simplify | elegant
**Confidence:** high | medium | low

**What I found:**
[Brief description of the current state]

**Why it matters:**
[What's wrong or what opportunity exists]

**Proposed change:**
[Show the before/after or describe the transformation]

**Apply this change? (y/n)**
```

Present findings in priority order:
1. **Elegant** findings first (the exciting ones)
2. **Simplify** findings next
3. **Cruft** last (least interesting but still valuable)

Within each level, sort by impact (most improvement first).

## Confirmation Protocol

- Present one finding at a time (or a small related group)
- Wait for explicit confirmation before making ANY edit
- If the user says "apply all" or "yes to all", you may batch-apply remaining changes of the same level
- If the user disagrees with a finding, skip it — don't argue
- After applying changes, show a brief summary of what was changed

## What makes a finding "elegant"

Not just shorter. Elegant code is where:
- The intent is obvious on first read
- There's no ceremony
- It uses the tools the way they were meant to be used
- Reading it teaches you something
- It makes the code around it simpler too
- It feels like the only way to write it

## Scope

- If invoked on a specific file or directory, analyze that scope
- If invoked without a target, analyze recently changed files (git diff)
- For large codebases, focus on the most-touched files (git log --shortstat)
- Always respect .gitignore and skip node_modules, dist, build, vendor, etc.

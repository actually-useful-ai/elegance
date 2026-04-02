# elegance

Code refinement plugin for Claude Code. Looks past surface-level cleanup to find the version of your code that feels inevitable.

## Install

```
/install lukeslp/elegance
```

## Usage

```
/elegance              # look at recent git changes
/elegance src/         # focus on a directory
/elegance app.tsx      # focus on a single file
```

## How it works

Six passes over your code, each looking for something different:

1. **Cruft** -- dead code, unused imports, orphan files, stale TODOs
2. **Duplication** -- copy-pasted logic, repeated CSS/JS patterns, near-identical components
3. **Conflicts** -- CSS specificity fights, competing event handlers, z-index chaos, duplicate state
4. **First principles** -- complex logic boiled down: "what is this actually trying to do?"
5. **Shared components** -- patterns that show up in multiple places and want to be one thing
6. **Elegance** -- the interesting part: searching for the solution that makes you think "of course"

Every finding gets a level:

- **elegant** -- a rewrite that makes you pause and appreciate it
- **simplify** -- it works, but it's working too hard
- **cruft** -- shouldn't be here

Nothing changes without your say-so. Each finding shows what's there now, what it could look like, and why. You confirm before anything is touched.

## What's in the box

| What | Type | Does |
|------|------|------|
| `/elegance` | Command | Run it with an optional path |
| `elegance` | Skill | The interactive review loop |
| `elegance-analyzer` | Agent | Heavy scanning runs in the background |

## Examples

A 47-line validation function that's really `zod.object({...}).parse()`. Three card components that differ by an icon and a color. CSS that sets `font-weight: 600` in nine different places instead of using a variable. A nested ternary that reads better as an object lookup.

These are the kinds of things elegance finds -- and for each one, it looks for the version that makes the code feel like it was always meant to be written that way.

## License

MIT

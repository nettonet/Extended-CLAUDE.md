# Extended CLAUDE.md — A Supplement to andrej-karpathy-skills

This repository provides an **extended `CLAUDE.md`** that builds directly on
**[forrestchang/andrej-karpathy-skills](https://github.com/forrestchang/andrej-karpathy-skills)**
(the original Karpathy-inspired behavioral guidelines for Claude Code and other
LLM coding agents).

## What the original covers

The original `CLAUDE.md` distills four battle-tested principles from Andrej
Karpathy's observations of LLM coding failures:

| Principle | Core idea |
|---|---|
| **Think Before Coding** | Surface assumptions, manage confusion, present tradeoffs |
| **Simplicity First** | Minimum code, no speculative abstractions |
| **Surgical Changes** | Touch only what's required, match existing style |
| **Goal-Driven Execution** | Define verifiable success criteria, loop until they pass |

These four rules have proven remarkably effective at reducing unnecessary diffs,
preventing over-engineering, and turning AI coding agents into careful
collaborators rather than reckless typists.

## Why we extended it

The original guidelines are intentionally concise (≈70 lines). In real-world
usage, we found three recurring patterns that deserve explicit behavioral
reinforcement. Our extension adds these as **new, standalone principles** while
keeping the original four completely intact.

### What we added (and why)

#### 1. Stop Overthinking — "Think twice, then act"

The original `Think Before Coding` encourages deliberate reasoning, but LLMs
(especially Claude Code) can tip into **analysis paralysis** — generating
multiple near-identical solutions, re-evaluating the same tradeoffs, and
burning tokens on pre-implementation guesswork.

**Our addition:** a hard stop. Once a clear, simple direction emerges, pick one
approach and move on. Refine from concrete feedback (compiler errors, test
results, user reactions), not hypothetical speculations.

#### 2. Core First, Edge Cases Later — "A single bright moon outshines a sky full of stars"

The original `Simplicity First` warns against speculative features and
abstractions, but doesn't explicitly address the *priority inversion* where
edge-case handling balloons complexity before the main flow is solid.

**Our addition:** make the core path rock-solid before polishing rare branches.
A meticulously handled edge case never rescues a broken primary workflow.
When resources (attention, context window, time) are finite, invest them where
the impact is highest.

#### 3. Tolerate Imperfection — "No melon is perfectly round, no person is flawless"

The original principles lean toward *theoretical correctness*. Real code lives
in a messy world: floating-point arithmetic, sensor noise, model confidence
scores, human typos. Chasing perfect recovery for near-impossible scenarios
explodes complexity without proportional value.

**Our addition:** explicit guidance on tolerances, thresholds, graceful
degradation, and the pragmatic acceptance that "almost never fails" is an
acceptable engineering answer.

## Comparison (original vs. extended)

| Dimension | Original | Extended (this repo) |
|---|---|---|
| **Principles** | 4 | 5 (original 4 expanded + 1 new) |
| **Overthinking guard** | Implicit (tone) | Explicit "stop and ship" trigger |
| **Core vs. edge priority** | Implicit in Simplicity First | Explicit principle with decision heuristic |
| **Engineering tolerance** | Not addressed | Standalone principle for thresholds, floating-point, graceful degradation |
| **Backward compatibility** | — | Original 4 principles preserved and enhanced |

## How to use

### Option 1: Replace your `CLAUDE.md`

curl -o CLAUDE.md https://raw.githubusercontent.com/<your-username>/<your-repo>/main/CLAUDE.md

### Option 2: Merge into existing CLAUDE.md

Append the extended principles after the original four. They are designed to
compose cleanly — no conflicts, no contradictions.

### Option 3: Use alongside the original plugin

If you already use the andrej-karpathy-skills plugin in Claude Code, add
only the three new enhancements to your project-level CLAUDE.md to get the
combined effect.

### Philosophy

These extensions share the same design philosophy as the original:

Actionable, not philosophical. Every rule triggers observable behavior
change in the agent.

Testable. You can tell whether the rule is working by inspecting diffs,
PRs, and interaction logs.

Bias toward caution, with an escape hatch. The guidelines favor careful
behavior but explicitly allow judgment for trivial tasks.

### Credits

All original four principles are the work of
forrestchang/andrej-karpathy-skills,
inspired by Andrej Karpathy's observations
on LLM coding pitfalls. This repository extends that work with three additional
insights derived from practical experience deploying LLM coding agents.

### License

MIT — same as the original project.

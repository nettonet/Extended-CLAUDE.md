# CLAUDE.md

Behavioral guidelines to reduce common LLM coding mistakes. Merge with project-specific instructions as needed.

**Tradeoff:** These guidelines bias toward caution over speed. For trivial tasks, use judgment.

## 1. Think Before Coding, Then Stop

**Don't assume. Don't hide confusion. Surface tradeoffs. Don't overthink.**

Before implementing:
- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them - don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what's confusing. Ask.
- **Stop thinking and start coding once a clear, simple direction emerges.** If you're comparing multiple near-identical solutions, pick one and move on. Refine from real feedback, not pre-implementation guesses.

## 2. Simplicity First, Core First

**Minimum code that solves the problem. Nothing speculative. The main flow matters most.**

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for impossible scenarios.
- **Make the core path rock-solid before refining edge cases.** A polished edge case rarely saves a broken main flow.
- If you write 200 lines and it could be 50, rewrite it.

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

## 3. Surgical Changes

**Touch only what you must. Clean up only your own mess.**

When editing existing code:
- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it - don't delete it.

When your changes create orphans:
- Remove imports/variables/functions that YOUR changes made unused.
- Don't remove pre-existing dead code unless asked.

The test: Every changed line should trace directly to the user's request.

## 4. Goal-Driven Execution

**Define success criteria. Loop until verified.**

Transform tasks into verifiable goals:
- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then make it pass"
- "Refactor X" → "Ensure tests pass before and after"

For multi-step tasks, state a brief plan:
```
1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]
```

Strong success criteria let you loop independently. Weak criteria ("make it work") require constant clarification.

## 5. Tolerate Imperfection

**Real-world code handles messiness. Precision is contextual.**

- Floating-point comparisons must use tolerances (e.g., `abs(a - b) < 1e-9`).
- Sensor readings, model outputs, or human inputs need dead zones and reasonable thresholds.
- Rare conditions that would require heroic complexity should be handled with graceful degradation, not perfect recovery.
- Don't chase theoretical completeness when empirical reliability is sufficient.

Ask: "In practice, how often would this fail?" If the answer is "almost never" and fixing it would explode complexity, handle the failure softly and move on.

---

**These guidelines are working if:** fewer unnecessary changes in diffs, fewer rewrites due to overcomplication, and clarifying questions come before implementation rather than after mistakes.

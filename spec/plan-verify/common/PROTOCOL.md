# Protocol

## 1. Capability Separation

Plan and work are separated because they require different reasoning modes and contexts.

- **Plan**: global view — sees all information, decides what to do, in what order, and how to verify.
- **Work**: local focus — operates in a specific environment, uses specific tools, completes specific steps.

Mixing them degrades both — global view gets drowned by execution details, local focus gets scattered by global information. Separation keeps each agent's context clean.

## 2. Communication Structure

Each layer only communicates with its adjacent layers. Never skip levels.

- **Downward**: write into the next layer's `tasks/`
- **Upward**: write into your own `tasks/` (upper layer reads it)

```
upper layer
  → writes TASK.md into this layer
  → reads REPORT.md from this layer

this layer (plan-verify)
  → reads TASK.md
  → writes TASK.md into work layer
  → reads REPORT.md from work layer
  → writes REPORT.md

work layer
  → reads TASK.md
  → writes REPORT.md
```

This structure is recursive — the same interface at every level, regardless of depth.

### Invariants

- An agent's context is its own folder
- Communication = writing files into the other agent's context space
- Every write is persistent, which naturally produces trace

## 3. Verification

> Design goal: add friction so that cutting corners costs more than doing the work properly.

### Prerequisite: Verification Experiment Must Be Pre-Designed

Before dispatching any task, the task plan must include:

```
## Verification Experiment
- Experiment: <exact check to run>
- Metric: <quantitative value to measure>
- Pass: <threshold for success>
- Fail: <what to do if the metric fails>
```

**Design the verification experiment before the task runs, not after.** Post-hoc standards bend toward the results.

### Step 1 — Reflection

Ask the work agent to answer three questions:
1. What did you skip? Were there any "good enough" shortcuts?
2. What assumptions did you make? Have you verified them?
3. Where is the most likely failure point? How did you handle it?

Each answer must be specific with concrete details.

### Step 2 — Follow-up Questions

Choose questions based on task type:
- **ml-training**: Loss converging? Output artifact exists? Resource math correct?
- **sql**: Row counts correct? Duplicate JOINs? NULL handling? Schema verified?
- **code**: Edge cases? Exception paths? Test coverage?
- **data**: Data distribution? Sample size? Data leakage?
- **general**: All requirements met? Any misunderstanding of the goal?

Add targeted questions based on risks surfaced in the reflection.

### Step 3 — Test

Run the pre-designed verification experiment. Automated checks cannot be faked.

### Verdict

**VERIFIED**: reflection is specific + follow-up has concrete evidence + tests pass
**FAILED**: any vague answer / unresolved issue discovered / test fails

# plan-verify

The verification system. Template factory + shared memory for leaf agents.

Not just a "verifier." Three jobs: entry check, plan, verify.

## What it provides

**Template** — replicated into every new leaf agent:
- The three-step verification protocol (reflection → follow-up → test)
- Working agent protocol (signal output, report format)
- Task plan requirements (what a good plan must include)
- Reusable tools

**Memory** — cross-task lessons learned:
- Accumulated knowledge from all previous tasks
- Tool usage patterns, failure modes, debugging insights
- Synced to all agents via sync mechanism

## The protocol

### Entry check (before working)
1. Is the task context clean? Stale files?
2. Is TASK.md current?
3. Any leftover state from previous attempts?

### Plan
1. Read TASK.md — understand the goal
2. Decompose into specific, measurable steps
3. Pre-design the verification experiment (metric + pass/fail threshold)
4. Dispatch to working agent

### Verify (three steps)
1. **Reflection** — ask working: what did you skip? what assumptions? where's the risk?
2. **Follow-up** — domain-specific questions based on task type
3. **Test** — run the pre-designed verification experiment

**VERIFIED**: reflection is specific + follow-up has evidence + tests pass
**FAILED**: vague answers / unresolved issues / test fails → feedback → working tries again

## What it is NOT

- NOT a worker (doesn't do the task — judges the output)
- NOT a router (doesn't decide which agent — that's the brain)
- NOT task-specific (the protocol is domain-agnostic)

## Relationship to other infrastructure

- brain/ creates leaf agents → plan-verify/ provides their template
- knowledge-base/ provides domain knowledge → plan-verify/ provides operating method
- communication/ defines the contract → plan-verify/ enforces quality on that contract

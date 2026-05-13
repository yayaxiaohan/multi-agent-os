# communication

How data flows between agents. The pipe, not the shell.

## The contract

```
Down:  TASK.md flows from sender to receiver
Up:    REPORT.md flows from receiver back to sender
```

## TASK.md format

```
## Intent
What I need done

## Context
What the fulfiller needs to know

## Deliverable
What I expect back
```

Sender describes WHAT, never WHO.

## REPORT.md format

```
## What was done
Concrete description

## Results
File paths, numbers, key findings

## Assumptions
Any assumptions, especially unverified ones

## Known limitations
Anything not done or potentially wrong
```

## Properties

- Sender doesn't name receiver
- Receiver doesn't know sender
- Same protocol everywhere — any depth, any agent type
- Filesystem native — folders are mailboxes, files are messages

## What it is NOT

- NOT resolution (non-leaf agents decide WHERE to send)
- NOT routing (the brain matches intent to agent)
- NOT verification (plan-verify checks output quality)

The pipe. Carries data. That's all.

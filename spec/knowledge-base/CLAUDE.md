# knowledge-base

The parts warehouse. Domain knowledge + platform tools for all agents.

## What it provides

**Domains** — task category knowledge:
- What this domain covers
- Verification patterns (what to check)
- Task plan requirements (what a good plan must include)
- Common failure modes (what goes wrong and why)
- Known tools

**Platforms** — infrastructure implementation knowledge:
- Interface contract (what this platform must support)
- Usage patterns (how to use the tools)
- Known quirks (gotchas, failure modes, workarounds)

## How it's used

When a new agent is created:
1. Classify: which domain(s)? which platform(s)?
2. Copy relevant domain knowledge into agent's specs/
3. Copy relevant platform tools into agent's tools/
4. The agent starts with accumulated knowledge, not from zero

## Classification

Agents are classified by domain (what kind of work) and platform (what infrastructure):

| Domain | Signals |
|---|---|
| ml-training | training scripts, GPU, checkpoints, loss, eval |
| sql | SQL queries, databases, schema |
| data | data pipelines, ETL, feature engineering |
| code | code generation, debugging, software engineering |
| research | paper reading, literature review, summarization |
| content-creation | writing, documents, resumes |
| evaluation | classification, fact-checking, semantic audit |
| verification | three-step protocol, supervision |

An agent can belong to multiple domains and use multiple platforms.

## What it is NOT

- NOT a router (doesn't decide which agent handles a task)
- NOT a verifier (doesn't check output quality)
- NOT task-specific (provides domain knowledge, not task instructions)

It's a library. Agents check out what they need.

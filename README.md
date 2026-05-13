# Subspace-Aligned Multi-Agent Architecture

A specification for recursive multi-agent systems grounded in the geometry of LLM knowledge representation.

## The one sentence

**The agent system works because folders activate the same subspaces that the model already uses to organize knowledge internally.**

## Seven principles

1. **Two agent types**: leaf (acts) and non-leaf (directs). A leaf can become non-leaf.
2. **Four infrastructure roles**, each isolated: attention, verification, knowledge, communication.
3. **One contract**: TASK.md down, REPORT.md up. Sender describes WHAT, not WHO.
4. **Recursive**: non-leaf can contain non-leaf. Any depth. No fixed levels.
5. **Activates, doesn't teach**: the LLM already has the knowledge. The system removes noise.
6. **Each level checks its own scope**. No level reaches into another.
7. **Clean context = focused agent**. Aligns with the model's internal geometry.

## What's here

```
article.html              The full design document (101 sections, 10 parts)

spec/
  brain/CLAUDE.md          Attention system — non-leaf template
  plan-verify/
    CLAUDE.md              Verification system — leaf template + memory
    common/PROTOCOL.md     Three-step verification protocol
  knowledge-base/CLAUDE.md Knowledge system — domain + platform parts
  communication/CLAUDE.md  Communication protocol — TASK.md / REPORT.md contract
```

## The theoretical foundation

Entity subspaces in LLMs (r_eff=5-9, cos=0.92, angles 77-84°) show that each entity occupies its own stable geometric region in activation space. The agent architecture mirrors this: each agent occupies its own folder, isolated from others, with an identity file that activates the right knowledge subspace.

Independent evidence: [Identity as Attractor](https://arxiv.org/abs/2604.12016) (arXiv, April 2026) confirms that identity documents induce attractor-like representational structure in LLM activation space.

## This is a specification

Not a framework. Not a library. Not a pip install.

Seven principles. Implementation-free. Build it with files, databases, APIs, Docker — the principles are the same.

We built it with a filesystem and Claude. You might build it differently.

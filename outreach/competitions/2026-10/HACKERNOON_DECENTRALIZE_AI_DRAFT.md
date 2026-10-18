# Who Authorizes an AI Agent? Separating Advice, Evidence and Action in AIOA spArkHAT

**HackerNoon Decentralize AI Hackathon — technical article draft (NOT SUBMITTED)**

Suggested tags: agentic-ai, open-source, ai-infrastructure, artificial-intelligence, decentralize-ai-hackathon

## A model can propose. It cannot authorize itself.

Much of today's agent engineering starts with a convenient line of code: take a model response, parse the tool call, and run it. That can be enough for a local demo. It is not enough to establish who gave the agent permission, which evidence the action relied on, whether the tool already succeeded, and what to do after a restart.

AIOA spArkHAT is an ongoing, local-first research and engineering project built around a different premise: **a model is a source of advice, not the authority governing the computer**.

This isn't an argument against useful agent autonomy. It is an argument for explicit boundaries around the autonomy a person chooses to grant.

## The core boundary

AIOA's public architecture describes an owner-authorized task traveling through several distinct concerns:

1. **Task and scope:** the user or operator defines an allowed task and its permissions.
2. **Model advice:** an LLM can propose a plan or next step, optionally receiving bounded critique.
3. **Evidence and provenance:** the system distinguishes source material, model statements, state and independently checked facts.
4. **Policy and human decision:** protected effects require an exact human approval rather than being inferred from model confidence.
5. **Guarded effect:** an approved operation runs through a constrained execution boundary.
6. **Receipt and readback:** recorded outcomes help establish whether an action actually happened, avoiding blind repeats after failure.

The project's slogan is simple: **provider ≠ authority**.

For example, if a coding model advises changing a configuration file, that advice alone does not confer permission to write. An authorized task, checked inputs, approved scope and the effect receipt are different records with different roles.

## Why this matters for verifiable AI

Verifiability is sometimes discussed as an all-or-nothing quality. In operational systems it is more specific.

A verifiable system can document what input was available, what was proposed, what the operator approved, which tool acted, and how the system confirmed the result. Some steps can be tested independently; other claims remain hypotheses until a suitable test exists.

That separation also matters when a model provider is replaced. The model's output format or recommendation might change, but an independently implemented authority gate should not disappear simply because a different API is now giving the advice.

AIOA explores integrations with multiple inference providers and local tool bridges, but **does not claim to be a decentralized GPU marketplace, blockchain protocol or censorship-resistant inference network**. Its relevance to open AI infrastructure is narrower and more concrete: user control, local-first operation, provenance and reproducible verification.

## Long-running work: the important failure mode

A long-running agent may eventually lose network connectivity, restart, hit an API limit or crash between making a tool request and recording a result.

The naive recovery method is to send the same request again. That risks duplicate effects. A stronger approach uses durable task state and effect receipts, plus independent readback when possible. If the system does not know whether a change happened, uncertainty is itself a state to surface—not an excuse to report success.

The public AIOA repository describes this direction with bounded execution, recovery controls and separate receipt semantics. The current bounded MCP transport has primarily READ scope; this article is not an announcement of unrestricted remote WRITE or EXEC access.

## What the public endurance evidence actually shows

A September 2026 **historical local** endurance report describes 86,426 reported active seconds and 722 hash-linked checkpoint records. A later file-integrity review checked 722 checkpoint digests and 721 predecessor links.

That is useful evidence about this particular recorded run, but it must not be promoted into general certification:

- The tested candidate is not current public main.
- The raw evidence bundle is not publicly released.
- The run attempted **zero replay attacks**, so it does not demonstrate replay-attack stress resistance.
- NVIDIA LIVE services were unavailable for that report.
- A proposed **Gold72** experiment is future work, not a completed 72-hour result.

The public [GOLD24 evidence review](https://github.com/luciferprosun/AIOA-spArkHAT/blob/main/docs/launch/GOLD24_LOCAL_EVIDENCE_REVIEW_20261013.md) discusses those limitations.

Engineering evidence is more useful when it says both what succeeded and what remains unknown.

## Where the project stands

AIOA spArkHAT has public source code, local demonstration pathways, a reviewable architecture and a growing body of engineering documentation. Linux/Android integration and longer-duration recovery tests remain active workstreams.

A separate **spArkSWARM** effort explores controlled project research, evidence tracking and outreach across developer services. Its external publishing remains bounded by human authorization; it is not a warrant for unsolicited automated posting.

We would value substantive review from developers who have built:

- policy gates for tool-using agents;
- crash-safe workflows and read-after-write verification;
- auditable context or provenance systems;
- user-owned tools that do not depend on any single model vendor.

## Reproduce, inspect, challenge

**Main code:** https://github.com/luciferprosun/AIOA-spArkHAT  
**Portfolio:** https://sparkhat.eu/aioa/  
**Technical documentation:** https://sparkhat-research.gitbook.io/sparkhat-reserch-docs/aioa-sparkhat  
**Demo video:** https://youtu.be/ABJijoNKmYM  
**Research review / discussion:** https://github.com/luciferprosun/AIOA-spArkHAT/issues

The practical question is not whether an agent can complete a dazzling demo. It is whether a person can understand and limit what the agent is permitted to do, and whether the system has honest evidence of what happened afterwards.

---

*Editorial disclosure:* AIOA spArkHAT is an active research/prototype project. Its publicly described endurance evidence relates to a specific local historical candidate. No independent production certification, live universal safety guarantee or completed Gold72 is claimed. This article is prepared for organizer and editorial review; it has not been published on HackerNoon and is not yet a contest submission.
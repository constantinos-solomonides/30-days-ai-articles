# AI Day 04 — "You can do everything right and still fail. That is life"

## The Pareto Line series: a 30-day experiment in AI use

> **Reminder**
> Articles in this series are intentionally written *mostly by AI*, with human guidance, constraints, and corrections applied explicitly. Any remaining roughness is deliberate.

---

### TL;DR
The sandbox worked. Ollama worked. OpenAI integration worked. Codex worked.

**The end goal, an autonomous OpenAI agent, still failed**

Not because of bugs, but because availability, billing clarity, and incentive alignment matter more than correctness once you attempt an AI-first workflow.

This was not a failure of engineering. It was a failure of assumptions.

---

## What I set out to do
Coming out of Day 03, the goals were intentionally modest. I wanted to:

* confirm that a local model could serve as a reliable inference engine
* introduce an agent container capable of automation
* verify whether OpenAI could be integrated cleanly into the sandbox.

The intent was not to build something impressive. It was to establish a baseline solid enough to justify pushing further into agentic territory.

From a technical standpoint, that baseline held.

---

## The sandbox did its job
The environment behaved exactly as designed. Containers were isolated correctly. UID/GID mapping was predictable. Filesystem access was controlled. Vim communicated cleanly with its sidecars. Ollama models loaded and responded consistently once cold-start latency was understood. OpenAI endpoints were reachable, and Codex authenticated and launched without friction.

There was no hidden misconfiguration left to uncover.

What failed here was something else entirely: **doing everything right and still failing**, because the AI did not question, challenge, or cross-check my assumptions. That distinction matters. It exposes a class of failure where correctness is necessary, but not sufficient. So the result is not there, but the cost remains.

---

## Where things actually broke

### An OpenAI outage
While validating the agentic path, OpenAI services were intermittently unavailable. I could have bypassed the AI and continued manually. I chose not to. Letting the blockage remain a blockage was part of the test. Any human foibles that came into play, like wasting time between checking for the outage? In line with what happens when your AI *assistant* is unavailable.

An AI-first workflow that collapses into a human-first workflow the moment the AI disappears is not, in practice, AI-first.

There were enough public reports at the time to confirm this was not isolated noise. The important point is not that outages happen—they do—but that **AI-first workflows inherit the availability profile of their providers**.

More critically, without an agent capable of continuing from where it left off, the AI becomes a harder blocker than the internet going down. When the internet is unavailable, you can still read man pages, inspect local code, and reason forward. When the AI is unavailable in an AI-first setup, progress can stop entirely.

### Billing ambiguity
The second blocker was quieter, and more revealing.

The billing interface suggested readiness. Hourly caps were visible. Authentication succeeded. Models resolved. Tools launched. And yet every real request failed because no usable credits were available.

This was not a misconfiguration. It was a **UX ambiguity with architectural consequences**. From the outside, the system appeared almost ready. From the inside, it behaved exactly like a broken system until every diagnostic path had been exhausted. The time cost to debug was still real and still had to be paid.

Worse, there was no clear pre-integration checklist—no explicit list of conditions to verify before integrating Codex into a real workflow. The burden of discovery was pushed entirely onto the user.

This is compounded by incentive misalignment. The tool is built by people whose success depends on increased usage and billable activity. A human operator, by contrast, is usually optimizing for economy of effort, predictability, and cost control. These incentives point in opposite directions.

---

## Why this matters more than it sounds
At this point, the obvious response would be to add a payment method and move on. That would both miss the purpose of the experiment and be out of scope for it, mostly financially.

Agentic systems are autonomous by design. They iterate, explore, and generate requests without constant human supervision. Binding that behavior to a paid, opaque billing system introduces multiple risks at once: runaway cost exposure, loss of predictability, and—most dangerously—severe financial impact when termination conditions or monitoring are poorly defined.

With agents, mistakes do not cost you a single bad request. They can cost you hundreds or thousands before you notice. This failure mode is not hypothetical; it is obvious once you look for it.

---

## Evaluation
Strictly speaking, on the individual level, there was no "failure". Everything worked as intended. It's the system that failed, not the components. Specifically, the infrastructure did not fail. The integration did not fail. The concept did not fail. Yet the system could not produce results and there was no clear warning to prevent me from going down a rabbit hole for one day. Codex integration went as *intended*, but not as *expected*.

What failed was **operational viability under real-world constraints**.

An OpenAI-based agentic path requires upfront payment enablement, trust in billing UX, tolerance for external outages, and confidence that agents will not silently burn money when something goes wrong. For this experiment, that combination is too fragile.

There's nothing wrong with "failing". Trying-out ways that don't work is a very normal occurrence in how human-only work goes. But I expected the AI approach to be better. "The sum of parsed knowledge and experience" and all that.

---

## Next steps
For the next step, the focus will shift toward free and open-source models, with particular attention to open-source agent frameworks. The same workflows will be attempted without paid APIs. The branch where codex was incorporated will remain unmerged, as a reference for others and perhaps for their use, since it works.

This is not an ideological shift but a pragmatic one. The goal is to understand what AI-assisted work actually costs—in time, attention, and reliability-so removing any availability constraints is necessary.

---

## Day 04 results summary
Day 04 did not produce a flashy demo. Ollama worked, code was generated successfully, much joy was had, and that was that. An agent didn't run. I did not gain a containerized assistant and the sample framework is not closer to being agentically developed.

The successes were a validated sandbox, a confirmed local baseline, and a clearer understanding of what "AI-first" actually implies in practice.

Sometimes the most useful result is identifying which path **not** to continue down—yet.

---

## Links
- **Experiment repository on** [**github**](https://github.com/constantinos-solomonides/pytest-framework-example)
- **Articles & prompts repository on **  [**github**](https://github.com/constantinos-solomonides/30-days-ai-articles)
- [**Date-limited search about the outage**](https://duckduckgo.com/?q=chatgpt+down&df=2026-02-02..2026-02-03&t=ffab&atb=v264-1&ia=web)
- **Top result from that search:**
  [ChatGPT back up after a brief outage, Downdetector shows — Reuters](https://www.reuters.com/technology/chatgpt-down-thousands-users-us-downdetector-shows-2026-02-03/?utm_source=chatgpt.com)
- **Second result from that search:**
  [ChatGPT Down: OpenAI Admits Outage Means It's Experiencing Issues — Forbes](https://www.forbes.com/sites/davidphelan/2026/02/03/chatgpt-down-openai-admits-outage-means-its-experiencing-issues/)
- **Historical outage example (June 2025):**
  [ChatGPT's ~34-hour outage affecting developers and businesses](https://www.datastudios.org/post/chatgpt-s-34-hour-outage-10-11-june-2025-timeline-technical-breakdown-and-business-impact?utm_source=chatgpt.com)
- **Historical outage example (November 2025):**
  [Major multi-component OpenAI API and ChatGPT outage](https://status.openai.com/incidents/01JMYB63BJ47J3SXV6KSCT4D2A)

---

## Disclosure
*This article is part of **The Pareto Line** series — a 30-day experiment in AI use, focused on producing Pareto-optimal outputs while keeping human judgment in the loop.*

*The series deliberately uses AI systems to draft articles and generate derivative content. A Pareto approach is followed: roughly 80% of a draft is considered acceptable, after which it is edited and corrected manually.*

*The stance throughout is deliberately skeptical. AI is treated as a useful tool, not as an authority. It is approached like an enthusiastic junior: helpful when guided and reviewed, capable of creating serious problems when allowed to operate without supervision.*

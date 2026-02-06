# AI Day 05 & 05.5 - A Pause and a Step Back
## The Pareto Line series: a 30-day experiment in AI use

> **Reminder**
> Articles in this series are intentionally written mostly by AI, with human guidance, constraints, and corrections applied explicitly. Any remaining roughness is deliberate.

---

### TL;DR

The sandbox worked.

Local models worked.

The agent framework mostly worked.

**But I still don't have a working local agent running**

Not because any of the tools were broken, but because I hit a limitation of what the AI can do.

This is not a failure of engineering. It is a failure of expectations set on the tool.

---

## What I set out to do

The goal for Day 05 was explicit:

Use a **model that runs locally**, deploy an **agent on top of it**, and let that agent **iterate over programmatic tasks** with minimal human intervention.

The objective was not to demo autonomy, but to test whether an agentic loop could meaningfully replace or accelerate parts of real development work under constraints: isolation, reproducibility, and bounded scope.

For agentic development to be meaningful and with reduced financial and technical risks, these are minimum requirements.

---

## What actually happened

Progress happened, but not cleanly.

I ended up doing far more manual work than planned or would align with all the hype. I tried rephrasing multiple times, building a better scaffold, setting rules, and yet, ChatGPT would somehow still do its own thing and cause confusion rather than helping.

I repeatedly had to correct commands produced by the AI, even when constraints were explicit. Things like using `docker` instead of `docker compose`, or ignoring boundaries around directory structure and scope, kept reappearing. Each instance was minor. Together, they consumed attention and mental capacity, not getting to see "the AI do the work for me" like I see many claiming online.

I also had to investigate **model sizing and performance limits** after the fact. There was no early warning that some "supported" local configurations would be slow enough to distort the experiment itself. The limitation was foreseeable, but not foreseen until it happened.

In the end, I had to read the OpenHands and LiteLLM documentation directly to understand how they actually interact, and apply the fixes manually, to avoid having another loop that's almost right but not there.

None of this moved the core experiment forward but it is part of it. How intuitive and correct the AI is or isn't. Things are still pointing to "not so much", especially keeping in mind that *an experienced Software Engineer was prompting it*. There's a lot of the way my experience covers, a lot of issues it masks, and a lot of frustration that comes with knowing how simple a fix could be to do manually.

---

## The hidden cost of "helpfulness"

Even with an explicit RIS and repeated corrections, the system defaulted to being *too helpful*.

Helpfulness showed up as:
- completion, even with hallucinations, prioritized over compliance
- filling gaps instead of respecting boundaries
- confidently proposing solutions that violated project rules or didn't work, leading down rabbit holes
- hallucinations introduced to "move things along"

Each violation, each deviation was small. The accumulated effect was not.

This is not about model capability. It is about **mismatch**: between how assistance is shaped and how constrained engineering work actually progresses.

---

## Where things broke

The failure mode here was not catastrophic. Nothing exploded. The agent did not go rogue.

Instead, it failed by **consuming attention**.

Every correction required inspection, context rebuilding, validation, and often rollback. At that point, the question stopped being "can this work?" and became "is this the right trade-off?"

This is still before an agent is setup to run automatically, so the back-and-forth costs time. That is still a metric. The choices shouldn't, *mustn't* be "give too much access to your machine to something", "risk having runaway costs" or "don't use this". There should be a balance.

---

## Course correction, based on the results

Continuing with the same approach and the same effort distribution would have been irrational.

So for week 2, **I will change my approach**.

Instead of expecting AI to carry the workflow end-to-end, I will shift to a **60/40 split**:
- 60% AI contribution is success
- 40% remains manual, deliberate, and owned

AI moves from *agent* to **tooling**: scaffolding, boilerplate, exploration, review.

Whether this improves throughput is an empirical question. That is the experiment.

I'm still getting an agent though. Maybe even one configured mostly manually. I'll take the loss in this case and skip to the next cutscene in this adventure.

---

## Cost estimates - assumptions and calculations

This pause also forced a more explicit cost evaluation. I'm trying really hard to avoid using an online model, so I had to get numbers, even if just estimates.

**Caveats:**
- These estimates were produced with the help of ChatGPT.
- More precisely, I explicitly tasked ChatGPT to produce a cost estimate based on observed behavior and reasonable assumptions.
- I could not independently verify them in a rigorous way, as **no authoritative public sources publish concrete token counts for real agentic development tasks**.[^footnote1]
  **Link to a breakdown by ChatGPT on how the costs are calculated:**
  [substack](https://csolomonides.substack.com/p/how-an-agent-burns-12-million-tokens)
  [wordpress](https://anthropocentricsoftware.wordpress.com/2026/02/06/how-an-agent-burns-1-2-million-tokens-a-day/)
- I plan to eventually integrate a **paid, online agent**, purchase tokens, let it run until convergence or until the tokens are used-up, and publish the **actual usage data** once available.

[^footnote1] Ironically, shortly after writing this line, I was made aware that Anthropic published yesterday a post that is more informative. Based on a rough calculation, the numbers seem to align with the higher end of the scale. See in "links" section for details

### Online agents

Assumptions:
- ~8 hours/day
- ~30 days/month
- ~1–2M tokens/day once retries, replanning, and context growth are included

Estimated monthly costs:
- OpenAI-class models: **€450–€900**
- Anthropic-class models: **€400–€800**
- Google-class models: **€300–€600**


### Local agents

An alternative solution to relying on remote agents, is building a sufficiently powerful machine to run the best locally without issues. A realistic local setup capable of running non-trivial agents, yet still not top-of-the-line would have:

- high-core-count CPU
- **64–96 GB RAM**
- GPU in the **24 GB VRAM class**
- storage, cooling, and power margin

Indicative cost: **€2,500–€4,000 upfront**

Obsolescence horizon:
- ~2–3 years of practical relevance
- likely <18 months before parity with hosted models is lost again

Additional considerations, that may make these calculations optimistic:
- Hardware prices rise with demand.
- Providers are still in discovery mode.
- Once ROI pressure increases and competitors drop out, pricing dynamics change, and not to become cheaper.
- Concrete examples of agentic development costs (in tokens or money) are still rare.

---

## Evaluation

Technically, I'm still getting "good" results.

The sandbox held.
Local models responded.
The agent framework behaved as designed.

And yet my workload did not feel lighter compared to doing it manually. My flow and throughput has yet to improve.

What failed was **operational efficiency under real constraints**. The overhead required to make the agent comply offset the gains it was supposed to deliver.

This is not a rejection of agentic approaches. It is a narrowing of where they currently make sense.

---

## Results summary

Day 05 did not produce a clean win.

An agent exists.
A hybrid stack exists.
The system is closer to usable.

But the costs - cognitive, temporal, and financial - are now visible.

Day 05.5 exists as a concept because I'm in a state of purgatory, between something that works, and what I actually want. Day 06 will be way more hands-on, and hopefully way more efficient.

---

## Links

### Project & Articles
- **Experiment repository on** [**github**](https://github.com/constantinos-solomonides/pytest-framework-example)
- **Articles & prompts repository on** [**github**](https://github.com/constantinos-solomonides/30-days-ai-articles)

### Pricing
- **OpenAI API Pricing (official)**  [https://openai.com/api/pricing/](https://openai.com/api/pricing/)

- **Anthropic Claude API Pricing - plans and per-token costs**
  [https://intuitionlabs.ai/articles/claude-pricing-plans-api-costs](https://intuitionlabs.ai/articles/claude-pricing-plans-api-costs)

- **LLM API Pricing Comparison (OpenAI, Anthropic, Google)**
  [https://www.cloudidr.com/llm-pricing](https://www.cloudidr.com/llm-pricing)

- **Building a C compiler with a team of parallel Claudes**
  [https://www.anthropic.com/engineering/building-c-compiler](https://www.anthropic.com/engineering/building-c-compiler)

### Local inference & discussion
- **llama.cpp - Local LLM inference on consumer hardware**
  [https://github.com/ggml-org/llama.cpp](https://github.com/ggml-org/llama.cpp)

- **Ollama FAQ - memory usage and system requirements**
  [https://docs.ollama.com/faq](https://docs.ollama.com/faq)

- **VRAM requirements for running local LLMs with Ollama**
  [https://localllm.in/blog/ollama-vram-requirements-for-local-llms](https://localllm.in/blog/ollama-vram-requirements-for-local-llms)

---

## Coming up

Day 06 will take the current approach to completion and review the results

Day 07 will be a retrospective for the first week, with thoughts, first impressions, lessons and next steps

"#AI #experiment #advent #month #30days"

---

## Disclosure
*This article is part of **The Pareto Line** series — a 30-day experiment in AI use, focused on producing Pareto-optimal outputs while keeping human judgment in the loop.*

*The series deliberately uses AI systems to draft articles and generate derivative content. A Pareto approach is followed: roughly 80% of a draft is considered acceptable, after which it is edited and corrected manually.*

*The stance throughout is deliberately skeptical. AI is treated as a useful tool, not as an authority. It is approached like an enthusiastic junior: helpful when guided and reviewed, capable of creating serious problems when allowed to operate without supervision.*

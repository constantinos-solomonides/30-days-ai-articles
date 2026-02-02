# Day 03 — Building an AI-Assisted Vim Sandbox
## The Pareto Line series: a 30-day experiment in AI use

## TL;DR

- Built a sandbox environment to try agentic development with minimized risk to my system
- The performance of AI in building the sandbox was comparable to reusing boilerplate
- The fact that I'm experienced with instructing computers to do things, may impact my results

---

Day 03 of the experiment focused on building an AI-assisted Vim environment inside Docker. The goal was to create a controlled, reproducible sandbox that could support local LLMs, agentic iteration, and strong filesystem isolation—without exposing the host system or relying on ad-hoc configuration. This is to avoid horror stories like [this](https://www.tomshardware.com/tech-industry/artificial-intelligence/googles-agentic-ai-wipes-users-entire-hard-drive-without-permission-after-misinterpreting-instructions-to-clear-a-cache-i-am-deeply-deeply-sorry-this-is-a-critical-failure-on-my-part) from happening.

Some may cry "foul" at this approach. They'll likely say that agents shine best when they're given access to loop over solutions until they get it right. That is understood and duly ridiculed, as the expectation of giving free reign to that extent on my host machine to something I do not control and has been known to mess up is simply absurd. An eager junior doesn't get the keys to the production database from sane seniors after all.

---

## Initial Goals and Constraints

The target environment was defined with certain limitations and expectations in place:

- Vim running inside a container
- AI assistance via a local LLM (sidecar container)
- No direct access to the host filesystem
- Persistence via bind-mounted directories (not Docker volumes)
- Non-root execution inside containers
- UID/GID alignment with the user where feasible
- Explicit avoidance of unsupervised or potentially hanging automation

This effort deliberately started from a clean slate. Prior attempts were not reused, although knowledge from two earlier attempts and updated Day-02 instructions informed the work. The branch `sandbox/v0.1.0` tracks whatever was committed from those efforts.

---

## Implementation Attempt

The environment was built using Docker Compose, combining:

- a Vim container,
- a local LLM service,
- and an optional AI agent container.

Vim was configured using `vim-plug`, with a boot-time seeding script intended to initialize configuration when persistent directories were empty.

From an architectural perspective, the setup was reasonable. From an operational perspective, it exposed several solutions provided by the AI that did not hold in practice.

---

## Issues and Failures

The main issues encountered were:

- Bind-mounting empty directories masked configuration installed during image build
- `vim-plug` was installed in paths that do not exist on Debian-based images
- Vim autoload behavior was misunderstood (`exists('*func')` is not a valid check)
- Runtime path ordering prevented plugins from loading
- Sentinel-based "run once" logic blocked reseeding after fixes
- `PlugInstall` did not create the expected `plugged/` directory
- Several failures were only diagnosable after copying exact error output
- Some automation paths could have hung or failed silently if left unsupervised
- A number of assumptions did not align with everyday Vim or Docker defaults

Individually minor, these issues compounded into significant friction.

To be fair, each and every one of those errors could have been done by a human as well. I will in fact admit that I could be that human without a doubt. However, having to *read* someone else's code instead of writing it means that we shifted the problem of writing code to reading it. This [is](https://medium.com/pythonic-thinking/reading-code-is-harder-than-writing-it-heres-how-i-finally-got-better-at-it-aa1c14ffc1d8) [not](https://www.joelonsoftware.com/2000/04/06/things-you-should-never-do-part-i/) [ideal](https://duckduckgo.com/?t=ffab&q=reading+code+is+harder+than+writing+it&atb=v264-1&ia=web) as it's harder to read than write code.

---

## Debugging and Corrections

Progress required repeated manual intervention: inspecting Vim's effective runtime state, correcting filesystem assumptions, and forcing reinitialization when automation short-circuited itself. When trying to **deploy** a safe environment to allow iteration, this challenge is something that becomes a bottleneck.

The environment was ultimately made functional, but not by automation converging on its own. The final 20% required hands-on correction.

---

## Comparison With Reusing Existing Boilerplate

On the journey to learn enough to be considered a senior Software Engineer you accrue experience and a lot of boilerplate. For me, and I expect for others as well, that is in the form of personal fun projects where I solved issues in some way and in test snippets I developed to answer questions on "how does that work". One mark AI should reach is "be simpler to use it than reuse and adapt old code"

From a cost–benefit perspective:

**Effort**
Roughly aligned with the 20/80 rule for a first iteration.

**Outcome**
No significant improvement over reusing an existing, familiar boilerplate.

**Disadvantages**
- Required navigating an unfamiliar workflow
- Introduced new failure modes
- Increased cognitive overhead for routine tasks

**Advantages**
- Exposed hidden assumptions
- Improved understanding of Vim, autoloading, and container boundaries
- Provided learning value despite limited immediate payoff

At this stage, the new approach does not clearly justify replacing the old one. Still, I will persevere, because \-supposedly\- the more I use AI the better it adapts. This is after all the spirit of this 30 day experiment. Comparing the last days to the first, not taking each individually

---

## First coding day summary

Overall, the tool is not prohibitively complex to use. AI can produce decent but not fully correct pboilerplate, providing a decent starting point. Better results can be gleamed after using the sandbox and let the agent(s) run for a long time independently.

---

## Next Steps

Day 04 will focus on putting the environment to actual use and debugging real workloads inside it. The question is no longer whether the sandbox can be made to work, but whether it meaningfully improves day-to-day development.

Work and artifacts are tracked here:

- https://github.com/constantinos-solomonides/30-days-ai

---


## Links

* Repository with the experiment commits on [github](https://github.com/constantinos-solomonides/30-days-ai)
* Repository tracking the AI-Assisted project recreation on [github](https://github.com/constantinos-solomonides/pytest-framework-example)

---

*This article is part of **The Pareto Line** series - a 30-day experiment in AI use, focused on producing Pareto-optimal outputs while keeping human judgment in the loop.*

*The series deliberately uses the paid version of OpenAI to draft articles and generate shortened LinkedIn posts. A Pareto approach is followed: roughly 80% of a draft is considered acceptable, after which it is edited and corrected manually.*

*The stance throughout is deliberately skeptical. AI is treated as a useful tool, but not as an authority. It is approached like an enthusiastic junior: helpful when guided and reviewed, and capable of creating serious problems when allowed to operate without supervision.*

*Alongside writing, a mix of local and online AI models is also being used to rebuild scaled-down versions of older projects previously developed under enterprise constraints. Older projects are chosen on purpose to provide a known baseline, making it easier to assess what AI actually changes in both workflow and outcome.*



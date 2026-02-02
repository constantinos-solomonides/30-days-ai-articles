<!--
Series: 30 Day AI Experiment
Day: 03
Focus: Environment setup, AI-assisted development, reality check
-->

# Day 03 — Attempting an AI-Assisted Vim Sandbox (and What It Actually Took)

Day 03 of the experiment focused on building an AI-assisted Vim environment inside Docker. The goal was to create a controlled, reproducible sandbox that could support local LLMs, agentic iteration, and strong filesystem isolation—without exposing the host system or relying on ad-hoc configuration.¹

This was not an exercise in novelty. The intent was to evaluate whether such an environment meaningfully improves on an existing, familiar boilerplate—or whether it simply replaces known complexity with a different kind of friction.

---

## Initial Goals and Constraints

The target environment was defined by a set of non-negotiables:

- Vim running inside a container
- AI assistance via a local LLM (sidecar container)
- No direct access to the host filesystem
- Persistence via bind-mounted directories (not Docker volumes)
- Non-root execution inside containers
- UID/GID alignment with the host where feasible
- Explicit avoidance of unsupervised or potentially hanging automation

This effort deliberately started from a clean slate. Prior environments were not reused, although knowledge from two earlier attempts and updated Day-02 instructions informed the work.

---

## Implementation Attempt

The environment was built using Docker Compose, combining:

- a Vim container,
- a local LLM service,
- and an optional AI agent container.

Vim was configured using `vim-plug`, with a boot-time seeding script intended to initialize configuration when persistent directories were empty.

From an architectural perspective, the setup was reasonable. From an operational perspective, it exposed several assumptions that did not hold in practice.

---

## Issues and Failures

The main issues encountered were:

- Bind-mounting empty directories masked configuration installed during image build
- `vim-plug` was installed in paths that do not exist on Debian-based images
- Vim autoload behavior was misunderstood (`exists('*func')` is not a valid check)
- Runtime path ordering prevented plugins from loading
- Sentinel-based “run once” logic blocked reseeding after fixes
- `PlugInstall` did not create the expected `plugged/` directory
- Several failures were only diagnosable after copying exact error output
- Some automation paths could have hung or failed silently if left unsupervised
- A number of assumptions did not align with everyday Vim or Docker defaults

Individually minor, these issues compounded into significant friction.

---

## Debugging and Corrections

Progress required repeated manual intervention: inspecting Vim’s effective runtime state, correcting filesystem assumptions, and forcing reinitialization when automation short-circuited itself.

The environment was ultimately made functional, but not by automation converging on its own. The final 20% required hands-on correction.

---

## Comparison With Reusing Existing Boilerplate

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

At this stage, the new approach does not clearly justify replacing the old one.

---

## Lessons Learned

- Strong isolation amplifies initialization complexity
- Automation must be observable and restartable
- Incorrect mental models are more expensive than incorrect code
- New workflows must earn their complexity through clear benefits

---

## Next Steps

Day 04 will focus on putting the environment to actual use and debugging real workloads inside it. The question is no longer whether the sandbox can be made to work, but whether it meaningfully improves day-to-day development.

Work and artifacts are tracked here:

- https://github.com/constantinos-solomonides/pytest-framework-example
- https://github.com/constantinos-solomonides/30-days-ai

---

¹ *This article is part of a 30-day, day-by-day experiment exploring how AI tools fit into real development workflows. The focus is on practical outcomes rather than polished success stories.*

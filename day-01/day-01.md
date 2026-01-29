## TL;DR

- This entry focuses on **portfolio development**, not writing
- I’m rebuilding older projects to measure where AI actually helps
- AI speeds up scaffolding and recall, not judgment or correctness
- Progress is uneven by design, and that’s part of the data

---

### Series Disclosure

*This article is part of a 30-day experimental series where I deliberately use the paid version of OpenAI to write articles and generate shortened LinkedIn posts. I use a Pareto approach: getting roughly 80% of the draft is acceptable, and I then edit and correct the result (see the [Pareto principle](https://en.wikipedia.org/wiki/Pareto_principle)).*

*I’m AI-skeptical in the sense that I consider AI a useful tool, but not what industry hype often claims it to be. I treat it like an enthusiastic junior: it can produce solid results when properly guided and reviewed, but it can create serious problems if allowed to operate without supervision.*

*Alongside writing, I’m also using a mix of local and online AI models to rebuild scaled-down versions of older projects I previously worked on in enterprise settings. I’m choosing older projects on purpose: they give me a baseline that makes it easier to assess what AI actually changes in the development workflow and in the final outcomes.*

---

## Why You Should Read This

If you’re curious whether AI actually helps with real development work rather than demos,
if you’ve seen AI generate plausible code that collapses under scrutiny,
or if you want a clearer picture of where AI saves time *and where it doesn’t*,
this article is meant as a way to reason about that boundary.

---

## Narrative Introduction

When people talk about AI in software development, the examples are usually clean.

Greenfield projects. Toy problems. Carefully chosen prompts. What’s missing is friction: legacy assumptions, half-remembered decisions, and constraints that only exist because something once had to run in production.

That’s why I’m rebuilding older projects instead of inventing new ones.

---

## Framework Definition — Baseline Before Acceleration

The framework guiding this part of the experiment is **Baseline Before Acceleration**.

**Metaphor:** timing a runner only after you’ve marked the track.

1. **Known Reference Point**
   - Includes: prior architecture, tradeoffs, and mistakes
   - Excludes: speculative redesigns
   - Ignoring it makes improvement claims meaningless

2. **AI as Recall, Not Authority**
   - Includes: scaffolding, boilerplate, pattern recall
   - Excludes: correctness, domain judgment
   - Ignoring it turns confidence into bugs

3. **Change Attribution**
   - Includes: tracking what AI altered vs. what stayed the same
   - Excludes: vague “it helped” conclusions
   - Ignoring it collapses cause and effect

This framework exists mostly to stop me from lying to myself about progress.

---

## Application Example — Current Portfolio Work

The current focus is a scaled-down reconstruction of an older internal tool I once built under enterprise constraints.

AI is useful here in very specific ways:
- Recalling framework idioms I haven’t touched in years
- Producing rough scaffolding quickly enough to be disposable
- Acting as a second set of eyes when refactoring unfamiliar code paths

It is *not* useful as:
- A source of architectural decisions
- A verifier of correctness
- A substitute for understanding why the original system behaved the way it did

A cheaper alternative would be to let AI redesign the tool entirely. That would look impressive and tell me very little. By constraining myself to reconstruction, I trade novelty for comparability.

Progress is slower than hype would suggest — but clearer.

---

## Reflection & Invitation

So far, the most consistent benefit isn’t speed. It’s reduced friction when returning to old mental models.

If you think rebuilding old projects is the wrong way to evaluate AI, I’d want to know what baseline you’d trust instead.
If you think I’m underusing the tool, I’m interested in where you’d be willing to give up control.

Either way, those disagreements are part of what I’m tracking as this continues.

---

### Mechanical + Disclosure Lint Check

- Mechanical smell: pass
- Hype leakage: none
- Disclosure completeness: pass

**Status:** Inspection pass

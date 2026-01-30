## TL;DR

- This entry focuses on **portfolio development**, not writing
- I'm rebuilding older projects and implementing existing ideas to measure where AI actually helps
- AI speeds up scaffolding and recall, not judgment or correctness
- Progress is uneven by design, and that's part of the data

---

### Series Disclosure

*This article is part of a 30-day experimental series where I deliberately use the paid version of OpenAI to write articles and generate shortened LinkedIn posts. I use a Pareto approach: getting roughly 80% of the draft is acceptable, and I then edit and correct the result (see the [Pareto principle](https://en.wikipedia.org/wiki/Pareto_principle)).*

*I'm AI-skeptical in the sense that I consider AI a useful tool, but not what industry hype often claims it to be. I treat it like an enthusiastic junior: it can produce solid results when properly guided and reviewed, but it can create serious problems if allowed to operate without supervision.*

*Alongside writing, I'm also using a mix of local and online AI models to rebuild scaled-down versions of older projects I previously worked on in enterprise settings. I'm choosing older projects on purpose: they give me a baseline that makes it easier to assess what AI actually changes in the development workflow and in the final outcomes.*

---

## Why You Should Read This

If you're curious whether AI actually helps with real development work rather than demos,
if you've seen AI generate plausible code that collapses under scrutiny,
or if you want a clearer picture of where AI saves time *and where it doesn't*,
this article is meant as a way to reason about that boundary.

---

## Narrative Introduction

When people talk about AI in software development, the examples are usually clean.

Greenfield projects. Toy problems. Carefully chosen prompts. What's missing is friction: legacy assumptions, half-remembered decisions, and constraints that only exist because something once had to run in production.

That's why I'm rebuilding older projects instead of inventing new ones and writing articles that were already in my mind to write. The conception part has been done and I know how much either of those would take me without AI, so I can better compare my outcomes to what I actually achieve.

### Disclaimers

- I fully expect that the first few articles and portfolio steps will take longer to do with AI, even compared to what I would do without. This is normal as tuning the tools is a big part of work anyway. The idea is that the AI, like an assistant, gets to "know" me better with each iteration and becomes more and more independent.
- In this series I do not explore any topics on security, privacy and other concerns, such as data sovereignty. I do expect those to be crucial concerns and perhaps can be explored in the future.
- I also do not explore the topic of cost and economical, ecological, moral or aspects of AI use. Those are perhaps the most important but they are not an issue inherent in the tool or its use, but of how it's being rolled-out and used by vendors, thus a different discussion
- I have not taken any formal classes on AI prompting but I did copy ideas I saw and liked. I'm examining the idea is that the tool can be useful with *intuitive* use. "A highly trained expert succeeds" is not an AI success story, it's a formal education story.

---

## Framework Definition - Baseline Before Acceleration

The framework guiding this part of the experiment is **Baseline Before Acceleration**.

**Metaphor:** timing a runner only after you've marked the track.

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

## Bonus metric - consistency

An issue I always face with my writing and development is inability to be consistent. This is due to many factors, including:

    - Analysis paralysis
    - Feeling the need to branch to multiple related topics as I discuss any one
    - Multiple editing rounds and analysis paralysis when trying say things

Therefore a failure to be consistent does not point to an interruption to the experiment, but is actually a result that will be added to it. If AI doesn't make it possible, or at least significantly easier, to be consistent, it will point to an issue with the use of AI in producing results. Let's keep in mind that it's been tooted as something you can actually offload your work to **significantly** compared to doing it yourself.

---

## Application Example - Current Portfolio Work

The current focus is scaled-down reconstructions of older internal tools I built under enterprise constraints.

I expect that AI will useful here in very specific ways:
- Recalling framework idioms I haven't touched in years
- Producing rough scaffolding quickly enough to be disposable
- Acting as a second set of eyes when refactoring unfamiliar code paths

I do not expect it to be:
- A source of architectural decisions
- A verifier of correctness
- A substitute for understanding why the original system behaved the way it did

Perhaps a cheaper alternative would be to let AI redesign the tool entirely. That would look impressive and tell me very little. By constraining myself to reconstruction, I trade novelty for comparability.

I fully expect that progress will be slower than hype would suggest - but clearer.

---

## Reflection & Invitation

So far, the most consistent benefit isn't speed. It's reduced friction when returning to old mental models.

If you think rebuilding old projects is the wrong way to evaluate AI, I'd want to know what baseline you'd trust instead.
If you think I'm underusing the tool, I'm interested in where you'd be willing to give up control.

Either way, those disagreements are part of what I'm tracking as this continues.

---

## Links

* Repository with the experiment commits on [github](https://github.com/constantinos-solomonides/30-days-ai)

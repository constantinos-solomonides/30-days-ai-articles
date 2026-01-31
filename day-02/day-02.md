# AI Day 02 - On Writing Good Documentation
## The Pareto Line series: a 30-day experiment in AI use

## TL;DR

- Documentation is often avoided, not because it's difficult, but because it's treated as optional
- Writing it later usually means writing never or writing fiction
- Consistency matters more than polish
- AI can help with cleanup and structure, not understanding

---

## Why documentation goes wrong

Most developers will complain when the documentation they need is poor or even missing entirely. Yet, they never write documentation themselves. Or it gets written at the end, from memory, under time pressure, when attention has already shifted elsewhere. They write in in other words at a time context is already gone.

Some of this is systemic. Agile and SCRUM are often misinterpreted as processes that make documentation unnecessary. Documentation is also rarely treated as a first-class deliverable, which makes it easy to deprioritize indefinitely. Documentation is treated as a liability, when in fact its absence is a debt; one causality comes to collect one way or another.

- Testing - and thus releases - takes longer than expected or misses the mark
- Releases depend on tribal knowledge, being blocked by the wrong people being away
- A small number of people become bottlenecks

Other issues are not -primarily- systemic but instead stem from a lack of personal standards. Treating documentation as meaningless is a choice. Treating it as someone else's responsibility is a choice. Waiting for the "right time" is also a choice. Not having a system for it in place is a choice. Those are areas where individual action still matters and can make a difference, even in imperfect environments.

---

## Documentation is an insurance policy.

It's for when your house is on fire. You don't go around hoping for it to happen, but when it does, it's got you covered. And like all insurance policies, if you don't plan right, you'll end up not getting what you thought you would.

Let's try a less violent concept, one most of us are familiar with. How we handle laundry. Some, throw everything into a growing pile. It's easy, it's fast, takes no time to implement and woe betide you should you need something specific fast. Others carefully fold and put everything away immediately. Maintaining it requires discipline, when things get busy it tends to collapse and it costs time and effort every single day. Should you need something in a hurry however, you know where it is and that it's ready to wear.

Documentation has the same tension. Optimizing only for speed creates a mess. Optimizing only for order becomes expensive.

---

## Documentation past the surface

### What kind of documentation exists

Documentation isn't one thing. Developer notes, testing instructions, user guides, and design rationale all serve different purposes. Problems arise when only one of these is considered worth writing, or when everything exists only as spoken explanation. The old adage of "it's like pizza, even when it's bad is good" only holds if you've ever been *really hungry* and you've had *really bad* pizza. Much like it, it'll make you sick to your stomach and weigh you down, and you'll wish for something, anything else if possible.

### Who it's actually for

This is the part I find most people get wrong. Documentation is often framed as something written for *others*. In practice, one of its most important audiences is *a future version of the person writing it*. Writing things down while they're still obvious saves time later. Waiting assumes memory will cooperate. If it does, it's usually in the way of the fay. It'll trick you, lead you astray and make you waste time that you don't have, laughing at you all the while.

### How to do it without burning time

Ironically, the same method that works best with how to treat laundry, works with doing documentation. Small piles for the immediate, everything else put neatly in its place. In other words, what works best is not choosing one extreme, but mixing the two.

Applied to documentation, that means:
- Keep rough notes while working
- Don't block progress on perfect structure
- Explicitly record assumptions while they're still visible
- Make it happen after you've cleaned everything up properly

In other words, have a file / directory in whatever format works for you where you pile everything up, keeping *some* order. If you need to set a variable, use a file that you source, if you need to activate something, record the instructions as a step and then do it. Once you make it end to end, start from a clean state (vanilla VM / container, new venv, fresh login etc.) and record everything you do to get it to work. Try to automate as much as possible. Remember, a commented automated setup script counts as documentation too.

---

## The time I cashed the check I wrote

It came to me as to us all, I didn't think the hammer would fall. Yet, testing work had to be done for a team that provided no written documentation and it fell on me to do it. Like all true champions of "It works on my machine", their process didn't have documentation because of course not. More precisely, they had a wonderful circular piece of insanity, where they would refuse to give us a step-by-step on setting it up on their lab ("You need to do it like it'll be done in the customer premises") and then they would refuse to give us generic instructions ("We'll show you how we do it in our lab").

That went as well as someone with an iota of experience in our field would expect. Important limitations went unmentioned. Assumptions were implicit and were discovered because you broke something. We were testing not so much the product or the process as the ability to get information from people who were too proud to admit they needed to provide it.

So I followed my own advice. Everything was written down. First in a personal file. Then in a shared document. Then rewritten again from a clean state, with assumptions made explicit instead of implied, every step being testing to verify it works when nothing is assumed and not stated. Months later, the same work had to be picked up again, first by me and then handed over to a colleague. Even I who worked on it the last time couldn't remember almost anything in my mind. That however didn't matter because I wasn't relying on my memory in synapses but instead on my memory in bits, and that was way less fickle. Most of my work could be resumed without questions or walkthroughs. Most of the handover was a sentence: "here are these documents and files detailing everything, ask me if you need anything"

---

## A shift that stuck

To be clear, I'm not a special snowflake. I didn't adopt this approach from theory or idealism. I adopted it due to a canceled layoff.

Company was restructuring and laying people off and I was the latest hire, not yet having shown my worth. I was blindsided and handed over an unholy mess. Later, that layoff was converted into an internal move. The same people I handed over to I interacted with daily still and could ask me questions on what I did. Thankfully, I wrote unit tests and comments enough. Still, I felt uncomfortable, thinking "I must do better".

Since then, my approach to documentation has been different. Daily work goes into a rough file. From time to time, it gets rewritten from scratch. Steps are recorded. Assumptions are written down. It isn't as easy as trusting I won't be let go again, but it sure is way more reliable. With repetition, it also becomes easier. Handover stops being a major event and becomes routine if you do a bit of it each day. As a bonus, you're saved from asking what the idiot who was in your shoes was thinking six months ago when they didn't explain anything in a document and now you have to pick-up where you left-off without so much as a comment to demystify the code.

---

## How AI changes things and how it doesn't

AI lowers the cost of cleanup. It helps reorganize notes, reduce repetition, and turn rough material into something readable. It can't understand for you. It can't guarantee that it parses your notes correctly. It doesn't know which assumptions are wrong or which details matter. It simply polishes what it's given to the best of its abilities. Like an enthusiastic junior, it wants to help, but it's not sure to do so. The same rule applies here as elsewhere: AI is useful, but it requires supervision.

One new category is emerging, though: documentation written specifically so AI tools can work without guessing. That doesn't replace human documentation; it adds another audience that also needs clarity. This series uses it in fact. In the repository that comes with the series, you'll find a file called `RIS.md` that will evolve as my interaction with the AI system improves. Another, or maybe many others, will be a part of the portfolio work. The files will be discussed more in the introspective articles, but until then, you can check them out directly in the repository.

---

## Closing

Documentation is often framed as wasted time. In practice, it's reflection time. Trying to explain how something works forces gaps, contradictions, and fragile assumptions to surface. Those problems exist whether or not they're written down. Documentation simply removes the ability to ignore them. You don't need a rubber duck, a blank page works just as well.

---

## Links

* Repository with the experiment commits on [github](https://github.com/constantinos-solomonides/30-days-ai)

---

*This article is part of **The Pareto Line** series - a 30-day experiment in AI use, focused on producing Pareto-optimal outputs while keeping human judgment in the loop.*

*The series deliberately uses the paid version of OpenAI to draft articles and generate shortened LinkedIn posts. A Pareto approach is followed: roughly 80% of a draft is considered acceptable, after which it is edited and corrected manually.*

*The stance throughout is deliberately skeptical. AI is treated as a useful tool, but not as an authority. It is approached like an enthusiastic junior: helpful when guided and reviewed, and capable of creating serious problems when allowed to operate without supervision.*

*Alongside writing, a mix of local and online AI models is also being used to rebuild scaled-down versions of older projects previously developed under enterprise constraints. Older projects are chosen on purpose to provide a known baseline, making it easier to assess what AI actually changes in both workflow and outcome.*


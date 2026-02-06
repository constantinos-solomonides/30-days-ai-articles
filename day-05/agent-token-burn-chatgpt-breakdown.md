# How an Agent Burns 1–2 Million Tokens a Day
## A concrete breakdown, not a pricing scare story

---

**NOTE** This is written by ChatGPT, following the prompt:

```
Previously in the conversation you stated that it would cost approximately 1-2M tokens per 8-hour days to run an agent in a loop until it converges to create software. Explain your reasoning and show your work.
```

There was **NO** human involvement in it's writing, other than adding this note. So "I" in the text below, is first-person for ChatGPT, not a human being

---

This article exists because “tokens” are often discussed abstractly, while agentic workflows consume them very concretely.

When I previously stated that **running an agent in a loop for a full working day can consume ~1–2 million tokens**, that was not a slogan. It was an order-of-magnitude estimate derived from how agents actually behave once you stop demoing and start iterating.

This post shows the reasoning and the math.

---

## What is being counted

A **token** is not a word and not a character. It is the unit of accounting used by language models after tokenization.

For any single agent step, *all* of the following are counted:

- system prompt
- developer instructions
- conversation history still in context
- task description and constraints
- tool schemas
- code excerpts, diffs, logs, test output
- the model’s generated response

Even if the human typed one short command, the agent usually resends a large context.

> **Tokens per step = everything the agent sends + everything it receives back**

---

## What an “agent step” looks like in practice

An agentic coding loop typically looks like this:

1. Read task + current state
2. Plan next action
3. Call a tool (edit files, run tests, inspect output)
4. Evaluate results
5. Decide whether to retry, revise, or proceed

Each of those cycles usually involves **one model call**. Sometimes more.

---

## Token usage per step (realistic ranges)

### Input tokens

A plausible breakdown for one step:

- System + developer scaffolding: **1,000–3,000**
- Task description + constraints: **500–2,000**
- Conversation history in window: **2,000–10,000**
- Tool schemas and instructions: **2,000–8,000**
- Code context (files, diffs, logs): **2,000–12,000**

**Input total per step:**
→ **~8,000 to 25,000 tokens**

---

### Output tokens

Typical output includes:

- Plan / reasoning: **500–2,000**
- Tool call JSON or instructions: **200–1,500**
- Code blocks or patches: **500–4,000**

**Output total per step:**
→ **~1,200 to 7,500 tokens**

---

### Combined tokens per step

- **Low**: ~9,000 tokens
- **Mid**: ~18,000 tokens
- **High**: ~32,000 tokens

That’s for **one agent step**.

---

## How many steps happen in a day

A realistic agent usually completes:

- **5–10 meaningful steps per hour**

Over an **8-hour workday**:

- 5 steps/hour → **40 steps/day**
- 10 steps/hour → **80 steps/day**

---

## The arithmetic

### Conservative lower bound

```
40 × 9,200 = 368,000 tokens/day
```

### Realistic mid-range

```
60 × 18,000 = 1,080,000 tokens/day
```

### Heavy agent loop

```
80 × 32,500 = 2,600,000 tokens/day
```

---

## Why “1–2 million” is a reasonable estimate

Because once you move beyond demos:

- context grows throughout the day
- retries are normal
- scaffolding is resent
- failures multiply steps

The **median working range** for a serious agent loop lands around:

> **~1–2 million tokens per full working day**

---

## Why this matters

- Online agents convert tokens directly into money
- Local agents convert tokens into latency

In both cases, convergence — not generation — is where the cost lives.

---

## Closing

Token economics only become visible when you try to live inside an agentic workflow.

Once you see the numbers, design decisions stop being theoretical.

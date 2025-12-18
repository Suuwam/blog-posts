---
title: Prompt Engineering is Just API Design With Worse Tooling
date: 2025-11-05
tags: [prompting, apis, product]
excerpt: |
  Prompts aren't magic, they're messy contracts. Here’s why treating prompts like you treat APIs saves you (and your teammates) headaches.
---

## If an API Looked Like Most Prompts...

I'll confess: I used to "prompt engineer" by throwing instructions into a long string until it looked like a ransom letter.  
- "Assume you're an expert in X."  
- "Be concise, but also detailed."  
- "Give JSON unless I say don't."  
- "Unless the date is Thursday, don't use jokes."  
- ...and the result: chaos.

When I worked with a team on a real product, this fell apart. Prompts broke at the worst times, updates for one edge case made three others worse, and onboarding new devs was…painful.

### API Perspective: What Changed For Me

If you treat your prompt like an API contract, you start to think about:
- **Versioning:** When you change the prompt, is it backwards compatible?  
- **Inputs/Outputs:** Is the structure clear, or vibe-based and brittle?  
- **Tests:** Can new devs (or future-you) check that outputs are actually right?  

#### What Works (in My Experience):

**1. Stable System Prompt as "Contract"**  
I now write one system prompt per feature—*never* in-line-in-code.  
It’s the “rules of the road” for the model: tone, allowed actions, hard constraints.

**2. Tiny, Swappable Task Prompts**  
Think of the user or per-request part as the "input" to a function.  
Keep it dead simple, e.g. "Summarize this text for a six-year-old."

**3. Output Format = Schema (Declared Up Front)**  
Now I show the model *real* output examples (JSON, markdown, table) right in the prompt.  
If you don’t, you will regret it. Models hallucinate structure if you rely on “please, emit JSON.”  
Pro-tip: If possible, validate responses with a schema (use zod in TS, pydantic in Python, etc) and let the model self-correct.

### A Real Painful Story

We once built a chatbot where the prompt was patched and tuned by at least three different engineers over two months.  
- No one “owned” the schema.
- Nobody knew what the actual default instructions were.
- Bugs crept in: date formatting, persona slipped from helpful to passive-aggressive, output started switching from markdown to HTML at random.

It took a week to refactor and add actual contracts & output checks, but we never had the weirdest bugs after that.

---

**Lesson:** Treat prompts as living, documented, versioned contracts—just like APIs. Lives (and sleep cycles) will be saved!

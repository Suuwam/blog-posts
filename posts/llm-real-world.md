---
title: From Toy LLM Demo to Production System: What Actually Breaks in the Real World
date: 2025-12-18
tags: [llms, evaluation, prompting, systems design]
excerpt: |
  An honest look at why student LLM projects-and even many startup demos-crash and burn in real-world use. Hint: It's not the model, it's everything else.
---

## I Broke My Own Demo. Here’s What Happened.

I’ll be honest: my earliest LLM demos *always* felt magical… until someone else used them. I remember shipping what I thought was a clever question-answer bot to a student team. Within 24 hours, it hallucinated that bananas were a type of gemstone and returned a JSON object that was missing half the keys. Oops.

It's never the model's fault. It's the system. Here are the gory details of what broke:

- **Stuffing too much into the context:** “Surely if I paste ALL the user’s notes, the model will get it.” Spoiler: It didn’t. It choked, got slow, and started ignoring key info.
- **No real eval loop:** My “testing” was eyeballing a few happy path answers and thinking, “looks good!” But real users broke it with typos and weird edge cases I never addressed.
- **Total UX confusion:** Users assumed this thing “knows everything.” Someone typed in a spreadsheet formula and expected the bot to run it. Another tried asking about data the model was never trained on.
- **No guardrails:** The model would occasionally manufacture confident nonsense. Did I handle that? Initially, I’d just laugh and hope no one noticed.

---

## “Probabilistic APIs with Contracts,” Not Magic

I wish someone had drilled this into me sooner: LLMs are **probabilistic functions with contracts**. Not psychic oracles. To make your thing reliable you have to own:
- What **inputs** you give it (schemas, system prompts, tools, etc.).
- The **budget** (how fast, how many tokens, how much $ per call).
- The **failure modes** (wrong, slow, or just plain empty).

Here's a snippet that saved my bacon (in TypeScript-style pseudocode):

```js
// Robust LLM wrapper: logs, validates, retries
async function callLLM({ prompt, schema, maxRetries = 2 }) {
  const start = Date.now();
  let attempt = 0;

  while (attempt <= maxRetries) {
    attempt += 1;
    const raw = await llm.chat({ prompt, model: "gpt-4-mini", temperature: 0.2, max_tokens: 512 });
    const latency = Date.now() - start;
    logEvent("llm_call", { latency, attempt, promptLength: prompt.length });

    // Try parsing/validating output
    const parsed = safeJsonParse(raw.content);
    const validated = schema.safeParse(parsed);

    if (validated.success) return validated.data;

    // On fail: re-prompt the model to fix itself
    prompt = buildSelfCorrectionPrompt(prompt, raw.content, schema);
  }

  throw new Error("LLM failed to return valid data after retries");
}
```

**Why bother?**
- Enforces the *model, temperature, and token budget*-no mystery runs.
- Logs latency so future-me can actually debug slow calls.
- Validates output (with Zod or similar), not just “hope it looks right.”

---

## Honest Advice (For Your Next Project)

- **Log everything.** When, how long, what you sent, what you got back. I regret every project where I skipped this.
- **Assume naive users.** Whatever your system does, someone will use it "wrong." That's not on them, it's on your design.
- **Be suspicious of demos.** If you've never seen your thing fail, you haven't tested it.
- **Iterate in public.** The best feedback I've gotten is from showing my unfinished, ugly version to users who gave honest, painful feedback.

---

*Filed under: shipped, broken, learned, and tried again. If you want the full saga or to share your battle scars, let’s connect!*

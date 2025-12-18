---
title: Prompt Engineering is Just API Design With Worse Tooling
date: 2025-11-05
tags: [prompting, apis, product]
excerpt: |
  Prompts aren't magic, they're messy contracts. Here’s why treating prompts like you treat APIs saves you (and your teammates) headaches.
---

I found this out the hard way: Early on, I’d throw instruction after instruction into a prompt until it looked like a ransom note. What broke? Everything—outputs drifted, context got confusing, and my teammates didn’t know what to expect.

**The trick:**

- **System prompt = your “stable” contract** (who is this bot, what should it *never* do?).
- **Task prompt = what the user wants, right now.**
- **Output schema:** Even if it's just a JSON “example” in the prompt, declare what comes out!

Reviewing failed “prompt hacks” in old projects, I realized I was just missing clear contracts and versioning—the stuff I always respected in real API design. Lesson learned.

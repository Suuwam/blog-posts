---
title: RAG for Humans: Designing Retrieval That Feels Intuitive
date: 2025-12-01
tags: [rag, ux, search]
excerpt: |
  RAG diagrams are easy. Building a retrieval system normal people trust? Now that’s hard. Here’s what I found.
---

When I built my first RAG prototype, it was honestly fun but...nobody trusted it. The system returned answers that felt right *to me* as a builder, but regular users said: "What did this even search? Why did it miss my document? How do I correct it?"

What worked after some painful feedback:

- **Expose your sources:** Show where answers come from—actual snippets, not just “source: database.”
- **Let users filter/search scope:** Don’t make them guess; let them choose “search only docs” or “FAQ/manual.”
- **Make feedback easy:** A single "this answer is wrong" button loops directly into evaluation and education.

Worry less about the vector math, more about what an honest, busy user expects. My original code wasn't perfect, but user trust improved the moment I showed *my* homework, too.

---
title: Winning Relay Hack X Aqore – Solving Real Staffing Problems Beyond PHP CRUD
date: 2025-11-05
tags: [hackathon, staffing-software, sql, php, system-design, teamwork, nepal]
excerpt: |
  Our team won the Relay Hack X Aqore hackathon by addressing real staffing system problems—moving beyond basic PHP CRUD apps to a database-driven, enterprise-style solution for candidate screening and shortlisting.
---

## Relay Hack X Aqore – Hackathon Win

I’m excited to announce that our team secured victory at the **Relay Hack X Aqore Hackathon**, hosted at **Techspire College**. Working alongside my teammates **Shuvam Khanal** and **Safal Lohani**, we took on the **Staffing Software Innovation Challenge**—a domain that’s mature globally but still underdeveloped and poorly implemented in Nepal.

This wasn’t another “build a form and save data” hackathon. The problem demanded **system thinking**, not just code output.

## The Real Problem

Most staffing systems built locally suffer from the same issues:

- PHP applications reduced to **basic CRUD** with no real domain logic  
- Business rules scattered across controllers instead of enforced centrally  
- Poor candidate filtering—manual shortlisting, keyword hacks, or Excel exports  
- No structured handling of **skills, experience, availability, and role matching**
- Tight coupling between UI logic and backend rules, making systems fragile

In short: **apps work, systems don’t scale**.

## Our Focus: Candidate Screening & Shortlisting

We deliberately focused on the **Candidate Screening & Shortlisting subsystem**—the most painful bottleneck in the staffing lifecycle.

Instead of:
- Writing filtering logic directly in PHP loops  
- Hardcoding conditions inside controllers  
- Letting every feature rewrite the same rules  

We built a **database-driven screening engine**.

## Technical Approach (Why This Was Different)

### 1. Business Logic Where It Belongs

Rather than pushing everything into PHP:

- Core screening logic was handled in **MS SQL Server**
- Used **JSON-based stored procedures** to:
  - Accept flexible candidate and job requirement payloads
  - Apply scoring, filtering, and shortlisting rules consistently
  - Return deterministic, structured outputs

PHP became a **thin orchestration layer**, not the brain of the system.

### 2. Structured Data Over Vibes

Typical PHP apps rely on loosely structured tables and ad-hoc joins.  
We instead focused on:

- Skill normalization
- Experience weighting
- Rule-based shortlisting instead of “if-else soup”
- Predictable outputs that could scale to ATS-level complexity

### 3. End-to-End Staffing Perspective

We didn’t treat this as a single feature.  
We designed it knowing how it fits into:

- Client acquisition
- Job posting
- Candidate intake
- Screening & shortlisting
- Interview tracking
- Payroll and placement

That context is what most student projects completely ignore.

## What This Hackathon Actually Taught Us

This wasn’t about learning a new framework. It taught us:

- Why **PHP-only logic breaks down** in complex domains
- How enterprise systems separate **business rules from application code**
- Why databases are not just storage—they’re enforcement layers
- How real staffing software is designed, not just demoed

Most importantly, it forced us to think like **engineers solving industry problems**, not students chasing features.

## Acknowledgement

Grateful to **Relay Hack**, **Aqore Nepal**, and **Techspire College** for setting a challenge that demanded depth, not surface-level execution. This experience raised the bar for how we think about backend architecture and real-world software systems.

---

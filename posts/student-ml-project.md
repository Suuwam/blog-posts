---
title: From Student ML Project to a Real Portfolio Piece
date: 2025-10-23
tags: [students, portfolio, ml projects]
excerpt: |
  Why do most student ML projects gather digital dust? Here's how to ship one that actually survives outside your repo.
---

## The Harsh Truth About Student ML Projects

Let me be real: I used to treat class ML projects like school essays. Write some code, maybe a Jupyter notebook, hit “submit,” and never look back. But then two things happened:  
1. I started mentoring juniors who wanted advice on getting hired.  
2. I sat on the other side of interviews, reviewing “portfolio” projects of students.

**And the pattern was brutal:**  
- The “cool” projects were ALL broken in some obvious way.  
- Reproducibility? Almost never.  
- README that made sense to a stranger? Rare.  
- The demo… usually only ran on the creator’s machine, with just the right versions and files.

### My Personal Wake-Up Call

I'll never forget trying to run a student's sentiment classifier. The README said "pip install -r requirements.txt" but somehow it pulled in torch 1.6 for Python 3.11, and nothing worked. The student was shocked ("but it worked last night!"). I was sympathetic-I’ve been there-so I gave feedback. Next round, the same errors.

At that point, I realized **I’d made all those same mistakes myself.**

### How To Actually Make a Portfolio Project That Survives

#### 1. **Do Less, Better**

Student (and hackathon) brains love *ambitious* ideas. But big ideas die on Windows-vs-Linux, CUDA, or "I haven't finished the front end yet." The best portfolio piece is a *small, finished, working* thing-bonus if you can demo it on a fresh laptop in 2 minutes.  

#### 2. **README for “Future Stranger-You”**

At the end of your project, imagine emailing your code to an older version of yourself who remembers nothing. Will you figure out how to run it in five minutes?  
If not: write better README.  
- Show **what problem it solves**
- Include **install/test steps**
- Show a **screenshot** (even a console example helps!)
- List **dataset/sample inputs/outputs**

#### 3. **Reproducibility ≫ Cleverness**

A basic model that can be cloned and run counts 10x more than a state-of-the-art experiment that needs your help to debug.  
Don't be the person whose project wins a poster prize and then "rots" after two months.

#### 4. **Tell the Real Story**

Skip the “just business” language. Instead, explain:
- What was confusing/fun/frustrating?
- What edge cases failed?
- What surprised you in the results?
- What would you do differently now?

When you write this as a narrative, you sound like someone who *actually learned*-and that's memorable.

#### 5. **The Interview Test**

When I look at a portfolio, I ask:  
*"Could this person help me debug in the real world, or did they just follow instructions?"*  
If your project tells that story, you stand out.

---

**TL;DR:** Don’t just aim for “working.” Aim for “reproducible by a sleep-deprived stranger.” That’s the project someone will remember you by.

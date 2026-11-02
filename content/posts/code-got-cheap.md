---
title: "Code Got Cheap. What's Scarce Now?"
date: 2026-11-02
draft: true
tags: ["agentic-ai", "engineering-management", "reliability"]
summary: "Agents made writing code cheap. They didn't make it cheap to know what the code should do, to check that it does, or to run it safely. Those are the new bottlenecks."
---

For most of software's history, writing code was the slow part. We built our processes,
estimates, and career ladders around that fact. Agents changed it in about two years.

Writing code got cheap. Three things did not:

1. **Knowing what the code should do.**
2. **Checking that it does.**
3. **Running it safely in production.**

Those are now the bottlenecks. A team that keeps its old habits but types faster will produce
more code and more bugs. The useful question for an engineering leader is no longer "how do we
write code faster?" but "what became scarce, and how do we reorganise around it?"

## What moved

| Used to be scarce | Now scarce |
|---|---|
| Typing the code | Saying precisely what must hold |
| Knowing the API | Judging whether a diff is correct |
| Writing tests by hand | Tests strong enough to catch a confident, wrong agent |
| Individual output | A trusted record of what was checked |

The left column is what agents are good at. The right column is where human judgement and
good tooling now earn their keep.

## A confident, wrong contributor

The hardest part of working with agents isn't that they make mistakes. People make mistakes too.
It's that agent mistakes look exactly like agent successes: fluent, well-formatted, plausibly
commented, often with passing tests the agent wrote itself.

That changes what review is for. Reviewing used to mean checking a colleague's reasoning, and
you could lean on their track record. With agents, a fluent diff tells you nothing about
whether it's correct. You need checks that don't depend on how convincing the change looks.

## Principles I'm working from

These are the principles I'm using with my team. Later posts go deeper on each.

- **Humans own intent.** Agents can draft specs and invariants, but a named person owns them.
- **Agents are untrusted contributors.** Capable and fast, but they work with bounded permissions
  and are judged by checks they can't influence.
- **Nobody grades their own work.** Whoever writes a change, human or agent, doesn't also change
  the tests or spec that judge it in the same change.
- **Rigor scales with risk.** A change to durability logic gets a formal model; a logging change
  gets a sentence. Spending rigor everywhere burns the goodwill you need where it matters.
- **Evidence, not confidence.** A change is done when it carries what it was checked against and
  the results.
- **Every failure becomes a check.** A bug found in review or production becomes a lint rule,
  an assertion, a property test, or a spec clarification, so it can't come back silently.

## What this means day to day

For engineers, more of the day goes to specifying, reviewing, and verifying, and less to typing.
That isn't a demotion. Stating invariants precisely and spotting a subtly wrong diff are harder
skills than writing a for-loop, and they're the ones that now matter.

For managers, the job is to protect time for that work. It doesn't look like output on a
dashboard, but it's what keeps faster code from turning into faster incidents.

## What's next

In this series I'll get concrete, using public tools and techniques:

- treating agents as untrusted contributors (sandboxing, least privilege)
- turning bugs into structural lint rules with **ast-grep**
- **property-based** and **differential testing** as checks agents can't game
- small **executable models in Lean**, and when proofs are worth the cost

If your team is going through the same shift, I'd like to hear what's working for you.

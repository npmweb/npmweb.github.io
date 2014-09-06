---
title: How to Apply the "No Broken Windows" Principle
layout: post
author: josh

---

Recently the head of our organization gave a presentation about the "keystone habits" principle. The idea is that certain habits, if you do them, affect many areas of your life, not just the habit itself. The example he gave was picking up trash: if you decide to pick up trash at your workplace, you'll feel more of a sense of ownership. That sense of ownership will affect how you view many problems at the workplace: instead of seeing yourself as disempowered and complaining, you'll see yourself as invested, and you'll want to find a way to make a difference.

Surprisingly, I had just read about a similar principle in [*The Pragmatic Programmer*](https://www.pragprog.com/book/tpp/the-pragmatic-programmer) called "No Broken Windows." The metaphor comes from urban buildings: why do some deteriorate and others stay in good condition? Researchers discovered that the "keystone habit" was fixing broken windows. If a broken windows was left unrepaired, residents got the sense that the building didn't matter, and things kept getting worse. But if the window was fixed right away, things didn't deteriorate.

*The Pragmatic Programmer* applies this principle to code. When you find a bug, if you don't fix it, over time you and your team get a sense that the code isn't in good shape, and you're less and less inclined to try to fix things. So the proposed application is, when you find a bug, fix it.

My first inclination was "that is a great idea and I have no idea how I'd be able to take the time to do that." So we discussed it at our team R&D meeting (an application of another Pragmatic principle, the brown bag lunch, from [*Practices of an Agile Developer*](https://www.pragprog.com/book/pad/practices-of-an-agile-developer)). The team had some great insights; here are some of the ones that stuck with me.

- On our team, we have good support from management and clients to fix broken windows during projects, but it's harder to find the time while working support tickets.
- "Broken windows" can refer to code errors, poor architecture, or incorrect business rules, but it's only about what's obviously-wrong. If something isn't done the way you would have done it, there might be a reason why it was done that way, and you should take the time to find out.
- Different developers notice different kinds of broken window, depending on their wiring: usability, design, code standards, architecture. That's a good thing. Fix the broken windows *you* see.
- Over time looking for broken windows, you'll get a sense of which fixes have the biggest impact and are worth taking the time on. But you won't learn that if you don't focus on fixing broken windows.

And the biggest principle, from my teammate Amy:

- **Try to do one extra thing.** Don't ignore all broken windows, but don't do huge refactoring either. When you're adding a feature or doing a support ticket, try to find one extra thing you can do.

How about you&mdash;what ways have you found to fix broken windows as part of your workflow? Let us know on Twitter at [@npmweb](https://twitter.com/npmweb)!
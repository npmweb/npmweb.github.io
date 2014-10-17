---
title: Managing a Many-Webapp Ecosystem
layout: post
author: josh

---

The way we do webapps is a bit different than most places I've heard of.

When it comes to how many and what kinds of webapps a business runs, I've heard of a few different setups:

- **Your business *is* the web,** so you've custom-built one or more large webapps.
- **The webapps are a core channel for your business,** so you run a few large ones, either off-the-shelf or custom-built.
- **You're a dev shop,** so you've built or set up many webapps, but don't have day-to-day responsibility for them.

Our needs are a bit different: our organization has many smaller organizations within it, each with their own brand, and multiple online needs. With so many needs, we designed an architecture of many webapps, most of them very small, each targeted to meet a specific need. It's worked fairly well for us so far, but because it's such an uncommon architecture we've had to learn a lot of lessons on our own. Here's what we've found so far.

Frameworks
==========

- **You always need a framework, especially when you don't.** Chances are there's something you're doing that a framework would do for you.
- **Choose frameworks that scale well:** frameworks that are easy to use for very small systems, yet are robust enough to handle larger systems. [Laravel](http://laravel.com) is a great example in the PHP space.
- **Multiple frameworks are okay if you have a reason for each.** For example, we use ExpressionEngine for our large CMS sites for robustness, WordPress for our small CMS sites for the UI, and Laravel for general webapp development.
- **Make sure you have in-house knowledge of the frameworks.** The first webapps we had developed were by a vendor using a framework our team never got familiar with. This led to a long turnaround time for bug fixes, and an eventual rewrite.
- **When evaluating frameworks, keep industry trends in mind.** If the features are comparable, go with the one that is the standard or gaining popularity. It will make it much easier to outsource work, find open-source plugins, reuse past code, etc.
- **Choose your tools with the skill set (both present and future) of your team in mind.** What languages does your team already know? What dev tools are they already comfortable with?
- **It's more important to pick a platform and learn it than it is to pick the "right" platform.** You can end up in decision limbo indefinitely, and new tools are always coming along. There are [no silver bullets](http://faculty.salisbury.edu/~xswang/Research/Papers/SERelated/no-silver-bullet.pdf). That said, you need to...
- **Have a proactive strategy for re-evaluating.** You can't realistically look at and switch to every new thing that comes along, but you also don't want to look up and be using antiquated software. Decide what *would* be [a good reason to start looking](http://ellislab.com/blog/entry/ellislab-seeking-new-owner-for-codeigniter).
- **Use SaaS platforms that have good APIs.** It's a huge time-savings to use Saas, but you'll probably need that data somewhere else, so you'll want to have good APIs to work with it.

Architecture
============

- **Minimize dependencies between systems.** We've created a single middleware web service that sits between our webapps and all of our backend systems, like login, payment, and form processing.
- **Don't overdesign. Your architecture should be as complex as your requirements: no more, no less.** If your webapp only needs to create, read, update, and delete data, then ["CRUD"](http://en.wikipedia.org/wiki/CRUD) isn't a bad architecture.
- **Standardize for the ecosystem, not for one project.** Don't pick a tool for Laravel if there's one that will also work for WordPress and ExpressionEngine.
- **Respect the POPO (Plain Ol' PHP Objects).** There's [a movement](http://philsturgeon.co.uk/blog/2014/01/the-tribal-framework-mindset) in the PHP world right now to build code that's framework-agnostic. Then just add in optional framework-specific hooks.


Project Management
==================

- **Treat different types of project differently.** We can bang out WordPress blogs without a second thought. But large webapps and multiple-site-impacting campaigns require more scheduling and testing.
- **Find solutions that work across different types of project.** If you know a process or tool will only work for one project type, maybe there's a better option out there.
- **Come up with guidelines for when to say "yes" to systems.** You need to default to saying "no", and only say "yes" for the right system. Our guidelines for large webapps are that it should not be available off-the-shelf, overlap with another system, be limited to one department, or be based on an experimental organizational process.

Maintenance
============
- **Consider team cognitive load.** Not every developer is a nerd like me, wanting to spend free time reading about code. If they don't know OO, SASS, package managers, and build tools, then you don't want to introduce them all at once.
- **Considered the "care and feeding" capacity of your team.** If you don't plan time for maintenance, you'll build more systems than you can support. Think about the hours your staff have available, the budget for enhancements, and server costs.
- **And find tools to help you update your systems.** The testing portion of the update will need to be done by hand regardless, so why not [use a tool](https://managewp.com/) to do the updates themselves? Also, pick an update schedule and stick to it.
- **Use an automated deployment tool.** If you aren't familiar with the whole range of types of automated deployment tools out there, [learn about 'em](http://css-tricks.com/deployment/). We use [dploy.io](http://dploy.io) by Beanstalk because of the extensive logging in the web interface. But whichever automated deployment tool you pick, pick *something*, and you'll [feel like this](http://devpractic.es/post/89425969374/first-time-doing-an-automated-deployment).
- **Use "rap sheets" to keep track of your systems' details.** Have a single document for each webapp in an easy-to-find place (Google Drive, a wiki, GitHub readmes) that tells you where it is in version control, who built it, technologies, dependencies, common support requests, etc.


Potpourri
=========

- **Come up with a standard look and feel.** Just because you have a lot of webapps, your users don't need to know that. If they do, they'll get confused. Come up with consistent branding, even reusable template markup.
- **Come up with a domain strategy.** We've been consolidating ours down to a few central domains, based around a strategy. And with some simple Apache config we can run different apps at different paths under the domain.

So Yeah
=======

So is there anyone else out there managing a many-webapp ecosystem, or is it just us? Even if you don't have as many as us, are you doing any of the above? Let us know on Twitter at [@npmweb](https://twitter.com/npmweb), and let us know what's helped you manage your webapps!
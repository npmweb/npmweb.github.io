---
title: How We Laravel
layout: post
author: josh

---

A friend of a friend just asked me for Laravel resources, and I sent him to the [regular](https://laracasts.com/) [places](http://culttt.com/). But then I realized that that wasn't enough. The Laravel philosophy is to figure out what works for you and do it. There are a bunch of little things about how we do Laravel that I wanted to share with him as well. And I figured it's the kind of thing I could post about so we as the community could talk about it.

In fact, I'd love to hear how you Laravel too! If you like this post, write one yourself and tweet it with [#HowILaravel](https://twitter.com/search?f=realtime&q=%23HowILaravel&src=typd). Let's get a discussion going!

Disclaimer: we have three Laravel apps under development but haven't released any of them to production yet, so this is all still in progress. Let me know if you have recommendations for other things we could try. Also, instead of building a few large apps, we build and maintain dozens of small apps, so our needs are different than some developers (I'll be blogging about those differences soon). Finally, don't use any of these just because I recommended it: look into it and decide if it works for you.

Built-in Stuff We Use
---------------------
These are all built-in Laravel features so you've probably heard about them. But in case you haven't, we love them and think you should check them out!

- [Migrations](http://laravel.com/docs/migrations) for setting up the database. Makes it so often to move database changes between environments and branches.
- [Seeding](http://laravel.com/docs/migrations#database-seeding) for setting up test data. Think through exception cases once and stick them in here; that way, it'll always be there to blow your code up as you try it!
- [Composer](https://getcomposer.org/) for downloading dependencies.
- [Require.js](http://www.requirejs.org/) for including JavaScript dependencies into a page. Require.js is actually automatically set up for us when we [install frontend components via Composer](https://github.com/RobLoach/component-installer). I'm sure we'll switch to NPM or Bower for frontend components eventually, but for now it's enough for our team to learn [one package manager](http://devpractic.es/post/87364152723/to-install-a-package-manager-you-have-to-install-a).
- [Resource controllers](http://laravel.com/docs/controllers#resource-controllers) for almost all of our controllers. I love the RESTful convention: it makes it easy for us to design our URL strategy, and makes it easy to add web service support. We break this convention when we need to for usability, but it's a good default starting point.

Stuff We've Changed
-------------------
Changes to the default Laravel project template or conventions.

- Instead of using the /controllers/ or /models/ directories, we replaced them with a single /src/ directory. This allows us to keep controllers, models, and all other application code under our namespace strategy, such as NpmWeb\MyAppName\Controllers.
- Instead of using the [built-in Blade escaping](http://laravel.com/docs/templates#other-blade-control-structures) to prevent cross-site scripting, we've taken it to the next level. OWASP [recommends](https://www.owasp.org/index.php/XSS_%28Cross_Site_Scripting%29_Prevention_Cheat_Sheet) some more robust cross-site scripting protection that takes into account differences between page body, tag attributes, URLs, JavaScript, etc. We've implemented it in a PHP library and a JS library, which I'd love to release, but frankly I'm terrified of getting sued if someone hacks it! Hopefully I can get some legal advice soon so we can get that released.

Libraries We're Using
---------------------
Composer packages we use by default for any new apps we create.

- [Ardent](https://github.com/laravelbook/ardent) instead of [Eloquent](http://laravel.com/docs/eloquent) for models. Ardent extends Eloquent and adds support for configuring validation rules directly inside the model and automatically running it on save--Rails-style, baby! Before the enterprisey folks jump down my throat, yes, this is not a great idea for super-big apps. But for our small apps, this is working best for us as a starting point.
- A [custom FormBuilder subclass](https://github.com/npmweb/laravel-forms) set up to output the forms in a way that works with our CSS framework, [Foundation 5](http://foundation.zurb.com/). This pattern has worked really well for us: instead of having to recreate that markup in every page and app, we put it into the form library itself.
- A [reference library](https://github.com/npmweb/reference) for accessing common dropdown data like genders, month names, and US state names.
- [Client Validation Generator](https://github.com/npmweb/client-validation-generator), which automatically generates validation code in your favorite client-side validation framework, based on your server-side validation rules. It's a generic PHP library that could be used with any server-side and client-side framework, but so far I've set it up for Laravel and [jQuery Validation](http://jqueryvalidation.org/documentation/).

So Yeah
-------

How about you? How do you Laravel? Tweet it with [#HowILaravel](https://twitter.com/search?f=realtime&q=%23HowILaravel&src=typd) and let's get the discussion going!
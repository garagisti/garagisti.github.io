---
layout: post
title: "There's something about Rails..."
date: 2016-01-14 20:38:03 +1100
author: Rahul Bose
---

I read an old blog [post][bottled-up-backbone-love-letter] from a friend I look up to for anything programming/computer related.

The blog post is excellent. A lot of depth and opinion about topics I don't fully appreciate (yet).

But, while the blog post was  there are a couple of lines that stand out for me:

> Rails is unabashedly an opinionated framework.
> Many of us Rails developers do what we do because (for the most part) we approve of those opinions.

I stopped at this point and reflected. I've never thought of any programming framework's 'opionnated-ness'. I've just accepted the programming gods knew they were doing. And I programmed to get things to 'work' accordingly.

So anyway, while I'm not a professional Rails developer (yet), this point got me thinking. I thought, do I also approve of Rails' opinions? Perhaps not all its opinions, but probably it's main ones.

So let me go back to the reasons why I chose Rails to develop in.

1. It's fast.

   ...well sort of. Firstly to anybody new to rails a preliminary [point](#point1).

   When I say Rails is fast, its fast in a practical, web-development sense. It lets good web developers get something up and running, (or modified) quickly. And the kicker is, most programmers have fun while doing it. I mean, who doesn't like the odd `$ rails generate scaffold` ?

   I'm sure there will be a labcoat that points me to benchmarks and tell me technically Ruby is not [fast][is-ruby-fast].

   Besides the technical reasons  flexApart from the technical capability of around 'scaffolding' and generating the relevant model details quickly etc, let's take a real world example. There was an article I read in the paper a while ago about the Mistakes a tech entreprenuer has learnt from. I can't find the link, but in summary:

  * The strategy of this Tech company is to get customers (who are business owners) to sign up to an app at no cost (the cost passed on to the user of the app).
  * Relevant teams of the Tech company work towards building a business plan (sales teams get 'buy in' from business owners, tech teams build the app accordingly).
  * The Tech company Leadership team decides that there's higher potential sign ups if the business owners pay to be included in the app (instead of the user at time of use).
  * The Tech company Leadership team directs the sales team to go back to the business owners, cap in hand and ask them to pay. The Leadership team Directs the tech team to make the relevant updates to the app.
  * Over half the sales team quits (which turned out to a high percentage of the Tech company).
  * The tech team were able to make the changes almost immediately...

   Now, while this is probably an example of poor sales strategy (and somebody will probably give me examples where half the tech team quit), but I'm looking at a real world example of how technology can 'enable' higher potential & value.

   The real point I'm trying to make here is that half (or all) the tech team could also have quit... was there something in the framework that make flexibility of the app possible? I choose to believe so.

2. It's Open / Free

   With all the hubub behind open sourcing the codebase, some people were ahead of the game (although past performance is not an indicator of future performance of any tech framework...)

3. Keeping things DRY

   For the newbies, read up on [DRY][dry-link]. To me this is something I was doing in the J2EE days (so it's not a new concept), but Rails takes it to a whole new level.

   [[expand on this]]

4. Everything in Ruby is an object.
5. “Skinny controllers and fat models…”
6. CRUD (Create, Retrieve, Update, Delete)
7. RESTful API - REST is the best pattern for web applications – organizing your application around resources and standard HTTP verbs is the fastest way to go.
8. Convention Over Configuration – means that Rails makes assumptions about what you want to do and how you’re going to do it, rather than requiring you to specify every little thing through endless configuration files.

Footnotes:
<a id="point1"></a>
  * [Rails][rails-link] is a web application framework. [Ruby][ruby-link] is a programming language. Rails was written in Ruby. When I refer to Rails, I include Ruby (but not vice-versa).

[bottled-up-backbone-love-letter]: http://bottledup.net/2013/05/16/dear-backbone-love-letters-from-a-rails-dev/
[rails-link]: http://guides.rubyonrails.org/getting_started.html
[ruby-link]: https://en.wikipedia.org/wiki/Ruby_(programming_language)
[dry-link]: https://en.wikipedia.org/wiki/Don%27t_repeat_yourself
[is-ruby-fast]: http://www.isrubyfastyet.com
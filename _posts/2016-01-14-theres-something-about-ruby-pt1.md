---
layout: post
title: "There's something about Rails...[Part 1]"
date: 2016-01-14 20:38:03 +1100
author: Rahul Bose
---

This is a 2 part series of posts that outlines the reasons I like Rails.

I read an old blog [post][bottled-up-backbone-love-letter] from a friend I look up to for anything programming/computer related.

The blog post is excellent. A lot of depth and opinion about topics I don't fully appreciate (yet).

However, there are a couple of lines that stand out for me:

> Rails is unabashedly an opinionated framework.
> Many of us Rails developers do what we do because (for the most part) we approve of those opinions.

I stopped at this point and reflected. I've never thought of any programming framework's 'opinionated-ness'. I've just accepted the programming gods knew they were doing. And I programmed to get things to 'work' accordingly.

So anyway, while I'm not a professional Rails developer (yet), this point got me thinking. I thought, do I also approve of Rails' opinions? Perhaps not all its opinions, but probably it's main ones.

So let me go back to the reasons why I chose Rails to develop in.

It's fast
======

   ...well sort of. Firstly to anybody new to rails, a [footnote](#footnote).

   When I say Rails is fast, its fast in a practical, web-development sense. It lets good web developers get something up and running (or modified) quickly. And the kicker is, most programmers have fun while doing it. I mean, who doesn't like the odd `$ rails generate scaffold` ?

   I'm sure there's a lab coat out there who will point me to benchmarks and tell me technically Ruby is not [fast][is-ruby-fast]. I'd also follow up to say that it's not a good idea to learn rails when you're under the time pressure to build a new project - it has a nice learning curve, but it does get complex when you're trying to do complex things.

   Besides the technical reasons, I look to real world scenarios. Often (always?) there's a need to be adaptable and quick in a start up environment. I read about the what happened to [Yumtable][Yumtable-link] and think, my experience has showed me that large companies make similar mistakes.

   Now, while the Yumtable experience is probably an example of poor sales strategy (and somebody will probably give me similar examples where half the tech team has quit), I'm looking at a real world example of how technology was adaptable, a real enabler.

   The point I'm trying to make is that I think it's important to be fast in the way Rails is fast. The rails framework, the ruby language, and when used well (i.e. adhering to the the discipline of their idioms), translate to a flexible and fast framework for the real world.

It's Open / Free
======

   It's probably a moot point in 2016 that Open Source frameworks are probably the tool(s) of choice when starting a new tech-venture. Apart from obvious realities of your environment and constraints (capital, skills shortages, talent availability etc.) playing a part in making decisions on your choice of software stack.

   What's cool about Rails is the community. So much so, I feel like the slogan made [ubiquitous][apple-trademark-link] by Apple can be re-applied by Rails ("There's probably a Gem for that")... And this is because there's a vibrant community (particularly in Australia) that help support and develop it.

   Having said this, judging by the plethora of Open Source Frameworks there's no direct correlation between an open framework and it's popularity (or even critical mass)...

DRY humor
======

   For the newbies, read up on [DRY][dry-link]. To me this is something I was doing in the J2EE days (so it's not a new concept). For me, this was about cleaning up the business logic and refactoring. But Rails takes it to a whole new level.

   In short DRY means Don't-Repeat-Yourself. Typically there are a parameters in an application that are used throughout the application. The DRY principle states that a modification of any single parameter of a system does not require a change in other logically unrelated elements. So in other words, write and configure your code so that you can make far reaching changes from one place.

   The cool thing is Ruby is that you can apply the DRY principles throughout the MVC architecture.

   * Views - The use of partials.
   * Controllers - Heaps of things. Ruby making things easier than the ol' Java Getter and Setter [logic][ruby-auto-get-set] with `attr_accessor:` And I liked the use of filters (also works in Models).
   * Models - Named Scope that let's you do some some.cool.linking.

     Yes I agree with all of this!

Objects, they're everywhere
======

   Absolute awesomeness. I used to love Java because it was more truly object oriented than C back in the day. I liked the purity of it.

   Also cool little things that you take for granted like built-in Ruby Duck typing methods such as `to_s` `to_i` and `to_a`.

   In Ruby... I can dot anything! Love!

"Fat Models and Skinny controllers...”
======

   Isn't that a memorable idiom. Not that you should have "Fat" models - because this could become an anti-pattern too. But it gives a guidance to new developers in that if you're going to put juicy business logic somewhere, don't do it in the controller.

   I'll stand on the shoulders of giants to explain this one.

   Take for example this in your Controller:

{% highlight ruby %}

def index
  @published_posts = Post.all :conditions => {['published_at <= ?', Time.now]}
  @unpublished_posts = Post.all :conditions => {['published_at IS NULL OR published_at > ?', Time.now]}
end

{% endhighlight %}

   This can be simplified in two steps.

   **Step 1:**

   Move the condition (business) logic to your Model and add new methods `all_published` and `all_unpublished`

{% highlight ruby %}

def self.all_published
    all :conditions => {['published_at <= ?', Time.now]}
end

def self.all_unpublished
  all :conditions => {['published_at IS NULL OR published_at > ?', Time.now]}
end

{% endhighlight %}

   **Step 2:**

   Simplify your Controller.

{% highlight ruby %}

  def index
    @published_posts = Post.all_published
    @unpublished_posts = Post.all_unpublished
end

{% endhighlight %}

   Thanks to Darcy [Laycock][darcy-laycock-twitter] for this simple example.

   Note how the controller logic is simpler (and easier to test) and we're singing from the same Rails hymnbook (ie we automatically DRY up the code).


There's a few more reasons I like Rails, but that's enough for this post. I'll follow this post up with a Part 2 that outlines my final few reasons.

Cheers, <br>
Garagisti

---

Footnote: <br>
<a id="footnote"></a>

   * [Rails][rails-link] is a web application framework. [Ruby][ruby-link] is a programming language. Rails was written in Ruby. When I refer to Rails, I include Ruby (but not vice-versa).

[bottled-up-backbone-love-letter]: http://bottledup.net/2013/05/16/dear-backbone-love-letters-from-a-rails-dev/
[rails-link]: http://guides.rubyonrails.org/getting_started.html
[ruby-link]: https://en.wikipedia.org/wiki/Ruby_(programming_language)
[dry-link]: https://en.wikipedia.org/wiki/Don%27t_repeat_yourself
[is-ruby-fast]: http://www.isrubyfastyet.com
[Yumtable-link]: http://www.smh.com.au/business/startup-war-stories-how-yumtable-almost-died-from-charging-the-wrong-customers-20150524-gh8qmy.htmlw
[apple-trademark-link]: http://www.trademarkia.com/theres-an-app-for-that-77980556.html
[ruby-auto-get-set]: https://coderwall.com/p/wfyjaw/ruby-automatic-get-and-set-methods
[darcy-laycock-twitter]: https://twitter.com/Sutto

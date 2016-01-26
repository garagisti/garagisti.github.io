---
layout: post
title: "There's something about Rails...[Part 2]"
date: 2016-01-14 20:38:03 +1100
author: Rahul Bose
---

So this post follows on from my earlier post outlining the reasons I like Rails.


6. CRUD (Create, Retrieve, Update, Delete)

   To me this is another one of those things I was doing in the J2EE days.

   It's obvious - fundamentally, there shouldn't be a myriad of ways you should need to touch your database in operation.

   * You put stuff in (Create),
   * You read values to use (Retrieve),
   * You change a value (Update), and;
   * You get rid of stuff (Delete).

    You could potentially simplify it further by combining the Create & Update - but this may slow things down...so it depends on how you're using the database.

   In short - I subscribe to this.

7. RESTful

So when I started Rails I didn't know enough detail about a RESTful API. Having previously worked in a J2EE environment with SOA based data exchange (web-services). I had not much experience in other (non-XML) protocols. Strangely enough, I came to realise I been using a RESTful architecture (HTTP) for ages.

REST stands for Representational State Transfer - which seems so contextual to me that I feel it means something to a few and nothing to many.

So let's think in the context of the Web, Client Server communication, Web Services (SOAP, WSDLs), caching of responses etc.

REST is a systems architectural style. It's not an implementation or protocol in the way HTTP is a protocol. I did some digging around and found an abstracted & contextualised view of REST.


![Pic of REST](/assets/post-images/REST1.gif "REST"){: .center-image}

So this image


REST is stateless, like all good engineering solutions!

First thing to get an understanding of is that HTTP is about applying verbs to nouns. Huh? are we in context or out of context again?

API - REST is the best pattern for web applications – organizing your application around resources and standard HTTP verbs is the fastest way to go.



8. Convention Over Configuration – means that Rails makes assumptions about what you want to do and how you're going to do it, rather than requiring you to specify every little thing through endless configuration files.



But after all is said and done. Why did I did I chose Rails to develop in? Over and above anything I've said, I owe it to myself.

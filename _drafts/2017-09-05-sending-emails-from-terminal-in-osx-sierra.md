---
layout: post
title: "Sending Emails from Terminal in OSX sierra"
date: 2017-09-05 22:00:03 +1100
author: Rahul Bose
comments: true
---

It's been a long time between drinks. A lot has happened in my personal life I suppose.

Anyway, the new outlook is to get things back on track and start blogging about the things I want to focus on.

So let's begin. Again.

This blog is an outline about how to send emails using terminal. There's obviously more you would want to do than simply sending emails, such as scheduling emails, and adding useful content to these emails. Such as, The F1 practice session is on tonight, and here's some detail about who won last year, the fastest times etc. etc.

For now, let's just focus on sending emails.

Basically, we will be using a postfix, which is the service used by mail, to send an email via a pre-established gmail account (although it could easily be your ISP) to act as the sever to send emails. You may need root access to create / edit files under postfix.


**Step 1:**
Edit the main.cf file under /etc/postfix
'$ cd /etc/postfix'

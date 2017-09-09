---
layout: post
title: "Sending Emails from Terminal in OSX Sierra"
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

{% highlight shell %}
$ cd /etc/postfix
{% endhighlight %}

Open the main.cf file. You will need to be admin.

{% highlight shell %}
$ sudo vi main.cf
{% endhighlight %}

Edit the file by adding the following lines to the bottom of the file.

{% highlight shell %}
# Navigate to bottom of the file
# ...
relayhost = [smtp.gmail.com]:587 # Note this is specific to gmail smtp.

# SASL SUPPORT FOR SERVERS
#
# The following options set parameters needed by Postfix to enable
# Cyrus-SASL support for authentication of mail servers.
# ie Use sasl when authenticating to foreign SMTP servers

smtp_sasl_auth_enable = yes

#  use tls
smtp_use_tls = yes
smtp_tls_security_level = encrypt
smtp_enforce_tls = yes
smtp_sasl_tls_security_options =
smtp_sasl_tls_verified_security_options =
smtp_tls_loglevel = 2

# We will allow Postfix to use anonymous and plaintext authentication.
smtp_sasl_security_options =n oanonymous
smtp_sasl_mechanism_filter = plain

# path to password map file
smtp_sasl_password_maps = hash:/etc/postfix/smtp_sasl_passwords
smtp_tls_per_site = hash:/etc/postfix/smtp_tls_sites
{% endhighlight %}

**Step 2:**
Create a SMTP SASL Password File and be sure to add a security level to it.

{% highlight shell %}
$ touch /etc/postfix/smtp_sasl_passwords
$ chown root:root /etc/postfix/smtp_sasl_passwords
$ chmod 600 /etc/postfix/smtp_sasl_passwords
{% endhighlight %}

Edit the newly created file  `smtp_sasl_passwords`

{% highlight shell %}
$ sudo vi smtp_sasl_passwords
{% endhighlight%}

Add the following line and replace `username` and `password` accordingly.

{% highlight shell %}
[smtp.gmail.com]:587 username@gmail.com:password
{% endhighlight%}


**Step 3:**
Start Postfix - this is usually not started in OSX by default, but if it is, then all you need to do is a reload.

Alternatively, reload postfix if it's already started.

{% highlight shell %}
$ sudo postfix start
postfix: Postfix is running with backwards-compatible default settings
postfix: See http://www.postfix.org/COMPATIBILITY_README.html for details
postfix: To disable backwards compatibility use "postconf compatibility_level=2" and "postfix reload"
/usr/sbin/postconf: warning: /etc/postfix/main.cf: unused parameter: mydomain_fallback=localhost
...
postfix/postfix-script: starting the Postfix mail system
{% endhighlight%}

Or if you had already started postfix prior to Step 1 & 2 then you will need to reload (or if you prefer you could also do a postfix stop and start.)
{% highlight shell %}
$ sudo postfix reload
postfix: Postfix is running with backwards-compatible default settings
postfix: See http://www.postfix.org/COMPATIBILITY_README.html for details
postfix: To disable backwards compatibility use "postconf compatibility_level=2" and "postfix reload"
/usr/sbin/postconf: warning: /etc/postfix/main.cf: unused parameter: mydomain_fallback=localhost
postfix/postfix-script: refreshing the Postfix mail system
{% endhighlight%}


**Step 4:**
If you're using gmail as your SMTP, then you will need to change your account to allow less secure apps to access your account.
Navigate to your gmail account settings and turn the setting on.

![Pic of gmail-less-secure-apps](/assets/post-images/gmail-less-secure-apps-setting.png "gmail-less-secure-app"){: .center-image}


**Step 5:**
Try a mail call.
{% highlight shell %}
$ echo "Hello" | mail -s "Test" you@domain.com
{% endhighlight %}



**Troubleshooting**
Use the `mailq` to see if the email is stuck in the queue to be sent.

Also You can use a -v option on the mail call if you want to see what happened.

{% highlight shell %}
$ echo "Hello" | mail -vs "Test" you@domain.com
{% endhighlight %}

If you're still stuck, Google is your friend :)


# yubo1factor
Yubo 1 Factor Authentication Vuln+Exploit

This is not designed as a tutorial or as a guide on how to exploit this app. This repository is solely designed for showing how easy it is to take over
and account on this social media platform and how YOU can protect yourself from this app.

TL;DR

-Don't use a Temp SMS number to sign in on this app.
-Don't click any malicious airdrops or install any malicious APK files.
-Encrypt or hide SMS messages in a different app or environment.
-Request a Dynamic IP from your provider, makes it harder to dump SMS.
-Don't be a moron and allow youself to be socially engineered.

The vulnerability in this app is that you can sign in as long as you provide the code sent to a phone number through registration; no password, no username,
no email address verification. This allows you to gain access to ANY account as long as you know the phone number attached to it.

Possible exploit routes: Reverse TCP application and a little bit of social engineering (or stealth attack), this is what I will be using. You can also use
other services to dump SMS like command injection on a shell, or the old fashioned way: steal their phone. You can send them an email with a hook that gives you access or sends you traffic that enters or leaves the phone - you get it, many different ways.

Check vuln+exp.md for the full walkthrough on this vulnerability.

---
layout: post
date: 2020-06-13 02:45
title:  "Cookies Intro"
mood: tired
category: 
- docs
---

Markdown (or Textile), Liquid, HTML & CSS go in. Static sites come out ready for deployment.

# Introduction

## Different type of cookies

**Session cookies**
Basically when you close the website, the cookies will be removed from your growers, so its risk is relatively low.

**Persistent cookies**
Even when you close your browser, the cookies will still be stored on it. And each time you return to the website that created this cookie, or you go to a website that has a resource produced by the cookie’s issuer (eg, an ad), this data is returned to the issuer.

	
**First-party cookies**


**Third-party cookies**

## The risk of cookies

**Cookies Fraud**

Here are four common types of cookie fraud and what they involve:

*Cross-Site Scripting (XSS)*
Here, a user will receive a cookie after they’ve visited a malicious website. This cookie contains a script payload that targets another website, but the malicious cookie is in disguise and looks as though it’s come from the website that’s being targeted. Therefore, when a user visits the targeted site, this fraudulent cookie (and its script payload) is sent to the targeted site’s server.

This type of vulnerability may be used by attackers to get past certain access controls like the same-origin policy.

*Session Fixation*
When this occurs, a user will be given a malicious cookie that contains the session ID of the cookie’s issuer. Then, when the innocent user goes to log into a domain that’s being targeted, the user’s session ID isn’t logged but the cookie issuer’s is. This makes it look as though the issuer is performing certain actions on the targeted domain but it’s the user that’s actually performing them.

This type of cookie fraud allows attackers to take over valid user sessions.

*Cross-Site Request Forgery Attack (CSRF)*
A legitimate cookie is received by a user when they visit a legitimate site. However, they then visit a malicious site which instructs the browser of the user to perform an action that targets the legitimate site they’ve previously visited. A request is received by the legitimate site alongside the legitimate cookie, and the same action is performed as it seems to have been triggered by the legitimate user, but it hasn’t, it’s been initiated by the malicious site.

*Cookie Tossing Attack*
In a cookie tossing attack, a user is provided with a cookie by a malicious site, which has been designed to look like it’s come from the targeted site’s subdomain. For example: http://subdomain.placeholder.com. Therefore, when the user goes to the targeted site (placeholder.com), all of the cookies are sent, including legitimate ones and the subdomain cookie. Where the cookie that’s interpreted first is the subdomain, this data will overrule any of the legitimate data contained in the other valid cookies.


---
layout: archive
title: "Projects"
permalink: /projects/
author_profile: true
php_video_id: yE0qTTi-_iQ
---


## Derandomization Attacks against Web Applications (2012)
Secure randomness generation is of fundamental importance in modern applications. From session identifiers, to CSRF tokens
and password reset tokens, the secure generation of random bytes lies in the heart of securing modern applications.

In order to evaluate the security offered by standard random number generators in Web applications, we studied  
the security of the built-in Pseudorandom Generators (PRGs) in the PHP runtime.
More specifically, we developed algorithms and techniques to mount practical
attacks against PRGs in web applications.  Our techniques
ranged from lattice based cryptanalysis algorithms, online solvers for large systems of linear
equations to timing attacks in order to reduce the entropy of time measurements.
Using our techniques, we crafted practical exploits which allowed us to predict
the password reset tokens used in order to reset a user's password in a number of
different PHP applications.  Our attacks allowed an attacker to takeover arbitrary
user accounts and affected a large number of applications including Joomla,
Wikimedia, eCommerce and others. According to a third party estimate around 10\%
of Internet applications were affected by our attacks.

For more information see the presentation from our Usenix Security 2012 paper: 
{% include youtubePlayer.html id= page.php_video_id %}

---
layout: archive
title: "Projects"
permalink: /projects/
author_profile: true
php_video_id: yE0qTTi-_iQ
lightbulb_video_id: f-1k0fNjkeY
---


## Learnability of Symbolic Automata and Transducers (2018)
Symbolic automata (s-FAs) and transducers (s-FTs) extend classical automata and transducers by allowing 
transitions to be taken over predicates instead of indvidual symbols.
During our work on using active learning algorithms for symbolic automata and transducers for testing
(see Active Learning for Security Testing below), a fundamental question came up: 
*For which type of predicates (i.e. Boolean algebras) are s-FAs efficiently learnable?* 

In this project, our goal is to study under which conditions, i.e. for which predicate and function families, 
symbolic automata and transducers are efficiently learnable. In our recent [paper](/files/cav18.pdf) published in CAV 2018,
we presented a novel learning algorithm for symbolic automata, MAT\*, which is a modular algorithm able to learn 
s-FAs over any learnable boolean algebra for which a learning algorithm is provided. Moreover, we provide a characterization
of the s-FAs which are efficiently learnable by MAT\* and conjecture that MAT* captures the class of all efficiently learnable s-FAs.
We are currently extending these results for the case of symbolic transducers. 

The implementation of MAT\* as well as all benchmarks from our paper are part of the [symbolic automata library](https://github.com/lorisdanto/symbolicautomata).


## Active Learning for Security Testing (2016-2017)



### LightBulb framework:

{% include youtubePlayer.html id= page.lightbulb_video_id %}



### HVLearn: 




## Breaking Location Privacy (2014)
In the past years we have seen an explosion in the number of 
Location Based Services(LBS) which work by utilizing the current location
of the user of the service. Many such applications, such as social networks and dating applications,
also tend to share location information about users with other users of the service. 
To avoid the obvious security and privacy risks of sharing a user's location, these applications
share an *approximate* location of the user. 


To evaluate the privacy guaranteed of various LBS we have developed a number of new
algorithms which exploit the imprecise information about the location of a user
which is provided by the LBS in order to infer the precise location of the user.
Our techniques range from combinatorial algorithms which iteratively improve the
inferred location of a user using binary search to statistical maximum likehood
estimation algorithms in order to cope with services which are utilizing randomness 
in order to hide the location of their users.
Using these algorithms, our team developed attacks
affecting a number of popular services such as Facebook, Tinder, Foursquare and
many others.
Finally, we provide information-theoretic lower bounds 
on the number of queries required by such attacks and provide a simple defense mechanism to
address such attacks which is currently adopted by Facebook.

For more information read the [full journal version of our paper](/files/tops2017.pdf), our [CCS 2015 paper](/files/ccs2015.pdf) and also check our [LBS auditing framework](https://github.com/nettrino/LBSProximityAuditor).

## Derandomization Attacks against Web Applications (2012)
Secure randomness generation is of fundamental importance in modern applications. From session identifiers, to CSRF 
and password reset tokens, the secure generation of random bytes lies in the heart of securing modern applications.

In order to evaluate the security offered by standard random number generators in Web applications, we studied  
the security of the built-in Pseudorandom Generators (PRGs) in the PHP runtime.
More specifically, we developed algorithms and techniques to mount practical
attacks against PRGs in web applications.  Our techniques
range from lattice based cryptanalysis algorithms, online solvers for large systems of linear
equations to timing attacks in order to reduce the entropy of time measurements.
Using our techniques, we crafted practical exploits which allowed us to predict
the password reset tokens used to reset a user's password in a number of
different PHP applications.  Our attacks allowed an attacker to takeover arbitrary
user accounts and affected a large number of applications including Joomla,
Wikimedia, eCommerce and others. According to a third party estimate, around 10%
of Internet applications were affected by our attacks.

For more information see the presentation from our [Usenix Security 2012 paper](/files/usenix12.pdf) and also check out our [online gaussian solving framework](https://github.com/GeorgeArgyros/mt_derand) and the [snowflake framework](https://github.com/GeorgeArgyros/snowflake) for bruteforcing PRG seeds. Finally, check our [secure random bytes implementation](https://github.com/GeorgeArgyros/Secure-random-bytes-in-PHP) for PHP applications.
{% include youtubePlayer.html id= page.php_video_id %}

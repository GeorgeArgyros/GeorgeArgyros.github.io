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
Many important security properties in modern applications come as a result of incorrect or non-standard parsing of 
various types of source code, protocols or file formats. For example, code injection attacks are a result of 
an incorrect parsing which results in confusing data with code. Other recent examples include .A term which we believe 

Our goal is this project was to develop a practical testing approach for detecting *parser logic* bugs.
Our approach works by first inferring a formal model of the parser in the form of an automaton and then, 
exploiting the nice properties of automata to verify  if the parser satisfies or violates certain security properties. 
One of the most appealing aspects of our approach is the capability to efficiently compare automata and find inputs 
which produce different results, effectively allowing us to compute *parser differentials*, a capability which 
allows us to effectively test many parsing logic bugs.

Based on the above idea we have developed two distinct systems for testing different security properties.

### LightBulb framework: Learning based testing of sanitizers and filters.
Code injection attacks ... 

In the course of two papers, we developed the Lightbulb framework which offers two distinct 
learning-based testing approaches. 
Firstly, we developed Grammar Oriented Filter Auditing (GOFA), an approach which allows the user to 
provide a Context Free Grammar of attack strings (eg., HTML strings leading to Javascript execution or 
SQL suffixes for SQL Injection attacks) and afterwards, we use the grammar to drive the learning 
algorithm and attempt to find attacks in the target filter or sanitizer. 
Our second approach, called SFADiff, instead of using a user provided grammar, 
uses another instance of a learning algorithm to infer the grammar from a language runtime, 
such as a Web browser or an SQL Database, thus taking into account the differences between each implementation
and providing greater testing accuracy. 
Using these approaches we found more than 15 vulnerabilities in many popular Web Application Firewalls. 


For more information check our [Oakland 2016 paper](/files/snp16.pdf) and our [CCS 2016](/files/ccs16.pdf) paper. The lightbulb framework is available in [Github](https://github.com/lightbulb-framework/lightbulb-framework).

The following [Blackhat Europe 2016](https://blackhat.com) talk gives an overview of the lightbulb framework.
{% include youtubePlayer.html id= page.lightbulb_video_id %}



### HVLearn: Learning-based testing of SSL/TLS hostname verification.
The hostname verification functionality is a fundamental functionality in the SSL/TLS protocol. The purpose of the hostname
verification functionality is to check that a domain name matches the hostname in the a certificate. The complexity of the 
procedure comes from the fact that instead of a single string matching routine, the SSL/TLS protocol gives the capability
to utilize wildcards in order to specify a range of domain names to match with the certificate. Incorrect implementation of
the these rules can result in severe security vulnerabilities such as man-in-the-middle attacks and others. 

To effectively test this parsing functionality, we developed HVLearn, a tool which uses automata learning algorithms to 
learn DFA models of the hostname verification implementation of different libraries and then uses either differential testing to find differences between implementation or can check whether the inferred parsers comply with regular expression
rules. Using HVLearn we found 8 unique violations of the RFC specification in several different SSL/TLS libraries.

For more information check our [Oakland 2017 paper](/files/snp17.pdf) and try out the [HVLearn tool](https://github.com/HVLearn/HVLearn).



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

## Derandomization Attacks Against Web Applications (2012)
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

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
*For which types of predicates (i.e. Boolean algebras) are s-FAs efficiently learnable?* 

In this project, our goal is to study under which conditions, i.e. for which predicate and function families, 
symbolic automata and transducers are efficiently learnable. In our recent [paper](/files/cav18.pdf) published in CAV 2018,
we presented a novel learning algorithm for symbolic automata called MAT\*, which is a modular algorithm able to learn 
s-FAs over any learnable boolean algebra for which a learning algorithm is provided. Moreover, we provide a characterization
of the s-FAs which are efficiently learnable by MAT\* and conjecture that MAT* precisely captures the class of efficiently learnable s-FAs.
We are currently extending our results for the case of symbolic transducers. 

The implementation of MAT\* as well as all benchmarks from our paper are part of the [symbolic automata library](https://github.com/lorisdanto/symbolicautomata).


## Active Learning for Security Testing (2016-2017)
Many security vulnerabilities in modern applications are  a result of incorrect or non-standard parsing of 
various protocols and file formats. For example, code injection attacks are a result of 
incorrect parsing which confuses data with code. Other recent examples include 
[URL parser differentials](https://www.blackhat.com/docs/us-17/thursday/us-17-Tsai-A-New-Era-Of-SSRF-Exploiting-URL-Parser-In-Trending-Programming-Languages.pdf) 
and [path normalization differentials](https://i.blackhat.com/us-18/Wed-August-8/us-18-Orange-Tsai-Breaking-Parser-Logic-Take-Your-Path-Normalization-Off-And-Pop-0days-Out-2.pdf) which resulted in critical vulnerabilities in popular services such as Uber and Amazon. This type of vulnerabilities are often referred to as *parsing logic* bugs.

Our goal is this project was to develop a practical testing approach for detecting *parsing logic* bugs.
Our approach works by first inferring a formal model of the parser in the form of an automaton and then, 
exploiting the nice properties of automata to verify that the parser satisfies certain security properties. 
One of the most appealing aspects of our approach is the capability to efficiently compare different parsers 
which are learned as automata models and find inputs under which the two parsers behave differently, thus
computing *parser differentials*, a capability which allows us to effectively test many parsing logic bugs.
Based on the above idea we have developed two systems for testing different security properties.

### LightBulb framework: Learning based testing of sanitizers and filters.
Code injection attacks are still raigning as one of the most important threats for Web applications
according to the recent Owasp top ten 2017. One of the most popular ways to defend against 
these attacks are sanitizers and filters. A very popular type of filter are Web Application Firewalls (WAFs)
which are enforced by the PCI-DSS standard as a necessary defense against code injection attacks. 

In the course of two papers, we developed the Lightbulb framework which offers two distinct 
learning-based testing approaches for filters and sanitizers. Our first contribution, is the first 
algorithm for learning Symbolic Automata (s-FAs) allowing us to scale automata learning algorithms into 
large alphabets such as UTF-16.
Next, we developed Grammar Oriented Filter Auditing (GOFA), an approach which allows the user to 
provide a Context Free Grammar of attack strings (eg., HTML strings leading to Javascript execution or 
SQL statements for testing SQL Injection attacks) and afterwards, we use the grammar to drive the learning 
algorithm and attempt to find attacks in the target filter or sanitizer. 
Furthermore, we developed a system called SFADiff which, instead of using a user provided grammar, 
uses another instance of a learning algorithm to infer the grammar from a language runtime, 
such as a Web browser or an SQL Database, thus taking into account the differences between each implementation
and providing greater testing accuracy. 
Using the lightbulb framework we have discovered more than 15 vulnerabilities in many popular Web Application Firewalls. 


For more information check our [Oakland 2016 paper](/files/snp16.pdf) which introduced GOFA and our [CCS 2016](/files/ccs16.pdf) paper introducing SFADiff. The lightbulb framework is available [here](https://github.com/lightbulb-framework/lightbulb-framework).
The following [Blackhat Europe 2016](https://blackhat.com) talk gives an overview of the lightbulb framework.
{% include youtubePlayer.html id= page.lightbulb_video_id %}



### HVLearn: Learning-based testing of SSL/TLS hostname verification.
Hostname verification is an important functionality in the SSL/TLS protocol. The purpose of hostname
verification is to verify that a domain name matches the hostname in a given certificate. The complexity of
correctly implementing hostname verification comes from the fact that, instead of having a single string matching routine, 
the SSL/TLS protocol gives the capability to utilize wildcards in order to specify a range of domain names to match.
Incorrect or inaccurate implementation of the these rules can result in severe security vulnerabilities 
such as man-in-the-middle attacks and others. 

To effectively test hostname verification implementations, we developed HVLearn, a tool which uses automata 
learning algorithms to learn DFA models of the hostname verification implementation of different libraries and 
then it can either user differential testing to find differences between implementation 
or check whether the inferred models comply with regular expression rules. 
Using HVLearn we discovered 8 unique violations of the RFC specification in several different SSL/TLS libraries.

For more information check our [Oakland 2017 paper](/files/snp17.pdf) and try out 
the [HVLearn tool](https://github.com/HVLearn/HVLearn).



## Breaking Location Privacy (2014)
In the past years we have seen an explosion in the number of available
Location Based Services(LBS). 
Many LBS, such as social networks and dating applications,
tend to share location information about users with other users of the service. 
To avoid the obvious security and privacy risks of sharing a user's location, these applications
share an *approximate* location of the user. 

To evaluate the privacy guarantees of various LBS we have developed a number of new
algorithmic attacks which exploit the imprecise information about the location of a user
which is provided by the LBS in order to infer the precise location of the user.
Our techniques range from combinatorial algorithms which iteratively improve the
inferred location of a user using binary search, to statistical maximum likehood
estimation algorithms in order to attack services which are utilizing randomness 
in order to hide the location of their users.
Using these algorithms, our team developed attacks
affecting a number of popular services such as Facebook, Tinder, Foursquare and
many others.
Finally, we developed information-theoretic lower bounds 
on the number of queries required by such attacks and developed a simple defense mechanism to
address such attacks which is currently adopted by Facebook.

For more information read the [full journal version of our paper](/files/tops2017.pdf), 
our [CCS 2015 paper](/files/ccs2015.pdf) and also check our 
[LBS auditing framework](https://github.com/nettrino/LBSProximityAuditor).


## Derandomization Attacks Against Web Applications (2012)
Secure randomness generation is of fundamental importance in modern applications. From session identifiers, to CSRF 
and password reset tokens, the secure generation of random bytes lies in the heart of securing modern applications.

In order to evaluate the security offered by pseudorandom generators (PRGs) in Web applications, we studied  
the security of the built-in PRGs in the PHP runtime.
More specifically, we developed algorithms and techniques to mount practical
attacks against PRGs in web applications.  Our techniques
range from lattice based cryptanalysis algorithms, online solvers for large systems of linear
equations to timing attacks in order to reduce the entropy of time measurements.
Using our techniques, we crafted practical exploits which allowed us to predict
the password reset tokens used to change a user's password in a number of
different PHP applications.  Our techniques allowed an attacker to takeover arbitrary
user accounts and affected a large number of applications including Joomla,
Wikimedia, eCommerce and others. According to a third party estimate, around 10%
of Internet applications were affected by our attacks.

For more information check our [Usenix Security 2012 paper](/files/usenix12.pdf). Also, check out our [online gaussian solving framework](https://github.com/GeorgeArgyros/mt_derand) for inverting the Mersennes Twister PRG and the [snowflake framework](https://github.com/GeorgeArgyros/snowflake) for bruteforcing PRG seeds. Finally, check our [secure random bytes implementation](https://github.com/GeorgeArgyros/Secure-random-bytes-in-PHP) for PHP applications.
Below you can find the talk given in Usenix security 2012.
{% include youtubePlayer.html id= page.php_video_id %}

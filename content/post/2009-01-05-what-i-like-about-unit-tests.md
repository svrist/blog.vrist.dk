---
title: What I like about Unit Tests
author: svrist
layout: post
date: 2009-01-05
url: /2009/01/05/what-i-like-about-unit-tests/
dsq_thread_id:
  - 68433642

---
They are included with the source code, committed to SC and build along with the code  pretty automatically these days!

Actually I dont really care if it&#8217;s unit tests, integration tests or any other kind of test, I just see unit tests every day as part of my work. The part I like is that it&#8217;s such an integrated part of the code.

When I do a code review, it&#8217;s not always possible to just load in the code as a project into my eclipse and run findbugs, pmd, checkstyle and eclemma.

In these cases I go straight to the included testcases to see what is being tested.  I always have the (maybe naive?) faith that by looking at the test I at least get a view of the &#8220;main&#8221; function of the code parts and that way I can start to dig through the code. This has helped me likewise  when trying to reuse some old code. The unit test showed me very easily how to initalize the functionality, what I need to supply, and what needed to be  present (the mocked out parts). 

So shame on you who don&#8217;t write unit tests! (or other kinds of directly included tests).
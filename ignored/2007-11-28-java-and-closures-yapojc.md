---
title: Java and closures – YAPOJC
author: svrist
layout: post
date: 2007-11-28
url: /2007/11/28/java-and-closures-yapojc/
dsq_thread_id:
  - 68433573

---
<p align="center">
  <strong>YetAnotherPostOnJavaClosures</strong>
</p>

So, I fell over some articles with both the words closure and java in them this week.

<a href="http://java.sys-con.com/read/465002.htm" title="Closures in compiled JavaFX code" target="_blank">It was this article about JavaFX closures. </a>

Since I&#8217;ve done some of my non-mandatory classes in my stud.scient. days (like the last 4years) it kinda woke my interest.

It seems like lots of things has happend in the Java world since I last had any real interest in it (somewhere around 1½ year ago).

  * Java 6 and 7.
  * <a href="http://www.javaworld.com/javaworld/jw-11-2007/jw-11-jsr223.html" title="Scripting on the jvm on JavaWorld" target="_blank">Scripting languages on the JVM</a>, like <a href="http://www.scala-lang.org/index.html" title="Scala language homepage" target="_blank">Scala</a> and <a href="http://groovy.codehaus.org/" title="Groovy language" target="_blank">Groovy</a>. Scala looks quite interesting in my opinion.
  * And all the stuff that I&#8217;ve been ignoring when coding small things in Java 1.4 SE and having fun with generics in Java 5 SE. 
      * Like for example J2EE, the bean concepts and Application servers and everything
      * <a href="http://www.springframework.org/" title="Spring framweork" target="_blank">Spring</a>
      * <a href="http://www.hibernate.org/" title="Hibernate website" target="_blank">Hibernate</a>
      * <a href="http://www.junit.org/" title="Junit website" target="_blank">JUnit</a>
      * <a href="http://en.wikipedia.org/wiki/Test-driven_development" title="Test Driven Development from Wikipedia" target="_blank">Test-driven-development</a>

Maybe &#8220;fell over some articles&#8221; is a bit inaccurate. I&#8217;ve actually been trying to catch up. My main focus has been on the things I needed in my day-to-day work. That included JUnit and Unit-testing, Spring and the Application Server Enterprisy way of doing things.

Luckily I already spent some time reading up on the concept of <a href="http://en.wikipedia.org/wiki/Service-oriented_architecture" title="SOA on wikipedia" target="_blank">SOA</a>.

There is a ton of material online about all these things. Currently(as in the past year) there&#8217;s alot of talk about feature request for Java 7. <a href="http://www.oreillynet.com/onjava/blog/2006/08/will_we_have_closures_in_java.html" title="Clsure talk from OnJava.com" target="_blank">Including closures</a>. I tried to do a &#8220;quick&#8221; catchup on the subject and decided to share my findings with the world:

As far as I gather there currently exist two proposals:

  * <a href="http://docs.google.com/View?docid=k73_1ggr36h" title="CICE proposal" target="_blank">CICE &#8211; Concise Instance Creation Expressions</a> by Josh Bloch, Doug Lea and <a href="http://crazybob.org/2006/10/java-closure-spectrum.html" title="Crazybob on closures" target="_blank">Bob Lee </a>
  * <a href="http://gafter.blogspot.com/2006/08/closures-for-java.html" title="The proposal on Gafters'blog" target="_blank">BGGA</a> &#8211; <a href="http://blogs.sun.com/gbracha/entry/achieving_closure" title="Gilad Bracha on closures" target="_blank">Gilad Bracha</a>, <a href="http://gafter.blogspot.com/2006/08/closures-for-java." title="Gafter with the proposal" target="_blank">Neal Gafter</a>, <a href="http://blogs.sun.com/jag/entry/the_black_hole_theory_of" title="Gosling on closure debate" target="_blank">James Gosling</a>, <a href="http://blogs.sun.com/ahe/entry/full_disclosure" title="Ahés blog on the subject" target="_blank">Peter von der Ahé</a>

and as in any other good war on the internet, it seems like we are at a point where religion is the turning point. The CICE people believes that the BGGA is <a href="http://www.infoq.com/interviews/joshua-bloch" title="Josh Bloch" target="_blank">&#8220;overly complex&#8221;, and will alienate users by &#8220;pushing the complexity of the language beyond the point where Joe Java can&#8217;t use the language anymore&#8221;</a>
  
Another interesting twist is the fact the Neal Gafter &#8211; who I see as the current &#8220;main-man&#8221; behind BGGA, is working at Google as well as Josh Bloch and <a href="http://rickyclarkson.blogspot.com/2007/04/is-josh-bloch-biggest-problem-for.html" title="Ricky Clarkson on the closure debate" target="_blank">Josh Blach is the JCP representative for Google as pointed out by Ricky Clarkson (and down played by Neal Gafter).</a>

So no real catfight there. But among the readers there&#8217;s a very Web2.0-ish involvement in the debate. Lots of evangelists on both sides. (I&#8217;m a BGGA&#8217;er myself! To me it seems like CICE is like sitting between two chairs). Among these debates and blogentries there&#8217;s lots of interesting reading (and hearing; podcasts).

Apart from the other links in this post I recommend:

  * <a href="http://gafter.blogspot.com/2007/03/closures-for-organizing-your-code.html" title="Gafter with examples" target="_blank">Gafter with closure examples</a>
  * <a href="http://gafter.blogspot.com/2007/11/closures-prototype-update-and-extension.html" title="Gafter with prototype" target="_blank">Gafter with prototype</a> for javac and a rewrite of fork/join code to use closures.
  * (Actually all of Gafters blog is very interesting if you like programming language issues)
  * <a href="http://www.javaposse.com" title="Javaposse podcast" target="_blank">JavaPosse podcast. (BGGA people as well)</a>
  * <a href="http://www.ibm.com/developerworks/java/library/j-jtp04247.html" title="IBM on the debate" target="_blank">IBM on the debate: Java theory and practice: The closures debate</a>

**UPDATE:** <a href="http://parleys.com/display/PARLEYS/Closures+for+Java" title="Gafter talk from JavaPolis" target="_blank">If you need the real thorough easy understandable walkthrough this is a very nice talk by Neal Gafter</a>

If you need even more reading try some of these googlesearches:

  * <a href="http://www.google.dk/search?hl=da&q=gafter+closures+-site%3Agafter.blogspot.com&btnG=S%C3%B8g&meta=" title="Google search on closures and gafter" target="_blank">Comments to Gafter and closures</a>
  * <a href="http://www.google.dk/search?hl=da&q=%22Josh+Bloch%22+closures&btnG=S%C3%B8g&meta=" title="Bloch and Closures" target="_blank">Josh Bloch and Closures</a>
  * <a href="http://www.google.dk/search?q=%22Gilad+Bracha%22+closures&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:da:official&client=firefox-a" title="Gilad Bracha closure" target="_blank">Gilad Bracha andClosure</a> (Actually i really like his blog all in all. Just the name and Im sold [&#8220;Computational Theology&#8221;][1]. Too bad it&#8217;s discontinued, but hey, <a href="http://gbracha.blogspot.com/" title="Gilad Bracha personal blog" target="_blank">he still writes a bit on Blogspot</a>)
  
     <a href="http://www.google.dk/search?q=%22Gilad+Bracha%22+closures&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:da:official&client=firefox-a" title="Gilad Bracha closure" target="_blank"></a>

 [1]: http://blogs.sun.com/gbracha/
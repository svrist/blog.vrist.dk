---
title: Logging vs. debugging
author: svrist
layout: post
date: 2009-01-18
url: /2009/01/18/logging-vs-debugging/
dsq_thread_id:
  - 68433647
categories:
  - English

---
It is probably no news that measurements in an experiment almost by definition affects the experiment. 

This is true also for IT systems, where logging is a very used way for observing running code.

From Jeff Atwoods Coding Horror blog about a problem during the beta of stackoverflow.com:

> We spent days troubleshooting these deadlocks by .. wait for it .. **adding more logging!** Which naturally made the problem worse and even harder to figure out. 
> 
> <a title="The Problem With Logging" href="http://www.codinghorror.com/blog/archives/001192.html" target="_blank">[link: The problem with logging]</a>

This illustrates my point exactly. 99% of the time logging affect the system in a neglible way. But you have to keep in mind that it actually could affect the &#8220;experiment&#8221;. In this case the performance or the behavior of your program.

 

My job is &#8220;Production Support&#8221; in the ITIL way. IE. ensuring quality of running services with  Incident Management and Problem Management. That means that for anything not related to normal operations we often need the logs. 

> Also in these days of powerful IDEs and remote debugging is that much logging really nescisary?
> 
> <a style="text-decoration: none;" href="http://stackoverflow.com/questions/153524/code-to-logging-ratio" target="_blank">[link: Stackoverflow: Code to logging ratio]</a>

Yes it is! We are supporting an <a title="wikipedia on ESB" href="http://en.wikipedia.org/wiki/Enterprise_service_bus" target="_blank">ESB</a> developed and customized during the last 3-5years and attaching a debugger isn&#8217;t really an option. 

So we are basically totally dependent on **good** logging for troubleshooting.

We have been dealing with a problem relating to big batches of large messages and the 2GB limit of our JVM&#8217;s. We started by initiating a project to throw some dedicated hardware after the code handing these large messages so it wouldnt affect the rest of the &#8220;stuff&#8221; running on the same application server. But unfortunately hardware acquirement and machine setup can be a slow process, and worst of all: It&#8217;s out of our hands! <img src="http://blog.vrist.dk/newwp/wp-includes/images/smilies/simple-smile.png" alt=":)" class="wp-smiley" style="height: 1em; max-height: 1em;" />

So our current guru took a quick look at the code and started grabbing for some low hanging fruit:

<div id="attachment_174" style="width: 415px" class="wp-caption alignnone">
  <img class="size-full wp-image-174 " title="Before debug" src="http://blog.vrist.dk/fwp/wp-content/uploads/2009/01/fc3b8r-debug.jpg" alt="Before ifDebugEnabled" width="405" height="155" />
  
  <p class="wp-caption-text">
    Before ifDebugEnabled
  </p>
</div>

<div id="attachment_175" style="width: 414px" class="wp-caption alignnone">
  <img class="size-full wp-image-175 " title="efter-debug" src="http://blog.vrist.dk/fwp/wp-content/uploads/2009/01/efter-debug.jpg" alt="After using if debugEnabled" width="404" height="156" />
  
  <p class="wp-caption-text">
    After using if debugEnabled
  </p>
</div>

 It turns out that developer had used the same politic as mentioned in the stackoverflow post:

> <&#8230;
  
> **DEBUG Level**
> 
>   * Any parameters passed into the method
> 
> &#8230;>
  
>  

The parameter in this case was 1-2MB xml-data which was logged like this:

> <pre lang="java">LOG.debug("Entering part 2.1 of method MyMethod with msg: "+msg.toXml());</pre>

In production only INFO and above is logged so the debug message was discarded. But the concat of 2MB data was still performed several times per message (10-12 as far as I recall). So the difference between the above to memory graphs is:

> <pre lang="java">if (LOG.isDebugEnabled()){
    LOG.debug("Entering part 2.1 of method MyMethod with msg: "+msg.toXml());
}</pre>
> 
> (as also mentioned here: http://wordstoday.wordpress.com/2007/11/26/log4j-why-use-isdebugenabled-in-your-code/)

This should buy us some time before we can isolate this process on it&#8217;s own hardware/jvm.

The guru is currently looking into writing a <a title="XPath tutorial from w3school" href="http://www.w3schools.com/XPath/default.asp" target="_blank">xpath</a> expression for <a title="PMD website" href="http://pmd.sourceforge.net/" target="_blank">PMD</a> run over our giant codebase. Could be fun to see what it&#8217;ll dig up
---
title: Eclipse setup
author: svrist
layout: post
date: 2008-04-03
url: /2008/04/03/eclipse-setup/
dsq_thread_id:
  - 68433617

---
<span class="zemanta-img" style="display:block;float:right;margin:1em;"><a href="http://commons.wikipedia.org/wiki/Image:Wave.svg" target="_blank"><img style="border:medium none;display:block;" src="http://upload.wikimedia.org/wikipedia/commons/thumb/4/40/Wave.svg/202px-Wave.svg.png" alt="Duke, the Java Mascot, in the waving pose." /></a><span style="display:block;margin:1em 0 0;">Image from <a href="http://commons.wikipedia.org/wiki/Image:Wave.svg">Wikipedia</a></span></span>I work with <a title="Eclipse website" href="http://eclipse.org" target="_blank">eclipse</a> all day, so I&#8217;ve spent some time messing around with plugins. Lots and lots of plugins.

The plugins I&#8217;ve current stablized on is:

  * Maven2 plugin: <a title="Maven2 plugin" href="http://m2eclipse.codehaus.org/" target="_blank">http://m2eclipse.codehaus.org/</a> (update-site: http://m2eclipse.sonatype.org/update/)
  * PMD for static analysis of java code: <a title="PMD for eclipse" href="http://pmd.sourceforge.net/integrations.html#eclipse" target="_blank">http://pmd.sourceforge.net/integrations.html#eclipse</a> (update-site: http://pmd.sf.net/eclipse )
  * Findbugs for static analysis of java bytecode <a title="Findbugs eclipse plugin" href="http://findbugs.sourceforge.net/manual/eclipse.html" target="_blank">http://findbugs.sourceforge.net/manual/eclipse.html </a>(update-site: http://findbugs.cs.umd.edu/eclipse/)
  * Checkstyle for doing code the Right Way(tm). <a title="Checkstyle" href="http://eclipse-cs.sourceforge.net/" target="_blank">http://eclipse-cs.sourceforge.net/</a> (update-site: http://eclipse-cs.sourceforge.net/update)
  * EclEmma <a title="ECLEMMA" href="http://www.eclemma.org/" target="_blank">http://www.eclemma.org/</a> for junit codecoverage (update-site: http://update.eclemma.org/) Very nice to get a view of how much your tests cover your code. 50% should be possible right? <img src="http://blog.vrist.dk/newwp/wp-includes/images/smilies/simple-smile.png" alt=":)" class="wp-smiley" style="height: 1em; max-height: 1em;" />
  * SpringIDE for code completion in spring bean xml-files. Very very nice! <a title="Spring IDe" href="http://springide.org/project/wiki/SpringideInstall" target="_blank">http://springide.org/project/wiki/SpringideInstall</a>, (Update-site: http://springide.org/updatesite)

I use the code formatter extensively as possible. It&#8217;s very nice to get these things like a gift instead of spending time on wrapping lines and formatting by hand.

When using the codeformatter you really can benefit from &#8220;<a title="Save action praise from other blogger" href="http://zvikico.typepad.com/problog/2007/08/eclipse-europa-.html" target="_blank">Save Actions</a>&#8220;. The most timesaving feature for me so far. My setup currently includes all checkboxes, and a stack of additional action. No more time spent inserting spaces between ) and {

Good stuff!

For my <a title="On of my posts about sparetime project" href="http://blog.vrist.dk/2008/02/19/toying-around/" target="_blank">sparetime</a> <a title="Sparetime project 2" href="http://blog.vrist.dk/2008/02/20/focus-on-the-technology/" target="_blank">project</a> I&#8217;m currently exploring other plugins:

  * Mercurial eclipse plugin: <a title="Eclipse hg plugin" href="http://www.vectrace.com/mercurialeclipse" target="_blank">http://www.vectrace.com/mercurialeclipse</a> (Update-site: http://www.vectrace.com/eclipse-update/)
  * <a title="New plugin mail" href="http://article.gmane.org/gmane.comp.lang.scala/11181" target="_blank">new Scala plugin</a> : http://scala.sygneca.com/tools/eclipse

The mercurial plugin isn&#8217;t quite ready yet, but it&#8217;s getting there. <a title="A ticket i spend some time on" href="http://home.zingo.org/trac/mercurialeclipse/ticket/166" target="_blank">Things are happening</a>, and as the mail and website for the new scala plugin suggests that plugin isn&#8217;t quite there yet.

I dont mind, it gives you that pioneering feeling <img src="http://blog.vrist.dk/newwp/wp-includes/images/smilies/simple-smile.png" alt=":)" class="wp-smiley" style="height: 1em; max-height: 1em;" />

If anybody should pop by and see this list, feel free to suggest all those nifty plugins I&#8217;m missing!

Happy coding

<fieldset>
  <legend>Related articles</legend> 
  
  <ul class="zemanta-article-ul" style="margin:1em 0 1.5em;padding:0;">
    <li class="zemanta-article">
      <a title="Open in new window" href="http://www.regdeveloper.co.uk/2008/03/14/java_platform_scripting_languages/" target="_blank">Other languages key to Java&#8217;s future</a> [via Zemanta]
    </li>
  </ul>
</fieldset>

<div id="zemanta-pixie" style="width:100%;margin:5px 0;">
  <a id="zemanta-pixie-a" title="Zemified by Zemanta" href="http://www.zemanta.com/"><img style="border:medium none;float:right;" src="http://img.zemanta.com/pixie.png?x-id=baa0f4e1-1003-4adf-a5d4-069214f0200d" alt="" /></a>
</div>
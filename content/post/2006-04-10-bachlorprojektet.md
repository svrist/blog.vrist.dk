---
title: Bachlorprojektet
author: svrist
layout: post
date: 2006-04-10
url: /2006/04/10/bachlorprojektet/
dsq_thread_id:
  - 68433433

---
Jeg synes lige det må være på sin plads med en opdatering omkring projektet <img src="http://blog.vrist.dk/newwp/wp-includes/images/smilies/simple-smile.png" alt=":)" class="wp-smiley" style="height: 1em; max-height: 1em;" />

Vi har fået tastet vores fine grammatik ind i en <a href="http://seet.dk/~seet/dat2b/kode/dk/kb/tdiagrams/parser/compiler/format.g" title="grammatik fil for antler" target="_blank">grammatik fil</a> for <a href="http://antlr.org/" title="Another tool for language recognition" target="_blank">antlr</a>. Det er ganske kraftfuldt det der antlr, med EBNF og alt muligt. Vi har en mini-lille lexer definition, en parser definition som laver et nydeligt træ og tilsidst en treeparser som løber det træ igennem og først og fremmest laver vores navnerum, og derudover kontrollerer at programmet &#8220;er&#8221; et gyldigt T-diagram. Dvs. stort set at brikkerne passer sammen lige som i domino.

Se et par diagram-programmer

[d1.b][1] [d2.b][2] [d3.b][3] Det overlades til læseren selv at regne ud hvad det er for nogle faktiske diagrammer de &#8220;laver&#8221;.
  
Nu skal vi til at have lavet noget rigtigt rapport (ud over [gram1.pdf][4]) og derefter er der mindst de sidste to semantikker

&#8211; Tegning &#8211; Umiddelbart skal vi bare understøtte et par interfaces til at tegne med og ikke til selv at rode med at tegne ting på skærmen osv. meeeen måske gør vi det alligevel. Det kunne jo være rart at få et par tegninger ud af det, og fra min dat0gb opgave har vi nogle tegne tools
  
&#8211; Opslag &#8211; Vi skal have lavet mulighed for at kunne lave opslag som giver et diagram ud for hvordan en given fil kan afvikles på en given maskine
  
Og så er der lige rapporten og evt. definiere noget database format for maskiner til brug for opslagsdimsen. <img src="http://blog.vrist.dk/newwp/wp-includes/images/smilies/simple-smile.png" alt=":)" class="wp-smiley" style="height: 1em; max-height: 1em;" />
  
Stadigt spændende ihvertfald, og det er jo godt

 [1]: http://seet.dk/~seet/dat2b/rapport/d1.b
 [2]: http://seet.dk/~seet/dat2b/rapport/d2.b
 [3]: http://seet.dk/~seet/dat2b/rapport/d3.b
 [4]: http://seet.dk/~seet/gram1.pdf
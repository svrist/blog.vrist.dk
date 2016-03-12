---
title: Biomolecular computers and programming
author: svrist
layout: post
date: 2010-06-07
url: /2010/06/07/biomolecular-computers-and-programming/
dsq_thread_id:
  - 105000161
categories:
  - English

---
I have recently handed in a report as a part of my masters/candidate in <a href="http://www.diku.dk" target="_blank">Computer Science at University of Copenhagen</a> &#8211; _&#8220;<a title="BlobVis visualization tool" href="http://blobvis.appspot.com" target="_blank">Visualizing blobs and computation in a biomolecular computation model</a>&#8220;._ It sounds very fancy and I would like to introduce the subject and my report here in hopefully a less dry way than in the report it self. <span style="color: #808080;">(This post will be in a &#8220;anecdotal&#8221; style and will not contain citations for all the facts. The report above should be up to academic par on citations)</span>

## Biomolecular computers and computation

Biomolecular computers or &#8220;biocomputers&#8221; is an area that have been research the last 20 years. At first much hype and hope was attached that this would provide some kind of break through to overcome the limitations of normal <a title="Wikipedia: Chip Computers" href="http://en.wikipedia.org/wiki/Computer_chips" target="_blank">silica-based chip computers</a> as we know and use today &#8211; your average PC and every microchip controlled device around. This is the same hope that surrounds <a title="Wikipedia: Quantum Computer" href="http://en.wikipedia.org/wiki/Quantum_computer" target="_blank">quantum computers</a> &#8211; a new approach for doing currently very long computations, for example <a title="Wikipedia: Integer Factorization" href="http://en.wikipedia.org/wiki/Integer_factorization" target="_blank">integer factorization</a> of large prime products within feasible time. The jury is still out on the possibility of [biomolecular computing][1] to deliver on that hope/potential. Other research have also shown &#8220;niche&#8221; interest in the area of <a title="Scientific american: Bringing DNA Computers to life" href="http://www.scientificamerican.com/article.cfm?id=bringing-dna-computers-to" target="_blank">&#8220;DNA Doctor&#8221; usage</a> of biocomputers where a &#8220;biocomputer&#8221; is implemented to interact directly with the cells in for example humans.

A biomolecular computer can be seen as a computer that  &#8220;._&#8230;use systems of biologically derived molecules, such as_ [_DNA_][2] _and_ [_proteins_][3]_, to perform computational_ [_calculations_][4] _involving storing, retrieving, and processing_ [_data_][5]_._&#8220;(F<a href="http://en.wikipedia.org/wiki/Biomolecular_computing" target="_blank">rom wikipedia</a>). Why is this interesting?

First of all: Why not? Tinkering, and playing around with things is interesting IMHO: By drawing the parallel between a biocomputer and a (human) brain you can say that it is a way to learn about ways nature works.

Second of all, a biocomputer will have different properties compared to conventional computers. Some of the first explored ideas was to use DNA interactions to solve very computational hard problems (NP-complete, traveling salesman like problems, Adleman 1994). This is interesting because it is possible to have millions and millions of molecules in lab-tube and thereby allowing for massively parallel computations &#8211; compared to a conventional computer which might have 4 (or at least not millions of) cores for parallel computations.

## The Blob programming model

When I contacted my supervisor about writing a project this winter I was introduced to &#8220;the blob programming model&#8221;. At that time it was mostly an article in progress. Just now it has been accepted for the <a title="CS2Bio programme. 10.30 Programming in Biomolecular computation" href="http://cs2bio10.di.unito.it/programme.html" target="_blank">CS2Bio workshop</a> as &#8220;Programming in Biomolecular computation&#8221; in Amsterdam, June 10, 2010.

The authors, <a title="Neil Jones page" href="http://www.diku.dk/hjemmesider/ansatte/neil/" target="_blank">Neil Jones</a> in particular, read lots of the articles around biomolecular computation, turing universality of the models, and formal algebras for describing molecular interactions (Like <a title="Kappa" href="Formal Molecular Biology" target="_blank">Kappa calculus</a> and <a title="Cardelli" href="http://lucacardelli.name/indexPapers.html#TuringUniversalityOfBGF" target="_blank">Biochemical Ground Form</a>) but his background as a computer scientist found something missing: **Where are the programs?**

Lots of interesting computational properties was proven but as a programmer there is no way to write a program as we know it.

Based on that &#8220;hole&#8221; a machine language was developed and described in the article which might theoretically could be used on a biocomputer. The models was dubbed &#8220;The blob programming model&#8221; and the article can be found at <a href="http://blobvis.appspot.com/blob" target="_blank">http://blobvis.appspot.com/blob</a>

## My Project &#8211; Visualizations of Blob programs

Based on this article I defined a project for doing a literature review of biocomputing literature as well as visualization theory applicable to visualization of blob programs. Normal progrogramming visualizations exists and have been used for many years, but in this case there was a special angle attached to the visualizations. The blob model has a potential physical analog as it might be possible to create a &#8220;biomolecular computer&#8221; that can execute the instructions and as the instructions is formed to be somewhat like an abstract molecule or similar a visualization of the blob instruction set could/should reveal interesting properties of blob programs with regards to their physical presence.

<div style="width: 260px" class="wp-caption alignleft">
  <a href="http://blobvis.appspot.com/screenshots"><img title="A blob program" src="http://blobvis.appspot.com/static/thumb_largedata-play.jpg" alt="" width="250" height="243" /></a>
  
  <p class="wp-caption-text">
    A program in the BlobVis tool
  </p>
</div>

At <a title="Blobvis site" href="http://blobvis.appspot.com" target="_self">http://blobvis.appspot.com</a> my report is available for download as well as the BlobVis visualization tool I developed. From there you can play around with a few simple &#8220;Blob Programs&#8221;, for example a &#8220;list append'&#8221; program and see a video of a program executing in BlobVis. As I focused on physical properties the tool uses a physical based algorithm for layouting the blob programs(Via <a href="http://prefuse.org" target="_blank">prefuse</a>) which allows you to drag around programs and data in a way that looks like it is immersed in water or similar. That gives an interesting effect and is fun to watch.

 [1]: http://en.wikipedia.org/wiki/Biomolecular_computing
 [2]: http://en.wikipedia.org/wiki/DNA "DNA"
 [3]: http://en.wikipedia.org/wiki/Proteins "Proteins"
 [4]: http://en.wikipedia.org/wiki/Calculation "Calculation"
 [5]: http://en.wikipedia.org/wiki/Data "Data"
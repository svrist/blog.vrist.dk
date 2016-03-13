---
title: LaTeX tricks
author: svrist
layout: post
date: 2005-08-11
url: /2005/08/11/latex-tricks/
dsq_thread_id:
  - 68433264

---
Jeg har altid været træt af at copy-paste en masse indledende manøvre for at få mine LaTeX dokumenter til at blive &#8220;som de plejer&#8221;. Når jeg skriver [DIKU][1] rapporter bruger jeg en opsætning, og når jeg laver [clique][2] dokumeter er det anderledes. Især med clique var det irriterende da jeg skulle bruge et par billeder og lign. fast, og normalt skulle de så ligge sammen med selve .tex eller et eller andet sted med predefineret hardcodet sti.

Det ledte til at jeg lave et par scripts:

## [c][3]

    
    #!/bin/sh
    
    
    prof=`echo $0 | sed -E "s/.*\/(.*)$/\1/"`
    
    
    . ~/texprofiles/$prof
    cmd=$1;
    shift
    
    $cmd $*
    
    

som jeg gemmer i ~/bin

Derefter laver jeg så en fil med samme navn som ovenstående og gemmer i ~/texprofiles.

### c

    
    includes=/home/sv/svn/clique/docbuilds
    export TEXINPUTS=".:$TEXINPUTS:$includes"
    
    

Jeg har brugt samme trict som med så mange andre unix tools, at scriptet opfører sig anderledes alt efter hvilket navn man bruger til det.
  
Hvis jeg f.eks. ville lave med diku includes, så ville jeg bare lave en

    
    ln -s ~/bin/c ~/bin/diku
    
    

og derefter sørge for at der er en diku i ~/texprofiles med det rette info.

Med ovenstående script og config kan jeg have mine billeder og type-specifikke preambles og funktioner i et fast dir og bare referere til det som
  
\input{master} hvor som helst bare jeg kører latex som:

    
    c latex minfix.tex
    
    

Derudover har jeg lavet et lille oprydningsscript:

### tclean

    
    #!/bin/sh
    
    if [ -e *.toc ]
    then
       rm *.toc
    fi
    
    if [ -e *.log ]
    then
       rm *.log
    fi
    
    if [ -e *.dvi ]
    then
       rm *.dvi
    fi
    
    
    if [ -e *.aux ]
    then
       rm *.aux
    fi
    
    if [ $1 ]
    then
    
    if [   $1 = "ps"  -o  $1 = "all"  -a  -e *.ps  ]
    then
       rm *.ps
    fi
    
    if [  $1 = "pdf" -o $1 = "all"   -a  -e *.pdf  ]
    then
       rm *.pdf
    fi
    
    fi
    
    

Det er så irriterende når der ligger alle de filer og roder <img src="http://blog.vrist.dk/newwp/wp-includes/images/smilies/simple-smile.png" alt=":)" class="wp-smiley" style="height: 1em; max-height: 1em;" />

Nu mangler jeg så bare at få lavet en eller anden form for makefile hieraki. [Simon][4] viste mig en Makefile vi brugte da vi lavede multimedia opgave, og det er ret smart til det, men problemet er at jeg også er blevet træt af at kopiere den stakkels Makefile rundt til alle projekter og opgaver <img src="http://blog.vrist.dk/newwp/wp-includes/images/smilies/simple-smile.png" alt=":)" class="wp-smiley" style="height: 1em; max-height: 1em;" />

 [1]: http://diku.dk
 [2]: http://clique.dk
 [3]: http://seet.dk/files/c
 [4]: http://simon.nitro.dk
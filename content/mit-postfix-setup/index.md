---
title: Postfix setup
author: svrist
layout: page
date: 2007-11-06
dsq_thread_id:
  - 68433537

---
# <u>** <font color="#ff0000"></font>**</u>**<font color="#ff0000">Jeg er gået over til Google, og dette er derfor aldeles pensioneret! </font>**

<p align="center">
  &nbsp;
</p>

* * *

## Search engine update

_I&#8217;ve noticed some hits from search engines regarding &#8220;_

<pre>postfix php script</pre>

&#8221; _and who am I to mislead these people?_

<p align="center">
  <em>I&#8217;ve actually used some time doing postfix setup. My research shows that it hardly is the timeworth to do your own scripting. <strong><a href="http://postfixadmin.sourceforge.net/" title="Postfixadmin homepage" target="_blank">Postfixadmin</a> can do the job perfectly.</strong></em>
</p>

_I&#8217;ve actually also seen some setups with postfix -> qmail -> vpopmail for more customer selfcare. Quite ok._

_Don&#8217;t use my guide here; try some of these maybe?_

  * <a href="http://www.howtoforge.com/virtual_users_postfix_courier_mailscanner_clamav_centos" title="Postfixadmin guide 1" target="_blank">http://www.howtoforge.com/virtual_users_postfix_courier_mailscanner_clamav_centos</a>
  * <a href="http://switch.richard5.net/isp-in-a-box-v2/installing-and-configuring-postfixadmin/" title="Postfixadmin guide 2" target="_blank">http://switch.richard5.net/isp-in-a-box-v2/installing-and-configuring-postfixadmin/</a>
  * <a href="http://es-web.dk/howto/?Side_ID=5" title="Postfixadmin guide 3" target="_blank">http://es-web.dk/howto/?Side_ID=5</a> [danish]

* * *

## Gammel guide &#8211; outdated

Nu har jeg efterhånden brugt nogle år på at få [postfix][1] til at makke ret. Diverse løsninger er opstået og jeg har brugt en del tid på at formidle det indimellem til de få rå der har gidet at høre om det.
  
Det har resulteret i noget (mere eller mindre outdatet) kode som jeg har liggende her på seet.dk.Hele &#8220;konceptet&#8221; er virtuelle postdomæner, med de nødvendige oplysninger gemt i en sql-database med et rimeligt skema. Det har krævet en del krumspring at får &#8220;normaliseret&#8221; den simple måde at lave postfix-courier-imap-mysql setup på over til et rimeligt database-skema.Først resulterede det i nogle halvlanghårdede sqls for at lave joins osv. over de rigtige tabeller, men med mit begrænsede kendskab til sql og [mysqls][2] evner gjorde at jeg frygtede det slet ikke skalerede med så slemme sql&#8217;s.

    
    
    select concat(userdata.username,\"mapdir\",\"@\",domains.domain),
    
    concat(domains.domain,\"/\", userdata.username,\"/Maildir/\"),
    
    concat(userdata.username,\"mapdir\",\"@\",domains.domain),
    
    domains.uid, domains.gid,
    
    \"dir\"
    
    from userdata, domains
    
    where userdata.domain = domains.id
    
    and userdata.mapping in ('dir+remote')
    
    
    
    SELECT userdata.username, userdata.password, domains.uid, domains.gid,
    
    concat('/usr/mailboxes/',domains.domain,'/',userdata.username,'/Maildir/'),
    
    userdata.realname, domains.domain
    
    from userdata, domains
    
    where userdata.domain = domains.id and substring(userdata.mapping,1,3) = 'dir'
    
    

Når jeg kigger på det nu, virker de ikke så slemme, og med en [rigtig database][3] ville det være en smal sag at lave ovenstående smart og fint.
  
En dag når jeg får tid&#8230;

Mine tests viste mig også at der bliver lavet mindst 4 opslag p. modtagen mail, hvilket heller ikke gjorde det federe. Derfor besluttede jeg dengang at lave et script (php var hvad jeg kunne) som parsede de &#8220;smukke&#8221; tabeller og lavede noget i stil med hashmaps (bare i sql) som postfix og courier-imap så blev peget over på.

Efterhånden fik jeg interesseret en anden gut i setuppet, men han skulle også bruge nogle flere features, så scriptet og databasen blev udvidet og nu står der efterhånden en del.

  * Scanning af mails med amavis og spamassassin
  * Forwards
  * Mailboxes (imap og pop3)
  * Autoresponder
  * i &#8211; alias
  
    En omvendt måde at lave forwards på. Definer en adresse og x-andre adresser i samme domæne som alle skal gå til den første adresse. Sært
  * Mailinglists med mailman

Og diverse kombinationer af ovenstående.

Tiden er dog ved at være løbet fra hele setuppet og koden og sql&#8217;en , men det skulle dog virke endnu.

**Filer i setuppet**
  
_Disclaimer_

Alt det her kræver at man faktisk fatter en smule af postfix og courier for at kunne bruge det til noget

  * [Postfix-config filerne][4]
  
    Først og fremmest, v*.cf og en master.cf entry til autoresponder, transport.cf og main.cf
  * [Courier.][5]
  
    Begge filer skal bruges, men det er muligt at istedet for at bruge filen direkte man burde merge de &#8220;rigtige&#8221; ting ind i en tidssvarende conf.
  * [Databasen][6]
  
    Skemaet til databasen. *.tables.dump er incl. misc entries fra et gammelt setup som man kan bruge som eksempel. De tabeller man bør ændre i er userdata,domains,autoreply. De andre står scriptet for.
  * [Amavis, mailscanning/filtering][7].
  
    Læg mærke til at der er lavet et farligt hack i toppen af amavisd.conf som sikkert er meget unødvendingt og kunne laves smartede med passende amavis-features nu om dage.
  * [Scripts.][8]
  
    Her er det famøse glue.php som står for oprettelsen af de rette mængder data for aggregat tabellerne. Derudover er der et autoreply script, men dette er major buggy. Faktisk broken så vidt jeg ved.
  * [Cli][9]
  
    Jeg har faktisk forberedt en smule CLI til systemet, men der er ingen garanti for at noget som helst i dette bib funker. Here be dragons

Resten er bare pynt eller rod.

Hvis der er nogen spørgsmål eller rants så skriv til [devnull@seet.dk][10]&#8230;Hmm eller <postfix@seet.dk>

 [1]: http://postfix.org
 [2]: http://www.mysql.com
 [3]: http://postgresql.org
 [4]: http://seet.dk/postfix/postfix/
 [5]: http://seet.dk/postfix/courier-imap
 [6]: http://seet.dk/postfix/base/
 [7]: http://seet.dk/postfix/amavis/
 [8]: http://seet.dk/postfix/scripts/
 [9]: http://seet.dk/postfix/cli/
 [10]: mailto:postfix@seet.dk
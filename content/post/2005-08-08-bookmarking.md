---
title: Bookmarking
author: svrist
layout: post
date: 2005-08-08
url: /2005/08/08/bookmarking/
dsq_thread_id:
  - 68433258

---
Phil (PHB@catpipe.net :D) viste mig i dag [delicious][1]. Super coolt til bookmarking distributed edition. Når man bookmarker en side kan man skrive et par tags på til at indexere efter og derefter er det super nemt at holde styr på dem ud fra de tags,hvis man bruger nogle ordenlige. Heldivis har den sådan en fin [suggest mulighed][2] som gør det hele noget nemmere.

Det distribuerede ligger i at alle ens bookmarks er offentlige, og hvis der er andre der bookmarker til en af de samme sider kan man se hvem de er og hvad de så ellers har i deres bookmark samlinger. Ganske ok!

Se f.eks. min: <http://del.icio.us/seet>

Derudover er der diverse [Phil (PHB@catpipe.net :D) viste mig i dag [delicious][1]. Super coolt til bookmarking distributed edition. Når man bookmarker en side kan man skrive et par tags på til at indexere efter og derefter er det super nemt at holde styr på dem ud fra de tags,hvis man bruger nogle ordenlige. Heldivis har den sådan en fin [suggest mulighed][2] som gør det hele noget nemmere.

Det distribuerede ligger i at alle ens bookmarks er offentlige, og hvis der er andre der bookmarker til en af de samme sider kan man se hvem de er og hvad de så ellers har i deres bookmark samlinger. Ganske ok!

Se f.eks. min: <http://del.icio.us/seet>

Derudover er der diverse][3] muligheder som Phil også fik vist mig.

`</p>
<pre>
wget -O bookmarks.xml --http-user=yyyyyy --http-passwd='xxxxxxx' \
  http://del.icio.us/api/posts/all

perl -MYAML -MXML::Simple -e 'print Dump XMLin shift' bookmarks.xml

</pre>
<p>`

 [1]: http://del.icio.us
 [2]: http://www.google.com/webhp?complete=1&hl=en "google suggest"
 [3]: http://del.icio.us/doc/api
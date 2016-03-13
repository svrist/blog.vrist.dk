---
title: What does CodingHorror have in common with Apache H-Base?
author: svrist
layout: post
date: 2010-02-18
url: /2010/02/18/what-does-codinghorror-have-in-common-with-apache-h-base/
dsq_thread_id:
  - 68433670
categories:
  - English

---
As I was in my &#8220;<a title="Class description" href="https://mit.itu.dk/ucs/cb_www/course.sml?course_id=868178&mode=search&semester_id=859988&lang=da&print_friendly_p=t&goto=1266753057.000" target="_blank">Advanced data management</a>&#8221; class today I realized that <a href="http://codinghorror.com" target="_blank">CodingHorror</a> aka Jeff Atwood of <a href="http://blog.stackoverflow.com" target="_blank">stackoverflow</a> fame agree quite alot with <a href="http://hadoop.apache.org/hbase/" target="_blank">Apache H-base</a>. <a href="http://hadoop.apache.org/hbase/" target="_blank">Apache H-base</a> is a column-store database system based on the <a href="http://labs.google.com/papers/bigtable.html" target="_blank">Google BigTable</a> ideas leveraging Apache Hadoop.

Jeff Atwood was is not very happy with the default &#8220;<a style="color: #0066cc; text-decoration: none;" href="http://www.databasejournal.com/features/mssql/article.php/3560451" target="_blank">incredibly pessimistic out of the box</a>&#8221; setup of databases in his <a href="http://www.codinghorror.com/blog/2008/08/deadlocked.htm" target="_blank">&#8220;Deadlocked!&#8221;</a> post.  Along the same lines, the H-store people published an article[1]:

>  <a href="http://nms.csail.mit.edu/~stavros/pubs/hstore.pdf" target="_blank">The End of an Architectural Era (It’s Time for a Complete Rewrite). </a>

They claim that the time is up for &#8220;legacy systems&#8221; like the model used by current RDMBS&#8217; like MySQL and SQL Server. The assumption of the H-base people that reasonates with Jeff Atwood &#8211; I believe &#8211; is:

> Every effort should be made to eliminate the cost of traditional dynamic locking for concurrency control, which will also be a bottleneck.

I don&#8217;t know if it is something Jeff Atwood is aware of, and I don&#8217;t know if that is a sign that a traditional RDBMS is maybe not what he wants, but it is worth think about &#8211; IMHO.

* * *[1]

<span style="font-family: verdana, arial, helvetica, sans-serif; line-height: normal; font-size: 11px; color: #444444;">Stonebraker, M., Madden, S., Abadi, D. J., Harizopoulos, S., Hachem, N., Helland, P., 2007. The end of an architectural era: (it&#8217;s time for a complete rewrite). In: VLDB &#8217;07: Proceedings of the 33rd international conference on Very large data bases. VLDB Endowment, pp. 1150-1160. URL:<a style="color: #1f81cd;" href="http://portal.acm.org/citation.cfm?id=1325981"><tt>http://portal.acm.org/citation.cfm?id=1325981</tt></a> <a href="http://nms.csail.mit.edu/~stavros/pubs/hstore.pdf">pdf</a> &#8211; <a href="http://liinwww.ira.uka.de/cgi-bin/bibshow?e=Njtd0ECMQ03118/fyqboefe}6:514795&r=bibtex&mode=intra">Bibtex</a> </span></p>
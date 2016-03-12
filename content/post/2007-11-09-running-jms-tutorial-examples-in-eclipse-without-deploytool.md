---
title: Running JMS tutorial examples in Eclipse without deploytool
author: svrist
layout: post
date: 2007-11-09
url: /2007/11/09/running-jms-tutorial-examples-in-eclipse-without-deploytool/
dsq_thread_id:
  - 68433554

---
I&#8217;ve currently been reading up on JMS via the <a title="J2EE 1.4" href="http://java.sun.com/j2ee/1.4/docs/tutorial/doc/" target="_blank">J2EE 1.4 tutorial</a>. (Chapters <a title="J2EE tutorial chapter 33" href="http://java.sun.com/j2ee/1.4/docs/tutorial/doc/JMS.html#wp84181" target="_blank">33</a> and <a title="J2EE tutorial chapter 34" href="http://java.sun.com/j2ee/1.4/docs/tutorial/doc/JMSJ2EEex.html#wp81128" target="_blank">34</a>). I use Eclipse J2EE.

The deploytool way of doing things annoyed me quite a bit. When I had to edit the /jms/simple/src/* code for the first example (remove the jupiter prefix used for the next example in the Connection Factories) I really wanted to use eclipse. But in Eclipse I needed to emulate all the magic that asant.bat and appclient.bat made to build the class-files and run the code. After lots and lots of browsing I found the jars I needed in my build (and run) path. I created an Application Client project for each of SimpleProducer, SimpleSyncConsumer and SimpleAsyncConsumer.

Each of these in the buildpath.

  * C:\Sun\AppServer\lib\install\applications\jmsra\imqjmsra.jar
  * C:\Sun\AppServer\lib\appserv-admin.jar
  * C:\Sun\AppServer\lib\appserv-rt.jar
  * C:\Sun\AppServer\imq\lib\imq.jar

besides from being created with the Sun Application Server 8.2 Default Configuration in the eclipse wizard. <a title=".classpath from one of the Application Clients" href="http://seet.dk/~seet/.classpath-jms-simple-example" target="_blank">Here&#8217;s a .classpath</a>

I also tried to emulate the deploytools .jars. To be able to create jars usable by appclient (and everything else) you need to manually fix the MANIFEST.MF. Set the Main-Class: to the right class. For examples like this for SimpleProducer:

`I&#8217;ve currently been reading up on JMS via the <a title="J2EE 1.4" href="http://java.sun.com/j2ee/1.4/docs/tutorial/doc/" target="_blank">J2EE 1.4 tutorial</a>. (Chapters <a title="J2EE tutorial chapter 33" href="http://java.sun.com/j2ee/1.4/docs/tutorial/doc/JMS.html#wp84181" target="_blank">33</a> and <a title="J2EE tutorial chapter 34" href="http://java.sun.com/j2ee/1.4/docs/tutorial/doc/JMSJ2EEex.html#wp81128" target="_blank">34</a>). I use Eclipse J2EE.

The deploytool way of doing things annoyed me quite a bit. When I had to edit the /jms/simple/src/* code for the first example (remove the jupiter prefix used for the next example in the Connection Factories) I really wanted to use eclipse. But in Eclipse I needed to emulate all the magic that asant.bat and appclient.bat made to build the class-files and run the code. After lots and lots of browsing I found the jars I needed in my build (and run) path. I created an Application Client project for each of SimpleProducer, SimpleSyncConsumer and SimpleAsyncConsumer.

Each of these in the buildpath.

  * C:\Sun\AppServer\lib\install\applications\jmsra\imqjmsra.jar
  * C:\Sun\AppServer\lib\appserv-admin.jar
  * C:\Sun\AppServer\lib\appserv-rt.jar
  * C:\Sun\AppServer\imq\lib\imq.jar

besides from being created with the Sun Application Server 8.2 Default Configuration in the eclipse wizard. <a title=".classpath from one of the Application Clients" href="http://seet.dk/~seet/.classpath-jms-simple-example" target="_blank">Here&#8217;s a .classpath</a>

I also tried to emulate the deploytools .jars. To be able to create jars usable by appclient (and everything else) you need to manually fix the MANIFEST.MF. Set the Main-Class: to the right class. For examples like this for SimpleProducer:

`
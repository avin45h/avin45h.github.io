---
layout: post
title: Node.js
comments: true
---

<div class="entry">
<h6><span style="font-family:verdana,geneva,sans-serif;"><span style="color: rgb(105, 105, 105);">(a Java developer&#39;s simple view)</span></span></h6>

<hr />
<p><span style="font-family:verdana,geneva,sans-serif;"><span style="color: rgb(105, 105, 105);"><span style="font-size: 14px;">Around an year back, I shifted to node.js. My career since beginning has been mostly about Java. After programming around traditional java-isque apps since like 4 years, node.js intrigued me. And that is when I took the leap to checkout what is the node.js hype about.</span></span></span></p>

<p><span style="font-family:verdana,geneva,sans-serif;"><span style="color: rgb(105, 105, 105);"><span style="font-size: 14px;">Node.JS is an awesome runtime which let&rsquo;s you write server/network logic using javascript, utilizing the event driven paradigm and is non blocking, which just basically means that you write the logic for some event, and specify what should happen after the event is complete and just proceed with next steps of your server side logic.</span></span></span></p>

<p><span style="font-family:verdana,geneva,sans-serif;"><span style="color: rgb(105, 105, 105);"><span style="font-size: 14px;">An analogy of this would be a birthday party planning. You&rsquo;re planning a birthday, you call up a cake shop, tell them that you want a cake , and as the cake is done, deliver it at a certain address with a nice greeting card. After telling them up, you just proceed to manage decorations for party and further work and so on.</span></span></span></p>

<p><span style="font-family:verdana,geneva,sans-serif;"><span style="color: rgb(105, 105, 105);"><span style="font-size: 14px;">If I were to plan this party using traditional design, this would be something like this (Considering I didn&rsquo;t make threads) :</span></span></span></p>

<ol>
	<li><span style="font-family:verdana,geneva,sans-serif;"><span style="color: rgb(105, 105, 105);"><em><span style="font-size: 14px;">Call cake shop</span></em></span></span></li>
	<li><span style="font-family:verdana,geneva,sans-serif;"><span style="color: rgb(105, 105, 105);"><em><span style="font-size: 14px;">Wait for the cake to be made.</span></em></span></span></li>
	<li><span style="font-family:verdana,geneva,sans-serif;"><span style="color: rgb(105, 105, 105);"><em><span style="font-size: 14px;">Wait for the delivery.</span></em></span></span></li>
	<li><span style="font-family:verdana,geneva,sans-serif;"><span style="color: rgb(105, 105, 105);"><em><span style="font-size: 14px;">Realize that you&rsquo;re too late to complete the decorations, heck.. you haven&rsquo;t even started it.</span></em></span></span></li>
</ol>

<p><span style="font-family:verdana,geneva,sans-serif;"><span style="color: rgb(105, 105, 105);"><span style="font-size: 14px;">Now, with a event driven - non blocking approach</span></span></span></p>

<ol>
	<li><span style="font-family:verdana,geneva,sans-serif;"><span style="color: rgb(105, 105, 105);"><em><span style="font-size: 14px;">Call cake shop and tell them to deliver it as it&rsquo;s made.</span></em></span></span></li>
	<li><span style="font-family:verdana,geneva,sans-serif;"><span style="color: rgb(105, 105, 105);"><em><span style="font-size: 14px;">Proceed for decorations.</span></em></span></span></li>
	<li><span style="font-family:verdana,geneva,sans-serif;"><span style="color: rgb(105, 105, 105);"><em><span style="font-size: 14px;">Complete decorations, and realize that you still have some time to play Tetris.</span></em></span></span></li>
	<li><span style="font-family:verdana,geneva,sans-serif;"><span style="color: rgb(105, 105, 105);"><em><span style="font-size: 14px;">Cake arrives.</span></em></span></span></li>
</ol>

<p><span style="font-family:verdana,geneva,sans-serif;"><span style="color: rgb(105, 105, 105);"><span style="font-size: 14px;">The power of this approach is that you are always ready to proceed for the next task, and that is where node.js excels. You just don&rsquo;t wait, and proceed to take the next task. There is a lot about node.js awesomeness online.. http://lmgtfy.com/?q=why+should+i+use+node.js</span></span></span></p>

<p><span style="font-family:verdana,geneva,sans-serif;"><span style="color: rgb(105, 105, 105);"><span style="font-size: 14px;">Now, what node.js is often confused with is, it being a magic pill for all sorts of web problems. There are scenarios where one should really avoid node.js.</span></span></span></p>

<p><span style="font-family:verdana,geneva,sans-serif;"><span style="color: rgb(105, 105, 105);"><span style="font-size: 14px;">Node.js is single threaded, What node.js does is, it has non-blocking I/O calls, which simply means, throw in a request and it will just send the task to be completed, and instead of waiting for it to be completed, it will just proceed to take care of next request. When the task gets completed, it will return with a response to the server. Now here is a catch, let&rsquo;s say I write a logic, that after a database record is fetched, proceed with some computation work.Now, a special request comes in which leads to some real heavy computation, Since node.js is single threaded, eventually after the database call it will get busy with the computation work, all further requests will be just kept waiting and the server will seem like not responding at all as our only main process is busy solving some complex sums.</span></span></span></p>

<p><span style="font-family:verdana,geneva,sans-serif;"><span style="color: rgb(105, 105, 105);"><span style="font-size: 14px;">For a person with java or similar background, when we talk about handling concurrent connection, say jsps and servlets on a tomcat server, we have a thread pool to handle concurrent connection. The above mentioned scenario of node.js being stuck is easily taken care of in this case of multiple threads. What get&rsquo;s busy with computation here is one thread, and rest of the threads are available to serve further requests.</span></span></span></p>

<p><span style="font-family:verdana,geneva,sans-serif;"><span style="color: rgb(105, 105, 105);"><span style="font-size: 14px;">With the right implementation and the case, node.js provides a really fast lightweight solution which is just easy to implement. It is far less time consuming to code IF you know what you&rsquo;re doing.</span></span></span></p>

<p><span style="font-family:verdana,geneva,sans-serif;"><span style="font-size: 14px;"><span style="color: rgb(105, 105, 105);">Suggested Read : </span><a href="http://www.manning.com/cantelon/"><span>Node.JS in Action</span></a></span></span></p>
</div>

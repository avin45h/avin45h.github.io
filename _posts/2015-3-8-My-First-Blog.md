---
layout: post
title: My First Blog
comments: true
---
#Node.js  
<h6>(a Java developer's simple view)</h6>
---
Around an year back, I shifted to node.js. My career since beginning has been mostly about Java. After programming around traditional java-isque apps since like 4 years, node.js intrigued me. And that is when I took the leap to checkout what is the node.js hype about. 

Node.JS is an awesome runtime which let's you write server/network logic using javascript, utilizing the event driven paradigm and is non blocking, which just basically means that you write the logic for some event, and specify what should happen after the event is complete and just proceed with next steps of your server side logic.

An analogy of this would be a birthday party planning. You're planning a birthday, you call up a cake shop, tell them that you want a cake , and as the cake is done, deliver it at a certain address with a nice greeting card. After telling them up, you just proceed to manage decorations for party and further work and so on.

If I were to plan this party using traditional design, this would be something like this (Considering I didn't make threads) :

 - Call cake shop
 - Wait for the cake to be made.
 - Wait for the delivery.
 - Realize that you're too late to complete the decorations, heck.. you haven't even started it.

Now, with a event driven - non blocking approach

 - Call cake shop and tell them to deliver it as it's made.
 - Proceed for decorations.
 - Complete decorations, and realize that you still have some time to play Tetris.
 - Cake arrives.

The power of this approach is that you are always ready to proceed for the next task, and that is where node.js excels. You just don't wait, and proceed to take the next task. There is a lot about node.js awesomeness online..   http://lmgtfy.com/?q=why+should+i+use+node.js

Now, what node.js is often confused with is, it being a magic pill for all sorts of web problems. There are scenarios where one should really avoid node.js.

Node.js is single threaded, What node.js does is, it has non-blocking I/O calls, which simply means, throw in a request and it will just send the task to be completed, and instead of waiting for it to be completed, it will just proceed to take care of next request. When the task gets completed, it will return with a response to the server. Now here is a catch, let's say I write a logic, that after a database record is fetched, proceed with some computation work.Now, a special request comes in which leads to some real heavy computation, Since node.js is single threaded, eventually after the database call it will get busy with the computation work, all further requests will be just kept waiting and the server will seem like not responding at all as our only main process is busy solving some complex sums.

For a person with java or similar background, when we talk about handling concurrent connection, say jsps and servlets on a tomcat server, we have a thread pool to handle concurrent connection. The above mentioned scenario of node.js being stuck is easily taken care of in this case of multiple threads. What get's busy with computation here is one thread, and rest of the threads are available to serve further requests.

With the right implementation and the case, node.js provides a really fast lightweight solution which is just easy to implement. It is far less time consuming to code IF you know what you're doing.

Suggested Read : Node.JS in Action, http://www.manning.com/cantelon/

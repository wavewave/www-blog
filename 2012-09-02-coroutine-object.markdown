---
title: coroutines as objects
author: Ian-Woo Kim
date: September 2, 2012
--- 

Why needed?
--------------------

GUI programming and modern programming enjoys asynchrous event handling. 
Haskell can certainly do that, but with purity, it's a little messy. 
Therefore, many people have thought about Functional Reactive Programming 
(FRP). FRP is a great idea but it's not completed yet and hard to incorporate 
with conventional imperative programming. 

State capturing in pure functional programming language can be traditionaly 
done with closure. Javascript community uses this technique to realize 
OOP in javascript. In haskell, this can be also done very elegantly with 
state monad. 

Asynchronous event handling needs some callback function
which easily leads to nested function call. Nested function call is very hard 
to abstract business logic out and cumbersome to write anyway. 

Coroutine can nicely give an additional abstract layer which separate 
business logic from IO layer. It's nothing but a free monad transformer or 
delimited continuation. 


take some benefit from object oriented programming without sacrificing purity at all. That's coroutine / continuation / state monad / monad transformer


* queue/logger is done with flushing mechanism. 

* lens, coroutine, state monad (closure), free monad. 

* all these efforts culminated into <code>coroutine-object</code> package


Design Principle 
----------------
 
State-carrying virtual world consists of <code>meta-world</code> and <code>world</code>
<code>meta-world</code> has driver and logger and ioactor, and <code>world</code> has 
world. world carries a state. Only <code>driver</code> has a unique input channel from
IO monad from event handler. <code>ioactor</code> can deal with IO action which can 
give a feedback from IO world through <code>driver</code>. <code>logger</code> is for 
maintenance purpose. World can have state and actors. Each actor should access world
state using lens. World can have temporary event queue and temporary log channel which 
will be flushed into logger and driver. Driver will get feedback event from world 
and sequentially reactivate those events.


Library dependency 
----------------- 

* <code>transformers-free</code> : FreeT monad transformer
* <code>lens</code> : lens is a collection of all the efforts 

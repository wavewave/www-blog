---
title: A Short Note of Hoodle Development 
tags: hoodle, development, haskell 
---

_The following is my original statement on hoodle development posted on [http://ianwookim.org/hoodle](http://ianwookim.org/hoodle) for some time._ 

I was a long-time user of <code>xournal</code> and contributed some code 
to the <code>xournal</code> project myself. The <code>xournal</code> program 
is excellent and fulfils my need much for jotting notes,  calculating with a pen 
and annotating papers in pdf format. However, as all the software in the world,
it needs to be improved. For example, we need more optimal effecient use of 
small tablet PC screen.  It is also very desirable to have a script for a program.
On the other hand, <code>xournal</code> is already a stable mature program and 
has lots of users.
It seems rather difficult to experiment such interesting features in 
the <code>xournal</code> project for me. <code>xournal</code> is written in C, 
which needs great care for maintaining code safely.  
When I implemented a lasso selection feature for <code>xournal</code> 
(it is included as of <code>xournal-0.4.7</code>), I found that the internal 
design should be significantly changed for adding a small interesting feature.
In addition, <code>xournal</code> is
based on GNOME canvas UI widget, which is one of soon-to-be-deprecated components 
of the GNOME project.
This led me to think about writing a new note-taking program from scratch. 

When I envisioned what the new "xournal" look like, I came up with the idea of "emacs"
 of pen note-taking program. Without doubt, <code>emacs</code> is one of the most
successful long-lived text editor software. The frame/window/buffer architecture
of <code>emacs</code> turned out very flexible accommodating many interesting 
ideas. Elisp, the LISP language used for <code>emacs</code> scripting, is a very 
useful machinery for extending and empowering <code>emacs</code>, sometimes very unexpectedly. 
Such extensibility is in part originated from the fact that 
ELisp is a functional programming language. By putting a function as a first-class
citizen of the language, modularity in design is achievable more easily in functional 
programming languages. Thus, I seriously considered a functional programming language 
as a main language for the development. 

So I have chosen haskell for the language. Haskell is a statically typed *pure* 
functional programming language. The language is very clear, concise and elegant.
The functional purity, which means that a function in haskell is really a function without 
side effects, shows a great power in concurrent and parallel programming. 
The haskell community is rapidly growing and so the library space in haskell is now 
filled with increasing flow of contributions.  
Although Graphical User Interface (GUI) programming in haskell is still new and not 
very common, it turned out that we have enough useful libraries for this development.
In fact, the haskell community is now seeking for totally new revolutionary directions 
of GUI programming, so-called *functional reactive programming (FRP)*. 
(However, in this project, I do not consider switching to FRP paradigm yet.) 

Since November 2011, I started the development under the name of 
<a href="http://ianwookim.org/hxournal"><code>hxournal</code></a>. The name honors 
the <code>xournal</code> project. Now, after some discussion about the name in 
online community, I decided to change the name to "hoodle" where "h" comes from haskell 
and "oodle" is in a sense of doodle. The progress has been impressively fast owing to 
the productivity of the language. <code>hoodle</code> has only 10k lines of codes,
which is significantly smaller than <code>xournal</code> and almost 1/5 of <code>xournalpp</code>
(New C++ version of <code>xournal</code> from scratch). As of Dec 2012, it has a baby 
scripting feature. The scripting feature will provide a similar path to <code>emacs</code> 
for community-contributed development.  

_This is it. I will refine my statement on <code>hoodle</code> development and keep it up-to-date in this blog._

---
title: poppler 0.12.3 released 
tags: poppler, haskell
---

A new version of haskell poppler library is now released. 
Recently, [gtk2hs-0.12.5](http://projects.haskell.org/gtk2hs/archives/2013/12/03/new-gtk2hs-0125-release) was released and we now have support to 
[gtk3](http://hackage.haskell.org/package/gtk3). We also have a great advance of [Cabal-1.18](http://coldwa.st/e/blog/2013-08-21-Cabal-1-18.html), but previous 
version of poppler was not buildable with the new Cabal.
So this version (0.12.3) of poppler is to support gtk2hs-0.12.5 and Cabal-1.18.
By default, poppler is compiled against gtk version 2, but with -fgtk3 option, 
one can build poppler with gtk3. 

Enjoy!



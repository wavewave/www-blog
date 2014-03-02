---
title: The first public release of fficxx 
tags: fficxx, haskell, FFI, binding, C++  
---

Hello!

I am very happy to announce the first version of fficxx ([http://ianwookim.org/fficxx](http://ianwookim.org/fficxx), also, see [http://github.com/wavewave/fficxx](http://github.com/wavewave/fficxx))

`fficxx` is a haskell Foreign Function Interface (FFI) generator to C++. This tool automatically generates 
haskell FFI package for a given C++ class structure. It has been used for generating my haskell binding to [ROOT](http://root.cern.ch) library called [HROOT](http://ianwookim.org/HROOT). Now I made it as a separate tool to benefit everyone trying to make a haskell-C++ binding. 

I am going to explain how to use the library/tool one by one in this blog. In the package, I provide a very simple sample in the `sample` directory of the `fficxx` cabal package. 

If interested, please try this and give me some comments on it in the [discussion mailing list](http://ianwookim.org/fficxx/discuss.html)




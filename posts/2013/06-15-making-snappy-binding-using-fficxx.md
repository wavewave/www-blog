---
title: Make a binding to snappy using fficxx 
tags: fficxx, haskell, FFI, binding, C++  
---
**Disclaimer:** _fficxx is at a very early stage and now under heavy development and hence subject to many changes. This article can be easily outdated when newer versions come. Please refer to [the fficxx main homepage](http://ianwookim.org/fficxx)._

This is the first article of the series I am planning to talk about how to use fficxx for generating haskell-C++ binding and how to use the generated library. 

So what is fficxx?
======================

Foreign Function Interface (FFI) to C++ library in haskell is notoriously hard. fficxx is a tool for doing the job for you. The goal of fficxx is to weaken the difficulties in making haskell-C++ binding and to provide relatively nice mapping between two completely different paradigm of programming. It automatically generates necessary boilerplate codes in several levels: C++-C shims, C-haskell FFI, low level haskell type representation for C++ class/object and high level haskell type and typeclass representation and some casting functions. The generated codes are organized into proper haskell modules to minimize name space collision and packaged up as cabal packages. The tool is designed to adapt different configurations and unique needs, such as splitting bindings into multiple cabal packages and renaming classes and functions to resolve some obstacles resulting from naming collision, which is quite inevitable in making FFI. FFI generation is done by providing the information of the C++ library in terms of quite simple haskell Embedded Domain Specific Language (EDSL), aiming at good usability for ordinary haskell users.  

In this series of article, I will explain how to use fficxx and generated library and the underlying principles for this tool through some examples. As for some *real world* example, there is [HROOT](http://ianwookim.org/HROOT): a binding to the ROOT framework. In fact, fficxx is a byproduct of the HROOT project. Since HROOT is too large for showing how to use this, I first chose a C++ library called "[snappy](http://code.google.com/p/snappy)", a simple performant compression/decompression library for the purpose of illustration[1].

The Snappy Library
==================

Snappy is a compression/decompression library. On my Arch Linux system, the library could be installed from Arch Linux official repository (`extra/snappy`). Once installed, the header files, `snappy.h` and `snappy-sinksource.h`, for snappy should be present in the usual place, for example, `/usr/include`. From now on, I assume that those header files are located in the system include path, and the library binaries, `libsnappy.a` and `libsnappy.so` are also in the system library path. This is an assumption of the simplest code generator `simpleBuilder` in fficxx[2].  


[1] I thank Carter for suggesting this.

[2] I will explain more customizable options, for example, using `pkg-config`, in other blog posts.




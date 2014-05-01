---
title: Make a binding to snappy using fficxx 
tags: fficxx, haskell, FFI, binding, C++  
date: 2013-06-15
---
**Disclaimer:** _fficxx is at a very early stage and now under heavy development and hence subject to many changes. This article can be easily outdated when newer versions come. Please refer to [the fficxx main homepage](http://ianwookim.org/fficxx)._

This is the first article of the series I am planning to talk about how to use fficxx for generating haskell-C++ binding and how to use the generated library. 

So what is fficxx?
------------------

Foreign Function Interface (FFI) to C++ library in haskell is notoriously hard. fficxx is a tool for doing the job for you. The goal of fficxx is to weaken the difficulties in making haskell-C++ binding and to provide relatively nice mapping between two completely different paradigm of programming. It automatically generates necessary boilerplate codes in several levels: C++-C shims, C-haskell FFI, low level haskell type representation for C++ class/object and high level haskell type and typeclass representation and some casting functions. The generated codes are organized into proper haskell modules to minimize name space collision and packaged up as cabal packages. The tool is designed to adapt different configurations and unique needs, such as splitting bindings into multiple cabal packages and renaming classes and functions to resolve some obstacles that are originated from naming collision, which is quite inevitable in making an FFI library. FFI generation is done by providing the information of the C++ library in terms of quite simple haskell Embedded Domain Specific Language (EDSL), aiming at good usability for ordinary haskell users.  

In this series of article, I will explain how to use fficxx and generated library and the underlying principles for this tool through some examples. As for some *real world* example, there is [HROOT](http://ianwookim.org/HROOT): a binding to the ROOT framework. In fact, fficxx is a byproduct of the HROOT project. Since HROOT is too large for showing how to use this, I first chose the [snappy](http://code.google.com/p/snappy) library for the purpose of illustration[1].

The Snappy Library
------------------

Snappy is a simple efficient compression/decompression library. It is written in C++, but it also provides C API, and using C API, many bindings to snappy for many other languages exist, including haskell (snappy on Hackage [cite]). However, we are going to make a binding to the C++ interface of snappy using fficxx only without resort to the C API. 
 
The installation of snappy library is easy in most linux distributions, windows and Mac OS X. 
For instance, on my Arch Linux system, the library could be installed from Arch Linux official repository (`extra/snappy`). Once installed, the header files, `snappy.h` and `snappy-sinksource.h`, for snappy should be present in the usual place, again in my case, `/usr/include`. From now on, I assume that those header files are located in the system include path, and the library binaries, `libsnappy.a` and `libsnappy.so` are also in the system library path. This is an assumption of the simplest code generator `simpleBuilder` in fficxx[2].  

In snappy library, we have two basic base classes: `Source` and `Sink`. There are a subclass `ByteArraySource` of `Source`, and a subclass `UncheckedByteArraySink` of `Sink`. The class `Source` and the class `Sink` define several virtual member functions, such as `GetAppendBuffer` of `Source` or `Available` of`Sink`, and the subclasses inherit them and also introduce new member functions as usual, for example, `Peek` of in `ByteArraySource`, `CurrentDestination` of `UncheckedByteArraySink`. This library also provides several _top-level_ functions, i.e. functions that are not defined as a member of a class. Some exmaples are `Compress` and `Uncompress`. What these member functions and top-level functions are intended for are quite clear by what their names suggest. I summarize the public interface of the snappy library in Fig. XXX. 

FIGURE XXX

Represent C++ interface    
--------------

fficxx should take a C++ interface data as an input for the code generation. Although it is ambitiously planned to have an automatic C++ parser for obtaining the interface data from C++ header files, such a luxurious machinary is not available as of now. Rather, we represent the interface information as simple haskell data structure.  









[1] I thank Carter for suggesting this.

[2] I will explain more customizable options, for example, using `pkg-config`, in other blog posts.




---
title: hoodle 0.4 released 
tags: hoodle, haskell
date: 2015-02-27
---

Yesterday, I released hoodle 0.4!

The major change in this update is tabbed interface! Like modern web browsers, you can open multiple hoodle files in one hoodle window and navigate them using tabs.

Internally, I improved its rendering engine quite much. Now it has a fully asynchronous renderer, which enables a faster change of zoom ratio using cached image and then update rendering later more precisely. This improves display performance from user's point of view a lot.

I also made a support for synchronisation and shared documents in association with a web service which I am now preparing for. By default, it is turned off, so all network-related dependencies for that will not be required unless turned on by -fhub flag. In addition, I also made dyre (dynamic reloading as xmonad and yi) opt-in, so you need to use -fdyre if you want to have the feature.
Now hoodle is being migrated to gtk3 though this version will not support gtk3 fully yet. I plan to migrate hoodle to gtk3 fully and use gtk3 exclusively in the next version, so this version will be the last gtk2 version. Once this is done, a multi-touch support will be enabled. (and also hoodle will be able to live in wayland, too!)

Enjoy hoodle!


---
title: Blog synchronization with hexo and git
date: 2019-12-27 17:40:58
tags:
description: Recently I upgraded my laptop from Thinkpad T440s to T480s. This note is intended to describe the method of updating the blog pages across multiple machines with hexo and git. The basic idea is to store the source files in a separate branch and store everything in a git repository.
---

A good [reference](https://juejin.im/post/5acf22e6f265da23994eeac9) about the steps.

* Git clone the hexo branch

* Install `Git`, `Node.js`

* `npm install`

* Install  hexo `npm install -g hexo-cli` 

* Done!

  Problem: No layout after `hexo clean` and `hexo g`. The theme file is empty. Git clone the theme again.
* After any change locally, `Git push` to synchronize any changes.
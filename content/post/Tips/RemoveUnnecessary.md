---
title: "How to remove unnecessary packages from Ubuntu ?"
description: "Clean Ubuntu "
date: 2018-01-18T19:53:57+05:30
draft: false

---

We will learn to remove unnecessary packages from the Ubuntu system.

<!--more-->

In order to save space or to make your system work faster, you can do following steps you can use following tricks

1. Remove all packages which got installed to satisfy dependency and now no more needed.

    sudo apt-get autoremove

2. Remove all packages which are downloaded for installation

    sudo apt-get clean

3. Remove files which can’t be downloaded or they are now useless.

    sudo apt-get autoclean

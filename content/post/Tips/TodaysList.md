---
title: "Display todays files in Ubuntu "
description: "Display todays files in Ubuntu"
date: 2018-01-18T19:53:57+05:30
draft: false

---

Trick to display list of all files which are created today.

<!--more-->

If you want to get list all files which you have created today then use following command

    ls -al –time-style=+%D | grep `date +%D`


Option - Description

  1. l	- Long listing of files
  2. a	- all files including hidden files
  3. –time-style - Time display style
  4. grep	- to find files only from given date
  5. date	- to find todays date and then it gets substituted in grep

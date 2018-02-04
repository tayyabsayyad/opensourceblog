---
title: "Finding big files in terminal"
date: 2018-01-18T19:53:57+05:30
draft: false

---

Trick to list all big files in order using ls command.

<!--more-->

You might often come across a situation where you want to find biggest files to delete to free space in your drives or home directory. I found this trick on

 http://www.tuxradar.com/content/linux-tips-every-geek-should-know

Use following command to find big files in sorted order by size.

    ls -lSrh


    It works as follows

    Option	Meaning
    l	- Long listing of files
    S	- Sort by file size largest first
    r	- Sorting list in reverse order
    h	- Human Readable File Size
    If you want big file to appear first remove ‘r’ option

    You can also append listing criteria for specific files

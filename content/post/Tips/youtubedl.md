---
title: "Youtube-dl"
description: "sharing a small trick on how to download a video from youtube using a command line tool youtube-dl"
date: 2018-01-18T19:53:57+05:30
draft: false

---
In this post we will learn easy way to download youtube videos and play lists.
<!--more-->

Hi all, Just sharing a small trick on how to download a video from youtube using a command line tool youtube-dl.

You can find the entire documentation of this tool here https://rg3.github.io/youtube-dl/

Install using following command

    sudo apt-get install youtube-dl

Once you install you can download videos using

    youtube-dl link

Example lets download one of my favourite video

    youtube-dl https://www.youtube.com/watch?v=lSRYCc7ApHc&amp;index=42&amp;list=PL-bTaZrTDhtbhxgS59t4HzwCnq2iIYMgV

You can also download multiple videos from the playlist as follows

    youtube-dl -ci play-list-url


To can also you the Youtube-dl tool behind the proxy as follows,

    youtube-dl --proxy  http://username:password@proxy-server:port https://www.youtube.com/watch?v=VcoVYfDVEww

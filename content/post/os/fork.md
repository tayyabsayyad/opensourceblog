
---
title: "Fork System Call"
date: 2018-02-09
draft: false
tags: ["os"]
keywords: fork, os
---

In this post we will learn to how fork system call works with example program.

<!--more-->

Fork is a system call used in the Linux to create a new process. Some of the important points about the fork is as follows.

*  When you call fork system call, it creates a copy of the process from the point onwards where it is called
* The newly created process is called as <b>Child process</b> where as the process who created it is called <b>Parent Process</b>
* Every process has its own process id so even child process has its own <b>Process id.</b>
* Parent and Child Process runs concurently and scheduled independetly by operating system.


Fork Example in c :

{{< highlight c "linenos=table,hl_lines=11 13" >}}

    #include  <stdio.h>
    #include  <sys/types.h>
    #define COUNT  200

    void  ChildProcess(void);                
    void  ParentProcess(void);               

    void  main(void)
    {
     pid_t  pid;
     pid = fork();

     if (pid == 0)
          ChildProcess();  
     else
          ParentProcess();
    }

    void  ChildProcess(void)
    {
      int i;
      for (i = 1; i <= COUNT; i++)
          printf("From child, value = %d\n", i);
     printf(" -------- Child Process Finished ---------- \n");
    }

    void  ParentProcess(void){
     int i;
     for (i = 1; i <= COUNT; i++)
          printf("From parent, value = %d\n", i);
     printf("-------- Parent Process Finished --------\n");
    }
{{< / highlight >}}


Output :

      tayyabali:c$ ./fork7             
      From parent, value = 1
      From parent, value = 2
      From parent, value = 3
      From parent, value = 4
      From parent, value = 5
      From parent, value = 6
      From parent, value = 7
      From parent, value = 8
      From parent, value = 9
      From parent, value = 10
      From parent, value = 11
      From child, value = 1
      From parent, value = 12
      From parent, value = 13
      From child, value = 2
      From parent, value = 14
      From child, value = 3
      From child, value = 4
      From parent, value = 15
      From child, value = 5
      From child, value = 6
      From parent, value = 16
      From child, value = 7
      From parent, value = 17
      From child, value = 8
      From child, value = 9
      -----------Ommited Output -------
      From child, value = 195
      From child, value = 196
      From child, value = 197
      From child, value = 198
      From child, value = 199
      From child, value = 200
      -------- Child Process Finished ----------
      From parent, value = 43
      From parent, value = 44
      From parent, value = 45
      -----------Ommited Output -------
      From parent, value = 195
      From parent, value = 196
      From parent, value = 197
      From parent, value = 198
      From parent, value = 199
      From parent, value = 200
      -------- Parent Process Finished --------



In the above program we have two functions ChildProcess and ParentProcess

* We create child process using fork() call on line no 11
* If fork call is sucessful it returns 0.
* If pid is 0 we call ChildProcess else we call ParentProcess function.
* Child and Parent processes run independetly and print count upto 200
* Child and parent will even have seprate copy of variables if we have any.
* Parent or Child any process can finish first depending on the CPU scheduling algorithm

### getpid and getppid methods

<b>getpid </b> : Returns the process ID of the calling process.

<b> getppid </b>: Returns the process ID of the parent of the calling process

Lets see how this works in the following program

{{< highlight c "hl_lines=" >}}
    #include  <stdio.h>
    #include  <sys/types.h>
    #define COUNT  200

    void  ChildProcess(void);                
    void  ParentProcess(void);               

    void main(void)
        {
         pid_t  pid;
         pid = fork();

         if (pid == 0)
              ChildProcess();  
         else
              ParentProcess();
        }

    void ChildProcess(void)
        {
          printf("Child Executes : Child Process id  : %d.\n",getpid());
          printf("Child Executes : Parent Process id : %d.\n",getppid());
        }

    void ParentProcess(void){
         printf("Parent Executes : Process id  : %d.\n",getpid());
         printf("Parent Executes : Parents Parent pid : %d.\n",getppid());
        }

        {{< / highlight >}}

Output :

        tayyabali:c$ ./fork9
        Parent Executes : Process id  : 11437.
        Parent Executes : Parents Parent pid : 9660.
        Child Executes : Child Process id  : 11438.
        Child Executes : Parent Process id : 11437.

When we see details of process 9660 we get as following

    tayyabali:c$ ps aux | grep 9660
    tayyaba+  9660  0.0  0.0  22968  5236 pts/2    Ss   20:38   0:00 /bin/bash

So as you can see the our parent's parent process is started by the /bin/bash by user tayyabali

We can see the relationship between all these processes is as follows

<b> (Parent's Parent 9660 )  --- > ( Parent 11437 ) --- > ( Child 11438 ) </b>

---
title: "Set Java Home in Ubuntu"
description: "Set Java Home "
date: 2018-01-18T19:53:57+05:30
draft: false

---
Open terminal and open file /etc/profile

    $sudo gedit /etc/profile

Copy your Java Home location as it can be in your home folder of open jdk

JAVA_HOME=”/home/tayyabali/jdk1.8.0_31/bin” or JAVA_HOME=”/usr/lib/jvm/open-jdk”

Append the home entry as following in the “profile file” following

    export JAVA_HOME=$JAVA_HOME:/home/tayyabali/jdk1.8.0_31/bin

Use source command to load the variables, by running this command:

    source /etc/environment

Then check the variable, by running this command:

    echo $JAVA_HOME

---
layout: post
category: "java"
title:  "String, StringBuilder, StringBuffer"
tags: [java]
excerpt: "compare"
---


### String vs StringBuilder and StringBuffer
>String is immutable. StringBuilder and StringBuffer is multable   

**Meaning of multable:** A multable object is the object that can modify value. A immutable object is the object that can not modify value.
Immutable means can't change the value of the same reference. Every time, we want to change it data, we need to reference to a new memory location.   
Example
```
String str = "abc"; // "abc" will created in memory and str will reference to "abc" 
str = "def"; // "def" will created in memory and str will reference to "def". "def" don't replace "abc"
```
### StringBuilder vs StringBuffer
>StringBuffer is synchronized, StringBuilder is not synchronized  

**Meaning of synchronized (synchronization):** When some thing is synchronized, many thread can access to it without any problem.
Then we will think that StringBuffer is better but note that we shouldn't use StringBuffer if it is unnecessarily, don't use it if only one thread is modifying and accessing it because it has lot of locking and unlocking code for synchronization which will unnecessarily take up CPU time. 
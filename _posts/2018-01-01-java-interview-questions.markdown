---
layout: post
category: "java"
title:  "Java interview questions"
tags: [java]
excerpt: "compare"
---

### HashMap vs Hashtable
Two different 
- `Hashtable` is **synchronized**, `HashMap` is not
- `Hashtable` **does not** allow **null** keys or values, `HashMap` **does**

Note: **Should not** use `Hashtable` for multiple threads application even it **synchronized** because `Hashtable` use synchronized for all methods (it's not good for performance (check `Hashtable` code for more detail)). For multiple threads application, you can use `ConcurrentHashMap`.  
Reference: https://stackoverflow.com/questions/40471/differences-between-hashmap-and-hashtable
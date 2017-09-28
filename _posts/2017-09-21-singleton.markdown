---
layout: post
category: "read"
title:  "Serializable and Parcelable?"
tags: [android,java]
excerpt: "compare"
---

### What is the different between Serializable and Parcelable ?
Serializable is a standard Java interface. You simply mark a class Serializable by implementing the interface, and Java will automatically serialize it in certain situations.  
Parcelable is an Android specific interface where you implement the serialization yourself. It was created to be far more efficient than Serializable, and to get around some problems with the default Java serialization scheme.  
(according to <https://stackoverflow.com/a/3323554/5381331>) 

### What is better ?

If you want to be a good citizen, take the extra time to implement Parcelable since it will perform 10 times faster and use less resources.
However, in most cases, the slowness of Serializable won’ t be noticeable.Feel free to use it but remember that serialization is an expensive operation so keep it to a minimum.  
If you are trying to pass a list with thousands of serialized objects, it is possible that the whole process will take more than a second.It can make transitions or rotation from portrait to lanscape feel very sluggish.  
(according to <https://stackoverflow.com/a/22350463/5381331>)  

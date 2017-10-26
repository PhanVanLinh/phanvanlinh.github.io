---
layout: post
category: "android"
title:  "Android memory"
tags: [android]
excerpt: "android memory"
---

####  Get available memory
https://stackoverflow.com/a/10747242/5381331
```
MemoryInfo mi = new MemoryInfo();
ActivityManager activityManager = (ActivityManager) getSystemService(ACTIVITY_SERVICE);
activityManager.getMemoryInfo(mi);
double availableMegs = mi.availMem / 0x100000L;

//Percentage can be calculated for API 16+
double percentAvail = mi.availMem / (double)mi.totalMem * 100.0;
```

#### When device run out internal storage
`Caused by: android.system.ErrnoException: write failed: ENOSPC (No space left on device)`

#### Some link need to read
http://www.techpaste.com/2012/07/steps-debugdiagnose-memory-memory-leaks-jvm/

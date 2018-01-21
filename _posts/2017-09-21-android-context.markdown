---
layout: post
category: "android"
title:  "Android Context"
tags: [android]
excerpt: "principle"
---

### Defining
Application Context: This context is tied to the lifecycle of an application
Activity Context: This context is tied to the life cycle of an activity

### Allow using Context

| |  Application|  Activity | Service| ContentProvider| BroadcastReceiver|
|--|--|--|--|--|--|
Show Dialog| NO  | YES | NO | NO | NO|
Start an Activity| NO (YES if we use flag NEW_TASK)  | YES | NO | NO | NO|
Layout Inflation| NO  | YES | NO | NO | NO|
Start a Service| YES | YES | YES | YES | YES |
Bind to Service| YES | YES | YES | YES | NO|
Send Broadcast| YES | YES | YES | YES | YES |
Register Broadcast Receiver| YES | YES | YES | YES | NO|
Load Resource Values| YES | YES | YES | YES | YES |

### Good using

| |  Application|  Activity | 
|--|--|--|
Create Singleton object which require a `Context`| **Should use**. Because  if we use **ActivityContext** here, the Singleton object will keep the reference to activity and the activity **will not** be garbage collected => memory leak| **Shouldn't use** | 
|Use a object in Library which require a `Context`|**Should use**|**Shouldn't use**|
|Do some thing with GUI|**Almost can not do**, it will return WindowManager$BadTokenException: Unable to add window -- token null is not for an application. It is not complete `Context` that supporting everything that Activity does|--|
|Show Toast| **Same**, Currently I think we can use `ApplicationContext` or `ActivityContext` because no document say which is better but I think we should use `ActivityContext` because some good developer say only use `ApplicationContext` when we really need it (https://stackoverflow.com/a/5228494/5381331) some post say `ApplicationContext` may crash in some few device(https://stackoverflow.com/a/36032279/5381331) and some developer say Toast is is UI so we should use `ActivityContext` (however in some case we show Toast outside of Activity so we need `ApplicationContext`). Conclusion, feel free to use both of theme is same  |**Same**| 
|Load resource|The same with Toast|The same with Toast|
|Normal object which require a `Context` (tied with Activity life cycle) |**Shouldn't use** because it simple **not necessary and suitable**|**Should use**|


### Context returned
`MainActivity.this` -> return **Activity** context  
`getBaseContext()` -> return **Activity** context  
`getApplicationContext` -> return **Application** context  


### Reference

https://stackoverflow.com/a/7298955/5381331
https://stackoverflow.com/a/5228494/5381331
https://possiblemobile.com/2013/06/context/
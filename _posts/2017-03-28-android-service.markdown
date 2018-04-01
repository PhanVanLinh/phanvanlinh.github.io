---
layout: post
category: "android"
title:  "Android service"
tags: [android]
excerpt: "android service"
---

# AndroidService

### Thread
1) Service is run on **MAIN thread** so if we want to execute heavy task we need to create a worker thread for execute it to prevent `Android Not Responding`.  
2) The  `onHandleIntent` inside `Intent Service` run on `worker thread`

### Type of Service

| Unbound Service | Bound Service | Intent Service   |
| :------- | ----: | :---: |
| Use to make a task for **long time** and **repeat**. | Like client(`eg: a screen`)-server (`Service`) model, client bind to server, server execute task and notify data to client. |  Use to execute task in **worker** thread (inside [onHandleIntent](https://developer.android.com/reference/android/app/IntentService.html#onHandleIntent(android.content.Intent)) method). It quite same `AsyncTask` [my answer here](https://stackoverflow.com/a/49585912/5381331)|
|start by `startService()`.| start by `bindService()`.|start by `startService()`. When start service, we will also send the intent (with data) to service. Then service will receive data and execute corresponding task. If we send multiple task durring service running, service will execute it sequentially synchronize (thread safe) |
|stop by `stopService()`.| stop when no client by to this Service . Client unbind service by `unbindService()`.|  Auto stop when the task inside `onHandleIntent` execute **finished**, or we can use `stopself()`|
|**INDEPENDENT** with the component started it.| **DEPENDENT** with the component started it.| **INDEPENDENT** with the component started it.  |

### Use Unbound Service or Intent Service
Look like `Unbound Service` and `Intent Service` have many thing similar however it have some different like
- `Unbound Service` don't auto stop, `Intent Service` have
- `Intent Service` have a available method run on worker thread (`onHandleIntent`), `Unbound Service` don't have  

=> `Unbound Service` is suitable for running some **long** and **repeat** task . `Intent Service` is suitable for run some **less longer** and **less repeat** task.

### Strangely
- If we want service keep running after application is destroyed, we need to use flag `START_STICKY`.  Then when application is destroyed, service will destroyed too, then it will recreated. However, for some specific device, `Service` will not restart (because the manufacture want to save the device battery)  (more details)(https://stackoverflow.com/questions/41627537/)service-not-start-again-after-kill-app-even-use-start-sticky-in-some-device

- When bind service, if use use flag 0 instead of `BIND_AUTO_CREATE`, service will not created. After that, when we start service programmatically by call `startService`, all the client that bind to service before will auto bind to service

### Note
- In many app, I often mix `Unbound Service` and `Bind Service` together


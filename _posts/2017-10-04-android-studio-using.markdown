---
layout: post
category: "android"
title:  "Android Studio Using"
tags: [android]
excerpt: "strangely"
---

### Get SHA1  
Simplest way is: Create new `MapApplication` then get `SHA-1 certificate fingerprint` inside `google_maps_api.xml` file

### Generate keyhash  
Follow https://www.youtube.com/watch?v=LUv8NDgu2Xk
`keytool -exportcert -alias androiddebugkey -keystore %HOMEPATH%\.android\debug.keystore | openssl sha1 -binary | openssl base64`
Step 1: `cd` to folder `Java\jre...\bin`  
Step 2: Replace `openssl` by `C:\openssl\bin\openssl`. If we don't have `openssl`, simply go to internet->download->extract.  
Step 3: Run command (like the below example)  
`keytool -exportcert -alias androiddebugkey -keystore %HOMEPATH%\.android\debug.keystore | C:\openssl\bin\openssl sha1 -binary | C:\openssl\bin\openssl base64`
Step 4 : Enter password (using empty password by enter)  
Bước 5: Done  

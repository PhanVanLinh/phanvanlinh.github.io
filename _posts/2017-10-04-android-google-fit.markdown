---
layout: post
category: "android"
title:  "Android Strangely"
tags: [android]
excerpt: "strangely"
---

### WebView
***Load html string content***
`webView.loadDataWithBaseURL(null, "<html><body><pre>line 1\nline 2</pre></body></html>", "text/html", "UTF-8", null);`  
Note: we should use `loadDataWithBaseURL` instead because `loadData` don't handle next line `(\n) `
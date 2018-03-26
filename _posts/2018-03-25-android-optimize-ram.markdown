---
layout: post
category: "android"
title:  "Android Optimize Ram"
tags: [android]
excerpt: "optimization"
---


## Android Optimize RAM

### I) Don't put image in drawable files
Put it inside each `drawable-...dpi` folders.
The reason is:
Example we put a image size 1000x1000px (about 500Kb) to only `drawable` folder. When we run this application in all device (all dpi), the size in RAM of this image <=> 1000x1000.
If we put image to `drawable-...dpi` folders, the RAM size of this image may smaller in low dpi device
### II) Don't include too much view in a layout
After debug I found that the view still initial event the visibility is GONE, if we have a view in a layout and it only show by some condition we should
- Use `ViewStub` for loading view on demand
- Use `PopupWindow`
- Use `Fragment`

### III) Reduce quality of image
#### ARGB_8888
Each pixel is stored on 4 bytes. Each channel (RGB and alpha for translucency) is stored with 8 bits of precision (256 possible values). It should be used whenever possible.
#### ARGB_4444
Each pixel is stored on 2 bytes. The three RGB color channels and the alpha channel (translucency) are stored with a 4 bits precision (16 possible values)
#### More mode
Don't care now :v
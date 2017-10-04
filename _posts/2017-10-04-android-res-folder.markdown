---
layout: post
category: "android"
title:  "Android res folder"
tags: [android]
excerpt: "res"
---

### Location
Base on https://stackoverflow.com/a/32328336/5381331
***There are two cases you deal with when working with images in Android:***
1. You want to load an image for your device density and you are going to use it "as is", without changing its actual size. In this case you should work with drawables and Android will give you the best fitting image.
2. You want to load an image for your device density, but this image is going to be scaled up or down. For instance this is needed when you want to show a bigger launcher icon, or you have an animation, which increases image's size. In such cases, to ensure best image quality, you should put your image into mipmap folder. What Android will do is, it will try to pick up the image from a higher density bucket instead of scaling it up. This will increase sharpness (quality) of the image.

***Thus, the rule of thumb to decide where to put your image into would be:***
- Launcher icons always go into `mipmap` folder.
- Images, which are often scaled up (or extremely scaled down) and whose quality is critical for the app, go into `mipmap` folder as well.
- All other images are usual `drawables`.
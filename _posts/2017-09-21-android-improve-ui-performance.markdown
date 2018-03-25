---
layout: post
category: "android"
title:  "Android Improve UI Performance"
tags: [android]
excerpt: "optimization"
---

## Improving Layout Performance

### I) Loading Views on Demand
> Use ViewStub

https://github.com/PhanVanLinh/AndroidViewStub

### II)  Optimizing Layout Hierarchies
> Use [Hierarchy Viewer](https://developer.android.com/studio/profile/hierarchy-viewer.html) for dump your layout

Some basic idea
- Example we have layout which have 3 TextViews (1 TextView at Center-Left, 1 TextView  at Top-Right, 1 at Bottom-Right). We can achieve it by using 1 RelativeLayout, or use 2 nested LinearLayout. In this case RelativeLayout is better for performance
- Prevent use layout:weight property because when we use layout:weight, layout need to redraw after it draw

### II)  Reduce Overdraw
By default, Android will set a default background for any layout (example default background for theme light is #FAFAFA).  
Then when we want to change the background of layout to another color (example #FFFFFFF), the overdraw will increase. To prevent it we can use `windowBackground`

    <style name="AppTheme" parent="Theme.AppCompat.Light.NoActionBar"> 
        ... 
        <item name="android:windowBackground">@null</item> 
    </style>

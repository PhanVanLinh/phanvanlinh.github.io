---
layout: post
category: "android"
title:  "Reduce APK size"
tags: [android, optimization]
excerpt: "Reduce APK size"
---



#  Reduce APK size

## I) Shrink Code and Resources

### Shrink Code
> use minifyEnabled true

    android {
        ...
        buildTypes {
            release {
                minifyEnabled true
                proguardFiles getDefaultProguardFile('proguard-android.txt'),
                        'proguard-rules.pro'
            }
        }
    }

- It will remove unused code of **own app** and **library** and also obfuscates the class, variable, method with short name **base on** proguard config when build project.
- After shrink, it will output some files for the details of the shrinking so if you want to verify  shrinking is correct you can check that files [(check docs for more details)](https://developer.android.com/studio/build/shrink-code.html#shrink-code)
- Sometime, shrinking remove some code that we don't want to remove so we can custom the remove files by custom the proguard

#### Some noted
- Shrinking code is disable when we use Instant Run, to enable it check the [(check docs for more details)](https://developer.android.com/studio/build/shrink-code.html#shrink-code)

### Shrink Resources
> use shrinkResources true

    android {
        ...
        buildTypes {
            release {
                shrinkResources true
                minifyEnabled true
                proguardFiles getDefaultProguardFile('proguard-android.txt'),
                        'proguard-rules.pro'
            }
        }
    }

- It will remove unused resource of **own app** and **library**
- We can remove some unused resource of some specific density by build multiple APK. 

#### Build multiple APK
> use splits in gradle

    android {  
        splits {  
               ...          
        }         
    }
[check the docs here](https://developer.android.com/studio/build/configure-apk-splits.html)

## II) Use Drawable object instead of image
- Use `shape`
- Use `vector image`

## III) Reused resource
- Use `android:rotate` for rotate image
- Use `android:tint` for change the color of image 

## IV) Avoid enumerations 
Enum take more size when build, if possible use  `@IntDef`, `@StringDef` annotation

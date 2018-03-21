---
layout: post
category: "design pattern"
title:  "Singleton"
tags: [java]
excerpt: ""
---

### EagerSingleton
```
public class EagerSingleton {
  private static volatile EagerSingleton instance = new EagerSingleton();
  private EagerSingleton() {
    // private constructor
  }
  public static EagerSingleton getInstance() {
    return instance;
  }
}
```
**Pros**: Easy, thread safe  
**Cons**: `instance` may create before `getInstance()` called.  
When `instance` load? `instance` is a static variable, static varible will load when `CLASS` load.  
When `CLASS` load? `CLASS` **only** load when we use this CLASS (for example, `CLASS.class`, `CLASS.staticVariable`, `CLASS.staticMethod`)
### LazySingleton
```
public final class LazySingleton {
  private static volatile LazySingleton instance = null;
  private LazySingleton() {
    // private constructor
  }
  public static LazySingleton getInstance() {
    if (instance == null) {
      synchronized (LazySingleton.class) {
        instance = new LazySingleton();
      }
    }
    return instance;
  }
}
```
**Pros**: `instance` only create when we call `getInstance()`  
**Cons**: If 2 threads call get `getInstance()` at same time and overcome `if (instance == null)` condition. Then 2 threads will excute in order => 2 objects will be created
### Double check LazySingleton
```
public class LazySingleton {
  private static volatile LazySingleton instance =  null;
  private LazySingleton() {
  }
  public static LazySingleton getInstance() {
    if (instance == null) { // first check
      synchronized (LazySingleton.class) {
        if (instance == null) { // second check
          instance = new LazySingleton();
        }
      }
    }
    return instance;
  }
```
**Pros**: `instance` only create when we call `getInstance()` and thread safe  
**Cons**: Not yet  
Why we need the `// first check`? Currently, I think that check `// first check` and return immediately is good for performace. If any time we `getInstance()` we need to `synchronized`, it may not good
### Initialization on Demand Holder
```
public class Singleton {  
  private Singleton() {
  }
  private static class LazyHolder {
    private static final Singleton INSTANCE = new Singleton();
  }
  public static Singleton getInstance() {
    return LazyHolder.INSTANCE;
  }
}
```
**Pros**: `instance` only create when we call `getInstance()` and thread safe  
**Cons**: If we want to pass to argument to getInstance(), I think we can not use this way

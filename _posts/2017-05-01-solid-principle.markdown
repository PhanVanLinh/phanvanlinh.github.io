---
layout: post
category: "principle"
title:  "SOLID principle"
tags: [principle]
excerpt: "principle"
---

```
1，Single responsibility principle
2, Open/closed principle
3, Liskov substitution principle
4, Interface segregation principle
5, Dependency inversion principle 
```

### **Single responsibility principle**

>One class should do one thing

### **Open/closed principle**

>Able to expand a class, but don't edit

When we need to add new fucntions for application, we should extend old class by inherit or hold this class in new class, shouldn't edit old class directly. This will make our project have more class but we don't need to test old class, just need to test new class with new function.

### **Liskov substitution principle**
> Child classes should never break the parent class’ type definitions.
> 
A subclass should override the parent class’ methods in a way that does not break functionality from a client’s point of view


    // violation of Liskov's Substitution principle
    // Car.java
    public interface Car {
      public void startEngine();
    }
    // Ferrari.java
    public Ferrari implements Car {
      ...
      @Override
      public double startEngine() {
             //logic ...
      }
    }
    // Tesla.java
    public Tesla implements Car{
      ...
      @Override
      public double start() {
             if (!isCharged){
                return;
             }
           //logic ...
      }
    }
    
    // Make the call
    public void startCar(Car car) {
       car.start();
    }

It violation `Liskov's Substitution principle` because the start method in Tesla (that override from Card) doesn't start car some time. It also violation with Function should do one thing (in Clean Code). To fix it

    public double start() {
             if (!isCharged){
                chargeTheCar();
             }
             //logic ...
      }

### **Interface segregation principle**

>Instead of using big interface with various methods, we should split it to multiple interface

The reason is very simple because if we don't split bigger interface, we must override all methods and sometime we do nothing with a lot method

### **Dependency inversion principle**

>1. High-level modules should not depend on low-level modules. Both should depend on abstractions.
>2. Abstractions should not depend upon details. Details should depend upon abstractions.

    // violation of Dependency's inversion principle
    // Program.java
    class Program {
    	public void work() {
    		// ....code
    	}
    }
    
    // Engineer.java
    
    class Engineer{
    	Program program;
    
    	public void setProgram(Program p) {
    		program = p;
    	}
    
    	public void manage() {
    		program.work();
    	}
    }

It break violation of Dependency's inversion principle because the **Engineer** class which is a high level class, and the low level class called **Program**.  
Assume that in future, the requirement change and we need a class like **SuperProgram**, we need to change the code in **Engineer** class and in ALL PLACE use **Program**.  Then we need to refactor a lot and need to test again
The solution for this problem is create a interface like 

    // Dependency Inversion Principle - Good example
    interface IProgram {
    	public void work();
    }
    
    class Program implements IProgram{
    	public void work() {
    		// ....code
    	}
    }
    
    class SuperProgram implements IProgram{
    	public void work() {
    		//....code
    	}
    }
    
    class Engineer{
    	IProgram program;
    
    	public void setProgram(IProgram p) {
    		program = p;
    	}
    
    	public void manage() {
    		program.work();
    	}
    }

### Reference
https://android.jlelse.eu/android-development-the-solid-principles-3b5779b105d2

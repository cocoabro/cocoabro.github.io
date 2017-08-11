---
layout:     post
title:      "Design Patterns"
subtitle:   "Learning Design Patterns"
date:       2017-07-05 
author:     "Rob"
---

# Design Patterns

With familiarity, design patterns are well tested solutions to common problems and issues that we may run into in Software Development. They are essentially "Templates" that are using for a specific issue. For instance, of one object changes and you want other objects to know. Instead of recreating the wheel, you could use the _Observer_ design pattern.

In 1990, Design Patterns: Elements of Reusable Object-Oriented Software, was created by a group of people (The authors of the book) known as the "Gang of Four" Their names are Erich Gamma, Richard Helm, Ralph Johnson, and John Vlissides. Exploring most of OOP and design patterns, written with C++ and Smalltalk. 


Example of Design Patterns

| Creational | Structural   | Behavioral | 
| ---|||
| Absract Factory  | Adapter   | Chain of Responsibility     |
| Builder | Bridge   | Command     |
| Factory Method  | Composite   | Interpreter     |
| Prototype  | Decorator  | Iterator      |
| Singleton  | Facade  | Mediator     |
|   | Flyweight  | Memento     |
|                  |             | Observer     |
|                  |             | State     |
|                  |             | Strategy     |
|                  |             | Template Method     |
|                  |                   | Visitor

For this post, there is only going to be two design patterns reviewed. 

# Singleton pattern

Let's say we create a class, and we only want one object of this particular class. This object needs to represent the currently running application — having more than one object may cause problems throughout the application itself. You could always NOT create more than one Object, but with design patterns, we can use the Singleton pattern to do this. 

We don't need to instantiate a Singleton, but that it is always running through the application. 

Begin by first creating our class as displayed in the code below: 

```java

    public class MySingleton {

        // additional functionality
        public someMethod() {
            //...
        }
    }
```

We then would add our constructor method, but we make it private, meaning that no other object can instantiate: 

```java
    
    // a private constructor, no other objects can instantiate this
    private MySingleton() { } 
    
```

So how does the object get instantiated? Here comes the tricky part — creating a static variable, that holds a placeholder to the singleton object. 

```java 

    // placeholder for the current singleton object
    private static MySingleton __me = null;
    
    // How you ask for the singleton
    public static MySingleton getInstance() {
    
        // check existence
        if ( __me == null){
            //if not, instantiate object and store
            __me = new MySingleton();
        }
        return __me;
    }
    
    public someMethod() {
        //...
        }
}
```

We don't have an instance just yet, first ask if the object exists. This is a technique known as _Lazy Instantiation_ there is only one of these, and there is always one of these. 

Asking for the singleton within the application is as such, which you can use in 3 different ways:

```java

    MySingleton single = MySingleton.getInstance();


    // using it somewhere
    single.someMethod();

    // or call directly

    MySingleton.getInstance().someMethod();
```

# Memento Pattern

This design pattern manages change, but does it in a way that does not violate encapsulation. It requires 3 classes that have certain roles. These are known as such: 

* _The Originator_
- _The Caretaker_
- _The Memento_

# The Originator

This object, we want to be able to change and then undo any changes to. It is not encumbered by keeping track of multiple states. 

# The CareTaker

When and why:

asks the Originator to save it's state, and passes receives the Memento object. The Caretaker doesn't know anything about the state of the Memento, it is simply there to save state, and undo any changes by handing the previous memento back to the originator. The caretaker can also ask for multiple levels of mementos, or basically multiple levels of undo. 

Encapsulation is not being broken during this time. 

# What is a Memento Then?

The _Memento_ object, is what gets created when the _CareTaker_ class requests that the Originator save itself. The memento details the parts of the Originator class and any information needed to return to a particular state. 

# There you have it

I did not want to go too deep into details because there are many Design Patterns that exist and can be applied within your applications. I am mostly interested in iOS, and I did find additional resources for applying Design Patterns in your iOS projects, you can check out <a href="https://www.raywenderlich.com/46988/ios-design-patterns">iOS Design Patterns</a> on Raywenderlich if you're interested. 
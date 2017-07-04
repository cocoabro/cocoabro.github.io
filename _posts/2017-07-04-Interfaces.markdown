---
layout:     post
title:      "Interfaces"
subtitle:   "Signing a contract"
date:       2017-07-04
author:     "Rob"
---

# Defining and Using interfaces

The term interface does not mean, user interface. An interface is created similar to a class, but with no functionality, or no actual code or behaviour. In java, interfaces are written in a specific way. 


In Java you can begin creating your interface like this:

``` java 
interface Printable { 

    // method signatures
    void print(); 
    void printToPDF(String filename);
}
```

So you might ask, what is the point of this? You're not allowed to put functionality inside an interface. If we create a new class and we choose to implement an interface, we are essentially signing a contract. The main idea when signing a contract is that you aren't the only one who will sign. 

Does the object support the particular interface? You can call things like the print method as I know that the object shares the same interface. 

An interface typically contains what we would call _method signatures_ that essentially have no functionality. 

> Program to an interface, not to an implementation. – Design Patterns, 1995

Not all languages support the idea of interface and implmentation. In Objective-C, it is known as conforming to the protocol.

An interface is just a list of method signatures, similar to a class, but has no actual functionality, code, or behavior. 

# Aggregation and composition. 

Aggregation works differently, previously we wrote about how a _car is a vehicle_ and that a car can't inherit as a bus. 

In terms of Aggregation you can think of it in a "HAS A" relationship. 

As an example: 

* A customer has a address.
* A car has a engine. 

It can implicitly suggest things like: 

* A bank has many bank accounts.

In UML it is displayed like this: 

![UML aggregation](/img/umlAgg.png)


The empty diamond refers to aggregation. 

- 1 Classrom: Refers to the classrom object. 
  * *Student: Refers to 0 to many students.
  
Aggregation describes a "HAS A" relationship. 


# Composition

Composition is essentially aggregation, but a more specific form of it. 

The solid diamond refers to composition.

It implies ownership, such as that if you deleted the document object, all the associated page objects to be deleted to. 

![UML composition](/img/umlComp.png)

# Ownership

The differences between aggregation and composition is as shows. In an aggregation situation, if we deleted the classroom object, I wouldn't expect a student object to get destroyed. In aggregation, students could be used in different objects.

The student object will still exist since there is no ownership implied, there would be no need to have a constructor as well as a destructor created. 

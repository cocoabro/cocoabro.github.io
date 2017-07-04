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

> Program to an interface, not to an implementation. – Design Patterns, 1995
---
layout:     post
title:      "Inheritance"
subtitle:   "Learning about Inheritance, and more"
date:       2017-07-03 
author:     "Rob"
---

# Inheritance

One of the four key concepts of object-orientation. 

Inheritance describes an "IS A" Relationship. For instance, can you describe something such as: 

* A car is a vehicle.
* A bus is a vehicle. 

Or you could also use other examples like: 

* An employee is a person
* A customer is a person

However, you can't use other terms because they simply do not make any sense:

* A car is a bus
* A customer is a shopping cart. 

You could also go as far as even saying: 

* A checking account is a kind of bank account.
* A savings account is a type of bank account. 

We know what makes sense and what doesn't. Inheritance allows us to borrow from the parent class, such as that if you have a class Car, and we would like to know if: 

* A Bentley Continental GT is a car is a vehicle. 
* A Pomeranian is a dog is a mammal is an animal. 

Inheritance is to allow us to identify shared attributes and behaviours between objects and avoiding reinventing the wheel. 

<div class="advertisement">
<script async src="//pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<!-- robmcelvenny.com -->
<ins class="adsbygoogle"
     style="display:block"
     data-ad-client="ca-pub-9138756976382898"
     data-ad-slot="5147608880"
     data-ad-format="auto"></ins>
<script>
(adsbygoogle = window.adsbygoogle || []).push({});
</script>   
        </div>

# UML Representation of Inheritance

To identify Inheritance in UML, it is normally represented by open ended arrows pointing to your main class as displayed in the screenshot below. 

![UML Inheritance](/img/umlInheritance.png)

You can see here how the super/parent class, is thoughtfully designed. These other objects are inheriting from the BankAccount class, which gives them everything from the main BankAccount class, but also allows to add additional _instance variables_ to the mix. 

These are known as the subclass, or child class. e.g. CheckingAccount might have a very small interest rate, where as SavingsAccount and InvestmentAccount have higher level interst rates set. 

# Super/Parent Class or Child/Subclass

When you start creating things like Albums, Books, or Movies – a lot of these objects will have the same states and behaviours shared between objects. Here is where the _super_ class comes in, and you can create classes that hold the base _instance variables_. 

| Book: Super Class|
| ----- |
| ``` title ``` |
| ``` price ``` |
| ----- |
| ``` purchase() ``` |
| ``` download() ``` |
     
 
 | Magazine: Child Class | 
 | ----- |
| ``` book inherited ```
| ``` author ``` | 
| ----- |
| ``` book inherited ``` |

# Abstract Class

Abstract classes exist only for inheritance, the class is never instantiated but other classes that inherit from the super class DO actaully get instantiated. Abstract Classes are never instantiated – yet they are useful because they provide shared behaviours. 

In languages like java you define an abstract class like this:

Java: 
``` java
    abstract class BankAccount { 
        [...]
    }
```

This is a much more common technique in languages like C#, Java, VB.NET, and C++. 

The "IS A" relationship is used to determine if there is inheritance between two classes. 
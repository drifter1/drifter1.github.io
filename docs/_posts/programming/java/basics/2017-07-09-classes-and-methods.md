---
layout: default
title: Classes and Methods
description: Java Classes and Methods
thumbnail: /images/tutorials/programming/java.png
categories: [programming, java]
tags: [programming, java, basics]
permalink: /tutorials/:categories/:title
---

# Java Classes and Methods

* * *

![](http://net-informations.com/faq/general/img/class.png)


  In today's post we will talk about the "parts" that a Java (and most object-oriented programming languages) Programm is split into the **Classes**. Last time, we talked a little bit about basic stuff to go from C to Java and created the main or driver class called "clike" to run our code without the need of talking about some stuff that deeply. We will also talk about some methods that are present in Objects or Classes in Java and are predefined and can be "edited". Let's start out with the structure of an class. 


# Class Structure


   Most of the times **each Class** will be in a **separate java file**, but it doesn't have to be a separate file. We can also have things like **Inner and Outer Classes**, but I will not talk about them for now. A Class **consists** of Variables so called **Data** and the Functions called **Methods**. The **visibility** of the whole class and the Data and Methods it consists from, can be tweaked with **Access Levels**. Those Access Levels come as words before the declaration of the classes, variables and functions type and name. There are 4 of them:


* *public*: visible from everywhere
* *private*: visible only in the class it is defined
* *protected*: visible in class it is defined, the subclasses it contains and the package the class is in
* default (if you put nothing): visible in class it is defined and the package the class is in


So, the **basic class mode**l is:



```
public class class_name{
```


```
     // DATA: variables
```


```
     // METHODS: functions
```


```
     // Inner Classes
```


```
}
```

We will have this Code saved in a Javafile called **class\_name.java** and:


* the DATA mostly will be private, but you could also use public ones some times
* the METHODS will be public, except some that might be called from other functions in class and don't need to be accessible from outside, when using the final Object.


There are two **basic types** of Classes:


1. Main or **Driver Classes** that run the main function and use the other ones to **create Objects**.
2. **Object Classes**, as I like to call them, that **will become Objects** in the Driver Class.


# Driver Classes:


   This Class contains the **main function** of the whole Java Programm and is **called first** and uses Objects of the other Classes to run the Code. So, using the other Classes we create Objects and do stuff on them like: 


* changing the variable values of a specific Object
* using the functions to do stuff on a specific Object
* compare 1 or more Objects and so on...


The **basic structure** of this type is:



```
public class class_name{
```


```
    //DATA: variables and Objects of the other Classes
```


```
   //METHODS: the main method(exists only in Driver Class) and maybe even others, but we mostly use the functions of the Objects main is using
```


```
   public static void main(String[] args){  //main method
```


```
   }
```


```
   // Inner Classes: that could be the classes that it will use as Objects
```


```
}
```

This is actually all you need to know right now about them so let's jump into the Object Classes.


# Object Classes - Constructors:


    A Object Class will be used as an Object when called in the Driverclass and it needs to have:


* informations (variables) about an Object that is part of our Programm
* methods to help us work with this informations (variables)


An Object Class **doesn't contain any main method** and so it will become an Object only when using it with the **new modifier**, like the Array's that we talked about last time. The way it "becomes" and Object is defined by an function called **Constructor** and there is a **default constructor** already there that gets overwriten if we write our own one and that doesn't take any parameters and just creates an empty Object. It is just an **public method** that doesn't return anything and we don't even write void! An Constructor is being written like this:



```
public class_name(){ //default constructor
```


```
}
```


```
public class_name(//parameters){ //custom one
```


```
   // Initialization of variables
```


```
}
```


```
//we can have infinitely ones of them
```

# Getters-Setters:


   The variables can be public, but for **safety** it's good to thing about using G**etters and Setters** and have **all the Data** be **private**. An G**etter** is a function **of the type that the variable it is used for is**, cause it has to return (get) the value an has **no parameters** at all. An S**etter** is **of type void** and has **one parameter that is the value that we want the variable it is used for to be set**. 


Suppose we have a **variable** of **type variable\_type** with name **v** then:



```
public variable_type getVariable(){ //getter
```


```
    return v;
```


```
}
```


```
public void  setVariable(variable_type v){ //setter
```


```
   this.v = v; //the value of the class (this.v) gets the value of the parameter v
```


```
}
```

# toString():


Next on let's talk about printing the information. You can simply print out every value of every single variable, but there is already a function called **toString()** that we will **override** and that **returns a String Representation** **of our Object**. We can **define by ourselves** what exactly should be returned by concatenating the values of our variables as we wish and putting messages between them. 


Suppose we have an Objectclass with a String name and an Integer age then we can override the function like this:



```
@Override //used for overriding
```


```
public String toString() {
```


```
   return "Name: " + name + ", Age: " + age; //it prints Name: name_value, Age: age_value
```


```
}
```

There is also a function called **equals()** that we can also override the same way and is being used for testing similarity and returns a boolean value true or false. We will talk about toString() and equals() again some other time.


# Methods:


Last but not least let's talk about **creating our own methods**. It depends on where you define them. When you are in an **ObjectClass** then you simple **create public functions** the same way as we defined the Setters and Getters functions, cause there already exists an instance of the Object and we call the functions from this Object. Like this:



```
public variable_type function_name(//parameters){  

  

   //code
```


```
   return v; //if variable_type is void then you don't need this  

  

}
```

When you are in the **Driverclass** in other hand, than you have to **create public static methods** like the main method, cause there is no instance of this class there, cause we rarely use the Driverclass as an Object.


So you do it like this:



```
public static variable_type function_name(//parameters){  

  

   //code
```


```
   return v; //if variable_type is void then you don't need this  

  

}
```

Most of the times we don't need functions in the Driverclass, but you should know that you will need the additional keyword **static** if you do so. 


# Code:


Let's Create a simple programm that contains a Driverclass and a Objectclass. We want to create 2 Student Objects and print them out. The **first one** will get each value of the variables individually using setters and print them out with getters and the **other one** by passing in the values of the variables as arguments with an **Overloaded Constructor** and print out with toString(). A Student is defined by his ID, Name and Surname that are of type Integer, String and String. We will not get user input. 


Driver:



```
public class Driver { // Driver.java
```


```
	public static void main(String[] args) {
```


```
		// 2 Student Objects
```


```
		Student s1;
```


```
		Student s2;
```


```
		s1 = new Student(); // using default constructor
```


```
		// setting each value individually with Setters
```


```
		s1.setID(100);
```


```
		s1.setName("Tom");
```


```
		s1.setSurname("Williams");
```


```
		// printing out using Getters
```


```
		System.out.println(s1.getID() + " " + s1.getName() + " " + s1.getSurname());
```


```
		s2 = new Student(101, "John", "Smith"); // using overloaded constructor
```


```
		System.out.println(s2); // you don't have to use s2.toString() when
```


```
					// putting it "alone"
```


```
	}
```


```
}
```

  



Student:



```
public class Student { // Student.java
```


```
	// DATA
```


```
	private int ID;
```


```
	private String name;
```


```
	private String surname;
```


```
	// private for safety
```


```
  

```


```
	// METHODS
```


```
  

```


```
	// Constructors
```


```
	public Student() { // default constructor
```


```
		ID = 0;
```


```
		name = surname = null;
```


```
		// we could also use setters
```


```
	}
```


```
    public Student(int ID, String name, String surname) { // overloaded constructor												
```


```
		this.ID = ID;
```


```
		this.name = name;
```


```
		this.surname = surname;
```


```
		// we could also use setters
```


```
	}
```


```
  

```


```
	// Getters-Setters
```


```
	public int getID() {
```


```
		return ID;
```


```
	}
```


```
  

```


```
	public void setID(int ID) {
```


```
		this.ID = ID;
```


```
	}
```


```
  

```


```
	public String getName() {
```


```
		return name;
```


```
	}
```


```
  

```


```
	public void setName(String name) {
```


```
		this.name = name;
```


```
	}
```


```
  

```


```
	public String getSurname() {
```


```
		return surname;
```


```
	}
```


```
  

```


```
	public void setSurname(String surname) {
```


```
		this.surname = surname;
```


```
	}
```


```
  

```


```
	// Other Functions
```


```
	@Override
```


```
	public String toString() {
```


```
		return ID + " " + name + " " + surname;
```


```
	}
```


```
  

```


```
}
```

* * *

## Java Language

<br>

{% include programming/java_topics.html %}
  
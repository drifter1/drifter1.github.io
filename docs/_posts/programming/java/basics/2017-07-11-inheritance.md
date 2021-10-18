---
layout: default
title: Inheritance
description: Java Inheritance
thumbnail: /images/tutorials/programming/java.png
categories: [programming, java]
tags: [programming, java, basics]
permalink: /tutorials/:categories/:title
---

# Java Inheritance

* * *

![](http://java.meritcampus.com/assets/vehicles-multi-level-hierarchy-2ae71f7f7869a8bc77de95f843a5b8f5.png)


   In todays post we will talk about **Inheritance** in Java. We will talk about how to use it with **abstract classes** and without them and take a look at some keywords like **extends** and **super**. So without further ado, let's start!


# Inheritance:


   The same way as we did in Composition we implement a relationship, but this time it's a **is-a relationship**. So every **Childclass** that **extends** a class will have **every DATA and METHOD** from the **Parentclass** it extends from. The Parentclass will contain variables (Data) and functions (Methods) and the Childclass will have all those and the ones it defines by it's own. We can even use the same ones as the Parentclass and **override** them, using the @override "modifier". To make a class be the child of another class we simply use the keyword **extends** and the name of the class when defining the class like this:



```
public class *child\_class\_name* extends *parent\_class\_name*{
```


```
    //DATA
```


```
    //METHODS
```


```
}
```

   To access all of the variable from the parent or **hyperclass** we use the keyword **super** and the **'.' modifier** and using that we can call any function and use any variable from the superclass with ease. You will get it when you see some Code later on.


   We use Inheritance to **make** the **code simpler** and to **save space** when some Objects are both another Object too and those similarities are then an Hyperclass that they inherit from. 


**For example**:


   A Car and a Truck are both Vehicles and we could have them both **inherit** from a class Vehicle that contains some informations and (abstract) methods that both have. That could be: 


* Data like name, hp, year, owner\_name
* Methods like speed(), accelerate() and so on.


  



# Constructor "Trick":


   To **construc**t an Object that inherits from another class you can use the way we learned before like this:



```
class_name object_name = new class_name();
```

    When using Inheritance you can also create an object from the **hyperclass** it inherits from and then use the constructor from the **subclass** you want like this:



```
hyper_class_name object_name = new sub_class_name();
```

This way we can have an **Array of hyperclass objects** and have them all be **separate subclass objects**. 


**For example:**


   You want to have an Array where you save Shapes (this is what we will make in the Code), but each one can be a **different** Shape. We don't want to create more than 1 Arrays, but we will create an Array or ArrayList that will contain Shape Objects and **each Shape** will use the **Constructor of it's type**, like Circle(), Square()  **instead** of the **Shape Constructor.** 


  



# Abstract Classes:


   Most of the times it makes sense to have the parentclass be a **abstract class**, because we can't define most functions and so we will have them be **abstract functions** (we will talk about them more in the next post) that can be defined only when having an abstract class or interface (also next time). The way we define an abstract class is using the **keyword abstract** when defining the class (the same goes for abstract functions). Like this:



```
public abstract class *class\_name*{
```


```
   //DATA 
```


```
   //METHODS (mostly abstract functions)
```


```
}
```

   A class that inherits from an abstract class **doesn't have to implement all of the abstract functions** (that's something that you need to do when having an interface). You can use those that you want and even create more.


**For example:**


   Suppose we have a Shape Object and we want to find it's Perimeter and Area using functions. When not knowing what kind of Shape it is (using subclasses that inherit from Shape), we can't define the functions so they need to be abstract and so the Shape Class will be also abstract. 


  



# Code:


   Let's Create an Program that has an ArrayList of Shapes and each Shape has a Name, 2 Functions that calculate the Area and Perimeter, and the toString() Method to print the Object out. We will have 2 Objects that will be Shapes: Circle and Square, and insert 5 random ones with random values, inside of the ArrayList and print it out afterwards. We will not use Getters-Setters to make it simpler.


 Shape:



```
// Shape is the abstract HyperClass and each other Shape IS A Shape
```


```
public abstract class Shape { // Shape.java						
```


```
	String name; // All Shapes have a Name
```


```
	// abstract Methods
```


```
	public abstract double Perimeter();
```


```
	public abstract double Area();
```


```
	public String toString() {
```


```
		return name;
```


```
	}
```


```
}
```

  



Circle:



```
 // Circle IS A Shape with specific Things
```


```
public class Circle extends Shape { // Circle.java
```


```
	static double pi = 3.14; // static variable
```


```
	double radius; // Circle HAS A radius
```


```
	public Circle(double radius) {
```


```
		super(); // constructor of super(or hyper)class
```


```
		this.radius = radius;
```


```
		name = "Circle"; // you can use just name instead of super.name
```


```
	}
```


```
	public Circle() {
```


```
		super(); // constructor of super(or hyper)class
```


```
		name = "Circle"; // you can use just name instead of super.name
```


```
	}
```


```
	public double Perimeter() {
```


```
		return 2 * pi * radius;
```


```
	}
```


```
	public double Area() {
```


```
		return pi * Math.pow(radius, 2);
```


```
	}
```


```
	@Override
```


```
	public String toString() {
```


```
		return super.toString() + " " + radius; // super is the HyperClass Shape
```


```
	}
```


```
}
```

  



Square: 



```
// Square IS A Shape with specific Things
```


```
public class Square extends Shape { // Square.java
```


```
	double side; // Square HAS A side
```


```
	public Square(double side) {
```


```
		super(); // constructor of super(or hyper)class
```


```
		this.side = side;
```


```
		name = "Square"; // you can use just name instead of super.name
```


```
	}
```


```
	public Square() {
```


```
		super(); // constructor of super(or hyper)class
```


```
		name = "Square"; // you can use just name instead of super.name
```


```
	}
```


```
	public double Perimeter() {
```


```
		return 4 * side;
```


```
	}
```


```
	public double Area() {
```


```
		return Math.pow(side, 2);
```


```
	}
```


```
	@Override
```


```
	public String toString() {
```


```
		return super.toString() + " " + side; // super is the HyperClass Shape
```


```
	}
```


```
}
```

  



TestShapes:



```
import java.util.ArrayList; //ArrayList Object
```


```
import java.util.Random; //Random Object
```


```
public class TestShapes { // TestShapes.java
```


```
	public static void main(String[] args) {
```


```
		ArrayList<Shape> list = new ArrayList<>(); // list of Shapes
```


```
		Random r = new Random(); // Random generator Object
```


```
		double random;
```


```
		for (int i = 0; i < 5; i++) { // inserting 5 shapes
```


```
			Shape s; // temporary Shape
```


```
			random = r.nextInt(2); // returns integer from range [0,2) so 0 or 1
```


```
			if (random == 0) { // create a Circle
```


```
				random = 1 + r.nextDouble() * 5; // returns double in range [1,6)
```


```
				s = new Circle(random);
```


```
			} else { // create a Square
```


```
				random = 1 + r.nextDouble() * 5; // returns double in range [1,6)					
```


```
				s = new Square(random); // using overloaded constructor
```


```
			}
```


```
			list.add(s);
```


```
		}
```


```
		// print them out
```


```
		for (int i = 0; i < list.size(); i++) {
```


```
			System.out.println(list.get(i));
```


```
		}
```


```
	}
```


```
}
```

* * *

## Java Language

<br>

{% include programming/java_topics.html %}
  

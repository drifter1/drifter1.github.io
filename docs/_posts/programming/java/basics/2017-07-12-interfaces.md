---
layout: default
title: Interfaces
description: Java Interfaces
thumbnail: /images/tutorials/programming/java.png
categories: [programming, java]
tags: [programming, java, basics]
permalink: /tutorials/:categories/:title
---

# Java Interfaces

* * *

![](https://www.javatpoint.com/images/core/interfacerelation.jpg)


   This time we will take a look at **Java Interfaces**. They are similar to **abstract classes** and use **abstract functions** and **static variables**. A Class can **implement** them and an Interface can **extend** from other Interfaces (the same way that Inheritance worked). We will also use an **Anonymous Object** in the Coding section.


# Interfaces:


   Interfaces are used to **define** some kind of **Behavior** (functions and even variables) that a Class **needs to have** to be the kind of Object the Interface is representing. Interfaces contain **abstract methods** that need **implemenation** from the Class that **implements** them. They also have some **static variables**, mostly **Constants** that get passed to the Class that implements them. So, they can be used for the same things as **abstract Classes**, but there is a big **difference**: "The abstract methods **need to be** implemented".


   To **define** a Interface you don't create a class but an **interface** like this:



```
public interface *interface\_name*{ //saved in *interface\_name*.java  

    // static DATA
```


```
    // abstract METHODS  

}
```

   A class that wants to implent a Interface uses the **keyword implements** the same way as we used **extends** for inheritance with classes. An Interface can also extend another Interface using **extends**, like we did in class inheritance. To make a class implement a interface we do this:



```
public class *class\_name* implements *interface\_name*{
```


```
    // DATA (the static variables from the Interface don't need definition)
```


```
    // METHODS (implementation of the abstract functions of the interface and other functions)
```


```
}
```

# Code:


   Let's go into coding now. We will create an interface that stands for Sorting and will contain the abstract functions DescendingSort() and AscendingSort(). Any class that wants to Sort will need to implement this Interface. And we will create an Driverclass(!) that implements Sorting and will have an integer array that gets filled with random numbers and afterwards sorts it with one random way and prints it out. 


   Because, it is the Driverclass that implements the Interface (and not an Objectclass) and **we don't have an instance** of the Object Driver (and don't want to create one as an Object) we will use a trick with the **new modifier** to create an **Anonymous Object** of type Driver that will only execute the functions and then "disappear".


Sorting:



```
public interface Sorting { // Sorting.java			
```


```
	//we don't have static variables in this one
```


```
	
```


```
	// abstract functions that need implementation
```


```
	public abstract void DescendingSort(int[] nums);
```


```
	public abstract void AscendingSort(int[] nums);
```


```
}
```

  



Driver:



```
// this Class is implementing Sorting
```


```
public class Driver implements Sorting { // Driver.java
```


```
	public static void main(String args[]) {
```


```
		int[] nums = new int[20];
```


```
		int r;
```


```
		//fill with random numbers
```


```
		for (int i = 0; i < nums.length; i++) {
```


```
			nums[i] = 1 + (int) (Math.random() * 100); // random int from 1 to 100
```


```
		}
```


```
		r = (int) (Math.random()*2); //random int value of 0 or 1
```


```
		if(r == 0){// print in Ascending Order	
```


```
			//calling the function using a new instance of Driver
```


```
			new Driver().AscendingSort(nums); 	
```


```
			//print array
```


```
			for (int i = 0; i < nums.length; i++) {
```


```
				System.out.println(nums[i]);
```


```
			}
```


```
			System.out.println();
```


```
		}
```


```
		else{ // print in Descending Order
```


```
			//calling the function using a new instance of Driver
```


```
			new Driver().DescendingSort(nums);
```


```
			//print array
```


```
			for (int i = 0; i < nums.length; i++) {
```


```
				System.out.println(nums[i]);
```


```
			}
```


```
			System.out.println();
```


```
		}		
```


```
	}
```


```
	// IMPLEMENTED METHODS
```


```
	public void DescendingSort(int nums[]) {
```


```
		for (int i = 1; i < nums.length; i++) {
```


```
			for (int j = 0; j < nums.length; j++) {
```


```
				if (nums[i] > nums[j]) {
```


```
					int temp = nums[i];
```


```
					nums[i] = nums[j];
```


```
					nums[j] = temp;
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


```
	}
```


```
	public void AscendingSort(int[] nums) {
```


```
		for (int i = 1; i < nums.length; i++) {
```


```
			for (int j = 0; j < nums.length; j++) {
```


```
				if (nums[i] < nums[j]) {
```


```
					int temp = nums[i];
```


```
					nums[i] = nums[j];
```


```
					nums[j] = temp;
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


```
	}
```


```
}
```

  



   This post was smaller, because we don't have to say much about Interfaces and how to use them and I don't wanted to put Interfaces with something else. I will try to do this with everything from now on, to make the posts smaller and easier to read. The stuff that comes after this will become more difficult and you should also get ready for a big Exercise that will contain everything that we did about Java until then. It will be my University Task with some things taken out, because I did it with an GUI and I will upload a second full version with GUI after we talked about GUI and Events, also tweaked a little, because it was like 10000 lines of Code on each of the 7 Classes that checked really every error and bug that could possible exist. 

* * *

## Java Language

<br>

{% include programming/java_topics.html %}
  

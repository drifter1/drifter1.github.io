---
layout: default
title: From C To Java
description: From C To Java
thumbnail: /images/tutorials/programming/java.png
categories: [programming, java]
tags: [programming, java, basics]
permalink: /tutorials/:categories/:title
---

# From C To Java

* * *

In this post we will talk about going from C into Java knowing all that I told in previous posts.


![](http://d3gnp09177mxuh.cloudfront.net/tech-page-images/java.png)


# **Statements:**


Most statements like if-else, while, for, switch-case are the same as in C and are predefined and don't need to be "imported". The way you define variable and functions is also mostly the same, except we need to use words in front now like public, static, private that are not so present in non-object-oriented programming. 


# Objects and Classes:


In **object-oriented programming** like Java or C# you use Objects that are **similar** **to** the **Structs** we talked about previously. The only difference is that a Struct now will **also have functions or methods** that can be called via the **"." modifier** the same way as we got or changed the values of specific member's of the Struct. This Objects are mostly made in **Classes**, a specific subprogramm of the whole Programm in which we split our programm. So, using objects and classes you put the code where it needs to be and the code is easier to read and parts of it **reusable**. For example, you don't have to make an char array now for String's but there is a **String Class or Object** predefined in Java that has all the methods and stuff you need to get going. There are many of those Object's included in Java Libraries and you can find all of them in the **Java API**:  <https://docs.oracle.com/javase/7/docs/api/>


# User Input:


For user input I like to use the Object **Scanner**, cause it's easy to use and can be used for all datatypes needed for basic stuff. You **define** it like that: 



```
Scanner s = new Scanner(System.in); //where System.in means Keyboard Input
```

then using **s.nextInt()** you can get Integer Input, **s.next()** String Input, **s.nextLine()** Line Input (Like an whole text) and **s.next().CharAt(0)** Character Input, where you call the String Input and that call a String function that returns the first Character. There are also other ways of doing it, but I think for starting out Scanner is the best way. For closing the Scanner you use **s.close()**. I do it to get rid of the Error, but sometimes it may come handy.


# Printing at Console:


For printing we use **System.out.print()** or **System.out.println()** that puts a new line also. You could also use **System.out.printf()** if you like the way C does things. For Printing an Variable with it you can just put it inside alone, but when you also have some message you will have to **concatenate** the String's using the **+ sign.**


**For example:** 


when you want to print the text "Hello, World!" you do **System.out.println("Hello, World!");**


when you want to print "value : 5" where 5 is the value of some integer a you do: 


**System.out.println("value : " + value);**


# **Arrays:**


An Array is an Object in Java and when using objects you use the **new** modifier to create and allocate the object, cause else it's like an pointer in C and is null and this will cause null pointer exceptions. So for creating an Integer Array of size "size" you do: **int[] A = new int[size];** You can also split those if you want to put the size afterwards like this:  



```
**int[]A;**
```


```
**//Other Code**
```


```
**A = new int[size];**
```

# **Code:**


Now that we know some basic stuff about Java let's create an C-Like programm in Java. Suppose we want to create a program that does some calculations on an integer array. The array will be of size "size" a variable that we get as user input (pseudo-dynamic) and size needs to be between 1...100.


We will create a menu that gets a string user input(switch case) and does the following:


 “fill”: fill Array with rand numbers between a...b where a, b integers and a < b


 “sum” : sum Array


 “max” : find max


 “min” : find min


 “sort” : sort Array


 “search” : search number


 “avg” : average


 “exit” : Exit


You don't need functions for them cause we don't spoke about them yet.



```
package steemit; //the packet in the IDE I save the code
```


```
  

```


```
import java.util.Scanner; //library for Scanner object
```


```
  

```


```
public class clike { // you have to call your .java file also clike.java
```


```
  

```


```
	public static void main(String[] args) { // this is the way we define main
```


```
  

```


```
		Scanner in = new Scanner(System.in); // java object for user input /
```


```
		int[] A; // define array without size
```


```
		int size; // variable for the size
```


```
		int a, b; // values from user
```


```
		int sum = -1, max, min;
```


```
		int search, num, temp; // user input
```


```
		double avg = -1;
```


```
		char sort; // for sort choice
```


```
		String choice; // string for switch case choice
```


```
  

```


```
		// size of array as user input
```


```
		do {
```


```
			System.out.print("Give size for array: "); // printing to console
```


```
			size = in.nextInt(); // getting user integer input
```


```
			if (size < 1 || size > 100)
```


```
				System.out.println("The size must be in the range of 1...100");
```


```
		} while (size < 1 || size > 100);
```


```
		A = new int[size]; // "allocate" the array of size
```


```
  

```


```
		do { // infinite loop
```


```
				// print menu
```


```
			System.out.println("“fill”: fill Array with rand numbers");
```


```
			System.out.println("“sum” : sum Array");
```


```
			System.out.println("“max” : find max");
```


```
			System.out.println("“min” : find min");
```


```
			System.out.println("“sort” : sort Array");
```


```
			System.out.println("“search” : search number");
```


```
			System.out.println("“avg” : average");
```


```
			System.out.println("“Q” : implementation of question Q");
```


```
			System.out.println("“exit” : Exit");
```


```
			// getting choice
```


```
			System.out.print("choice: ");
```


```
			choice = in.next(); // getting string input
```


```
			switch (choice) { // switch case of String (couldn't be done in C
```


```
								// that easily cause in Java String is a Object
```


```
			case "fill":
```


```
				// read numbers a, b for range
```


```
				do {
```


```
					System.out.println("Give 2 ints to fill array with random numbers between them");
```


```
					System.out.print("a: ");
```


```
					a = in.nextInt(); // getting user integer input
```


```
					System.out.print("b: ");
```


```
					b = in.nextInt(); // getting user integer input
```


```
					if (!(a < b))
```


```
						System.out.println("a must be less then b");
```


```
				} while (!(a < b));
```


```
  

```


```
				// fill array with number in range [a,b]
```


```
				for (int i = 0; i < A.length; i++) {
```


```
					// getting random number between a...b
```


```
					A[i] = a + (int) ((b - a + 1) * Math.random());
```


```
				}
```


```
				break;
```


```
			case "sum":
```


```
				// calculating sum
```


```
				sum = 0;
```


```
				for (int i = 0; i < A.length; i++) {
```


```
					sum += A[i];
```


```
				}
```


```
				System.out.println("sum of array is: " + sum);
```


```
				break;
```


```
			case "max":
```


```
				// finding max
```


```
				max = 0;
```


```
				for (int i = 1; i < A.length; i++) {
```


```
					if (A[i] > A[max])
```


```
						max = i;
```


```
				}
```


```
				System.out.println("max is " + A[max]);
```


```
				break;
```


```
			case "min":
```


```
				// finding min
```


```
				min = 0;
```


```
				for (int i = 1; i < A.length; i++) {
```


```
					if (A[i] < A[min])
```


```
						min = i;
```


```
				}
```


```
				System.out.println("min is " + A[min]);
```


```
				break;
```


```
			case "sort":
```


```
				// sorting array
```


```
				System.out.println("Do you want ascending (a) or descending (d) order?");
```


```
				do {
```


```
					System.out.print("Choice: ");
```


```
					sort = in.next().charAt(0); // getting char input
```


```
				} while (sort != 'a' && sort != 'd');
```


```
				if (sort == 'a') { // ascending sort
```


```
					for (int i = 0; i < A.length; i++) {
```


```
						for (int j = 0; j < A.length; j++) {
```


```
							if (A[i] < A[j]) {
```


```
								temp = A[i];
```


```
								A[i] = A[j];
```


```
								A[j] = temp;
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
				} else if (sort == 'd') { // descending sort
```


```
					for (int i = 0; i < A.length; i++) {
```


```
						for (int j = 0; j < A.length; j++) {
```


```
							if (A[i] > A[j]) {
```


```
								temp = A[i];
```


```
								A[i] = A[j];
```


```
								A[j] = temp;
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
				break;
```


```
			case "search":
```


```
				// search for a number
```


```
				System.out.print("Give number to search for: ");
```


```
				num = in.nextInt();
```


```
				search = -1;
```


```
				for (int i = 0; i < A.length; i++) {
```


```
					if (A[i] == num) {
```


```
						search = i;
```


```
						break;
```


```
					}
```


```
				}
```


```
				if (search != -1)
```


```
					System.out.println("Found at pos: " + search);
```


```
				else
```


```
					System.out.println(num + " was not found!");
```


```
				break;
```


```
			case "avg":
```


```
				// find average
```


```
				if (sum == -1) { // if sum was not called: error
```


```
					System.out.println("Choose “sum” first");
```


```
					break;
```


```
				}
```


```
				avg = (double) sum / A.length;
```


```
				System.out.println("avg of array is: " + avg);
```


```
				break;
```


```
			case "exit":
```


```
				// terminate programm
```


```
				in.close(); // close the Scanner
```


```
				System.exit(0);
```


```
			default:
```


```
				// wrong choice
```


```
				System.out.println("Wrong choice! Give another choice!");
```


```
			}
```


```
  

```


```
		} while (true);
```


```
  

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
  




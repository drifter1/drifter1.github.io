---
layout: default
title: Exceptions
description: Java Exceptions
thumbnail: /images/tutorials/programming/java.png
categories: [programming, java]
tags: [programming, java, basics]
permalink: /tutorials/:categories/:title
---

# Java Exceptions

* * *

![](https://i.imgur.com/yuL3H.png)


   Hello it's a me drifter1 and today we will talk about **Exceptions** in Java. We catch Exceptions using the **try-catch** statement and the Exceptions can be **predefined** ones from java libraries, like for File Errors (we will talk about them next time) or **user-defined** that I will show you how to create and use them.


# Exceptions:


   An Exception is an **Error** that occurs when something *that is not supposed to happen* happens in the Code. 


   Those Errors can be:


* a variable gets a value that is outside of the range it should be in (an id is negative but it should be positive)
* a numeric variable (integer or double) gets an String as value that causes an Exception
* an input operation fails to execute cause the file asked for doesn't exist (file input)
* a object has not been allocated and the pointer that points to it is null (null pointer exception)
* an object of some specific type is not found or is null, but it was needed for some method


          and many others...


   If some type of **Exception occurs** and we **don't have** any **Code to catch it** then the programm will most of the times **crash** or stop functioning properly. So, let's discuss how we can catch one.


# Try-Catch:


   To **catch an Exception** and prevent the programm from crashing we use a try-catch statement. The Code that **could cause** an **Exception** comes inside of the **try** part. The **Exception** that we **want to catch** comes inside of the **catch** part. Finally, in the **finally** part we put **Code that needs to be executed either a Exception occurs or not**. You are **not obligated** to use the finally part. An try-catch-finally statement is written like this:



```
   try{
```


```
       // something that could cause Exceptions
```


```
   } catch(Exception e){
```


```
       // what to do when Exception Occurs (mostly Error Message)
```


```
   } finally{
```


```
      // important Code that needs to be executed
```


```
   }
```

   Using this type of statements we can do most of the stuff that we need for **Exception Handling**. But, we can't use it directly when having Custom Exceptions. Let's take a look into them.


# Custom Exception Messages:


   An user-defined Exception is a **Class** that **inherits** from the **Exception class** from the Java library. We can "fill" the class with 2 ways:


1. Have an **Constructor** that **calls** the **super Constructor** (from the Exception class) with an **String argument** to print an Error message.
2. Have an **Constructor** set the value of a **String variable** to contain the Error message and use the **toString() method** for printing the Error message


**Code 1:**



```
public class CustomException extends Exception { // user defined Exception
```


```
        public CustomException(){ // constructor
```


```
               super("Custom error message!");
```


```
	}
```


```
}
```

  



**Code 2:**



```
public class CustomException extends Exception{  // user defined Exception
```


```
       String message;
```


```
       public CustomException(String message){ // constructor
```


```
             this.message = message;
```


```
       }
```


```
       public String toString(){
```


```
             return message;
```


```
       }
```


```
}
```

   With the **first one** you just **call a new instance of the Exception** to print the Error message and with the second one you **print a new instance of the Exception** that will automatically print the Error message using toString(). 


  



# Catching Custom Exceptions:


   To catch Exceptions that are **not user-defined** we simply put the Code that could cause one inside of the **try-catch statement**, because the Class functions that we are using already test for Exceptions and can catch them but can't do something until we do something using try-catch. 


   To make a **function check** for a specific Exception we use the **throws keyword**. Using this keyword the function will **check for a condition** (programmer-defined) and when the condition is true or not (it has to do with the type of Exception we are talking about) it will **return a new instance of the Exception** that will cause an Exception that needs to be handled. This is done like this:



```
public variable_type *function\_name* (//parameters) throws CustomException_name{
```


```
   if ( // something wrong){
```


```
      throw new CustomException();
```


```
   }else{ // something right
```


```
      //other Code
```


```
   }
```


```
   //it could also be opposite way
```


```
}
```

   Than every time we call the function, **if an Error occurs the function will throw an Exception** and when we have the function inside of the try part and we check for the specific CustomException or an Exception generally (most of the times) inside of the catch part we will be done with Exception Handling for this Code.


  



# Code:


   We will make a little programm that creates an Student with id, name and surname using an overloaded constructor, that uses Setters for setting the variables. The Constructor will check if the id is greater than 0 using a Custom Exception that gets thrown inside of the setId() function. Finally, we will do it right and print it out.


IdNotGreaterThanZeroException:


  




```
// Custom Exception
```


```
public class IdNotGreaterThanZeroException extends Exception { // IdNotGreaterThanZeroException.java
```


```
	public IdNotGreaterThanZeroException() {
```


```
		super("Id is less than or equal to zero!");
```


```
	}
```


```
}
```

  



Student:



```
// Object class that makes sure that id is > 0
```


```
public class Student { // Student.java
```


```
	private int id;
```


```
	private String name;
```


```
	private String surname;
```


```
	// Overloaded constructor
```


```
	public Student(int id, String name, String surname) {
```


```
		// try-catch statement for Exception Handling
```


```
		try {
```


```
			// We are trying to set the id
```


```
			setId(id);
```


```
		} catch (IdNotGreaterThanZeroException e) {
```


```
			// id was less than 0 and an Exception occurs
```


```
			System.out.println(e.getMessage()); // print error message
```


```
			return; // optional
```


```
		}
```


```
		setName(name);
```


```
		setSurname(surname);
```


```
	}
```


```
	// GETTERS-SETTERS
```


```
	public int getId() {
```


```
		return id;
```


```
	}
```


```
	// method that throws user-defined Exception
```


```
	public void setId(int id) throws IdNotGreaterThanZeroException {
```


```
		if (id < 0) {
```


```
			throw new IdNotGreaterThanZeroException();
```


```
		} else {
```


```
			this.id = id;
```


```
		}
```


```
	}
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
	public void setName(String name) {
```


```
		this.name = name;
```


```
	}
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
	public void setSurname(String surname) {
```


```
		this.surname = surname;
```


```
	}
```


```
	public String toString() {
```


```
		return id + " " + name + " " + surname;
```


```
	}
```


```
}
```

  



TestStudent:


  




```
public class TestStudent { // TestStudent.java
```


```
	public static void main(String[] args) {
```


```
		Student s;
```


```
		// put a negative id
```


```
		s = new Student(-5, "James", "Mcdonald");
```


```
		// while creating a new Student we caused an Exception
```


```
		// but it don't stopped the Code, because we caught it
```


```
		// inside of the setId() functions
```


```
		// and now we can re-do it right
```


```
		s = new Student(5, "James", "Mcdonald");
```


```
		System.out.println(s);
```


```
	}
```


```
}
```

   In this example it actually doesn't make so much sense to use an Custom Exception, but I think it is some good Code to understand how to use them. Next time we will get into Files and use Exceptions to check if a specific File exists before reading from it to prevent Errors.

* * *

## Java Language

<br>

{% include programming/java_topics.html %}

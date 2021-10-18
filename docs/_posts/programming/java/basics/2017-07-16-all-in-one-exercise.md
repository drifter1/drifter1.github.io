---
layout: default
title: All-in-One Exercise
description: Java All-in-One Exercise
thumbnail: /images/tutorials/programming/java.png
categories: [programming, java]
tags: [programming, java, basics]
permalink: /tutorials/:categories/:title
---

# Java All-in-One Exercise

* * *

![](https://ignite.apache.org/images/java.png)


   Today's post will be a Task that I had to do in my Univesity, simplified a little bit. I will upload the **Solution after 1 week** in another Post. I think it's pretty good for understading some things about Java a little bit better. It contains everything that we talked about in Posts so far. So, without further do here comes the Exercise.


# Exercise:


 Write a Programm in Java that manages the Property Charges of an Condominium (or Condo). Use Inheritance and Composition to create relationships between the Classes. Use Constructors, use Getters-Setters for all except the ArrayLists to make it easier. Use the toString() Method to make it easier to print out. The Programm must contain the following Classes:


**Condominium:**


id (integer)


address (Object of type Address)


list of Apartments (ArrayList)


administrator (Object of type Administrator)


expenditure (float)


  



**Apartment:**


condominumId (integer)


apartmentId (string of type floor\_apartmentnumber like this: 1\_2)


owner (Object of type Owner)


squareMetres (integer)


millRate (integer)


propertyCharges (float)


  



**Person:**


id (integer)


surname, name (strings)


address (Object of Type Address)


  



**Owner:**


all the stuff from Person +


apartment (Object of type Apartment)


  



**Administrator:**


all the stuff from Person +


condominium (Object of type Condominium)


  



**Address:**


city (string)


street (string)


number (integer)


zip (integer)


  



And a **Driver** class that will run the following menu infinitely:



```
1. Insert Administator/Condominium
```


```
2. Insert Owner/Apartment
```


```
3. Print All Apartments
```


```
4. Find Apartment using Code
```


```
5. Find Property charges of specific Owner
```


```
6. Calculate Expenditure of Condominium
```


```
7. Calculate/Print Property charges of all Apartments
```


```
8. Save to Text File
```


```
9. Load from Text File
```


```
10. Save to Serializable File
```


```
11. Load from Serializable File
```


```
0. Exit
```

It will also contains a list of Owners, the Administrator and Condominium (we only have one Administrator and one Condominium).


  



**Hints** for the menu:


1. Create an Object of type Administrator and Condominium and set each others CompositionPartner to each other.


2. Create an Object of type Owner and Apartment, set each others CompositionPartner and insert the Owner inside of the ArrayList in Driverclass and the Aparment inside of the ArrayList in Condominium.


5. Get an Owner id as input and print the charges of his apartment (6 need to be run before!)


6. Get the expenditure as input to make it easier


7. Set the apartments charges to [expenditure * millRate / 1000] and print those out afterwards, where the millRate will be calculated like this:


Floor 1 has weight 1.0 and as we go higher on the Floors we add 0.2 (Floor 3 has 1.4 = 1.0 + 0.2 * 2) and we multiply this weight value with the apartments squareMetres and divide it with the sum of the weight*squareMetres of all apartments in the Condominium. 


(millRate = (weight * squareMetres) / (Sum of weight * squareMetres of all apartments including this one)


10./11. need to have the Classes Serializable


  

Hope you have fun with it :)

* * *

## Java Language

<br>

{% include programming/java_topics.html %}
  

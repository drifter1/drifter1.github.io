---
layout: default
title: All-In-One Exercise Extended
description: Java All-In-One Exercise Extended
thumbnail: /images/tutorials/programming/java.png
categories: [programming, java]
tags: [programming, java, gui]
permalink: /tutorials/:categories/:title
---

# Java All-In-One Exercise Extended

* * *


![](http://d3gnp09177mxuh.cloudfront.net/tech-page-images/java.png)


    Before leaving for Vacation I would like to upload another Exercise. I will upload the Solution when I return. You have to do the same Exercise already posted [here](https://steemit.com/programming/@drifter1/programming-java-all-in-one-exercise) (solution is [here](https://steemit.com/programming/@drifter1/programming-java-all-in-one-exercise-solution)), but using a GUI. I will also talk about other Stuff that changes in this Task and how I did it, so that you can try doing it that way and fix our Code using my Solution afterwards.


#  Task Changes / Extensions:


* The Programm needs to work for more then one Condominium
* A Condominium needs to have at least 1 Admin, but it can have more now
* A Apartments needs to have at least 1 Owner, but it can have more now
* Our Menu will contain 2 new Options that are for inserting another Admin or Owner into an already set up Condo or Apartment
* Our Programm will be an GridLayout GUI Frame, where each Option will be accessed via JButtons that create a new JDialog (you could create new Frames if you like or even make the GUI be some other Layout that is splited into Options/Buttons and Dialog/Input Panel that display on each Option when it is selected)
* We will have our Driver extend JFrame and create an Object of type Driver to run it, so that we can afterwards using custom JButtons and JDialogs access our Condos, Owners, Apartments from the Driver Class in any of the other Classes.
* The Buttons and Dialogs used will be one class each, that will run an different Code, specified by the Name of the Component (String "numbers"), using a Switch Case Statement inside of the actionPerformed() function of the Button and the Constructor of the Dialog


  



Hope you have fun with it.


See ya soon :)


* * *

## Java Language

<br>

{% include programming/java_topics.html %}
  
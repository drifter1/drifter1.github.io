---
layout: default
title: Web Applets
description: Java Web Applets
thumbnail: /images/tutorials/programming/java.png
categories: [programming, java]
tags: [programming, java, gui]
permalink: /tutorials/:categories/:title
---

# Java Web Applets

* * *

![](https://www3.ntu.edu.sg/home/ehchua/programming/java/images/Applet_HelloWorld.gif)


    I'm back! :) And here we are again with another Tutorial. I wanted to upload the Solution, but I need more time to check some things inside the Code that doesn't seem to work right or are to complicated! Today, we will talk about **Java Applets for Browsers**. I will show you how to write the Code in Java and how you can call such an Applet using HTML inside of a Website. So, without further do, let's get started!


# Differences to normal Java Coding:


There are some major differences between Applets and Standalone Java Applications. 


Those are:


* An Applet extends the java.applet.Applet class
* There is no main method invoked neither defined
* Applets are designed to be run inside of an HTML Page


An Applet has an **Lifecycle** and we use the following methods to do stuff with it:


* **init()**, for initialization purposes, called first
* **start()**, that is called automatically after the init() method and whenever the user returns to the page containing the applet after gone off to other pages
* **stop()**, that is called automatically when the user moves off the page in which the applet sits
* **destroy()**, that is called when the browser shuts down normally
* **paint()**, that is invoked after the start() method and everytime the applet wants to repaint itself


    We don't have to write Code for any of the methods. The init method can be changed to initialize values, create or setup GUI Elements and so on... The most important one is paint that let's us draw our Applet.


# Basic Applet Structure:


    An basic Applet needs to extend the Applet (awt) or JApplet (swing) class and contains at least 2 methods called init() and paint().



```
import java.applet.Applet; // import javax.swing.JApplet
```


```
import java.awt.Graphics;
```


```
public class MyApplet extends Applet { // or JApplet 
```


```
    public void init() {
```


```
        // INITIALIZATIONS
```


```
    }
```


```
    public void paint(Graphics g) {
```


```
        // Draw the Applet using the Graphics g Object
```


```
    }
```


```
}
```

    Because, our Applet is an GUI Component/Element we can do stuff like resizing, setting Color, adding Frames, Panels, Buttons etc. the same way we did it with other GUI Elements. Using the draw methods that the Graphics Object inside of the paint method gives us, we can now draw even more stuff.


# Graphics Object:


    The Graphics Object contains many methods that let us draw Lines, Ovals, Rectangles, Strings in different Sizes, Places and Colors into the Applet. The Parameters specify the Locations in (x, y) pixel coordinates, where x and y are  0 in the top left of our applet and x indicating the width and y the height.


Some of those methods are:


* g.setColor(Color c) that let's us change the Color of our drawing "Tool"
* g.drawLine(x1, y1, x2, y2) that let's us draw a Line from (x1, y1) to (x2, y2)
* g.drawOval(x, y, width, height) that let's us draw a Oval with Center (x, y) and specific width, height
* g.drawRect(x, y, width, height) that let's us draw a Rectangle with Origin Point (x, y) and specific width and heigth values from there
* g.drawString(string, x, y) that let's us draw a String with Origin Point (x,y)


We could use all of those methods inside of loops to draw Mathematic Equations and other stuff we like.


# Example Applet:



```
import javax.swing.JApplet;
```


```
import java.awt.Graphics;
```


```
import java.awt.Color;
```


```
public class MyApplet extends JApplet { // MyApplet.java
```


```
	public void init() {
```


```
                // set up applet
```


```
		this.setSize(500, 500);
```


```
		this.setBackground(Color.white);
```


```
	}
```


```
	public void paint(Graphics g) {
```


```
		// drawing one time
```


```
		g.setColor(Color.black);
```


```
		g.drawLine(0, 50, 50, 100);
```


```
		g.drawString("Hello World!", 100, 200);
```


```
		g.drawOval(300, 300, 50, 50);
```


```
		g.drawRect(250, 150, 50, 100);
```


```
		// drawing with loops
```


```
		g.setColor(Color.orange);
```


```
		int counter = 1;
```


```
		while (counter <= 10) {
```


```
			g.drawLine(10, 10, 500, counter * 10);
```


```
			++counter;
```


```
		}
```


```
		g.setColor(Color.blue);
```


```
		for (int i = 0; i < 10; i++) {
```


```
			g.drawLine(0, 500, 500, i * 50);
```


```
		}
```


```
		g.setColor(Color.DARK_GRAY);
```


```
		for (int i = 0; i < 25; i++) {
```


```
			g.drawOval(250 - 10 * i, 250 - 10 * i, 20 * (i + 1), 20 * (i + 1));
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

# Invoke inside of a HTML Website:


To call an Applet inside of an HTML File we have to use the following Code:



```
[applet code = "MyApplet.class" width = "500" height = "500"]  

  

[/applet]
```

(change the [] with <>  from HTML!)


Where you can put more stuff inside then the width and height I put in this example!


  



This was the end of today's Tutorial! 


Hope you enjoyed it!


* * *

## Java Language

<br>

{% include programming/java_topics.html %}
  
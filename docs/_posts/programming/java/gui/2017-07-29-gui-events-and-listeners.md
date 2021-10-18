---
layout: default
title: Events and Listeners
description: Java GUI Events and Listeners
thumbnail: /images/tutorials/programming/java.png
categories: [programming, java]
tags: [programming, java, gui]
permalink: /tutorials/:categories/:title
---

# Java GUI Events and Listeners

* * *


![](https://www.tutorialspoint.com/swing/images/swing_button.jpg)


    After talking about the basic GUI Creation stuff we now take a look at **how we get input** from them that does all kinds of stuff using **Events** and **Listeners** (basically **Event** and **Action Listeners**). Getting input and doing stuff with it is not so difficult. We will simply use the **java.awt.event library** that contains everything that we need. So without further do let's get started. 


  



# Event Library:


    The event library contains **Classes and Interfaces** that can be used for getting different kinds of **Input**. The **Classes** are used to **define** what kind of Input we want and the **Interfaces** contain functions that **receive** and **process** the information from each type of Input. So our **Code** can cause an **Event** that we will handle using a **Listener** like this:


![](https://www.codeproject.com/KB/java/677591/EventModel.jpg)


The different **Events** and the **Listeners** we use for them are:


* ActionEvent -> ActionListener (for component defined action)
* AdjustmentEvent -> AdjustmentListener (for Scrollbar and ScrollPane adjustments)
* ComponentEvent -> ComponentListener (for moving, resizing, visibility changes of an component)
* ContainerEvent -> ContainerListener (for content changes like adding, removing a component in a container)
* FocusEvent -> FocusListener (for checking if a component lost or gained the input focus)
* HierarchyEvent -> HierarchyListener (for changes in the component hierarchy a component belongs to)
* InputMethodEvent -> InputMethodListener (for informations about text composition)
* ItemEvent -> ItemListener (for checking if an item was selected/deselected)
* KeyEvent -> KeyListener (for checking if a keystroke occured in a component)
* MouseEvent, MouseWheelEvent -> MouseListener, MouseMotionListener, MouseWheelListener (for checking if a certain mouse action occured in a component)
* TextEvent -> TextListener (for object text changes)
* WindowEvent -> WindowListener, WindowFocusListener, WindowStateListener (for status changes on a certain window)


You can take a deeper look [here](https://docs.oracle.com/javase/7/docs/api/java/awt/event/package-summary.html).


    All those Listeners are implementing the **EventListener Interface** from the java.util library, that defines the basic things that a Listener needs to have to listen to Events. And, even tho we use the awt library we can use the same Events and Listeners, cause the **Action Interface** used in the swing library is **implementing the ActionListener** from the awt library, and therefore also the EventListener.


  



# Handling Events:


    Handling Events is pretty simple. We simply have to add an Listener for an specific Event we want to handle at the Component that will cause it. We use a function called **addActionListener(l)** or **addKeyListener(l)** or **addMouseListener(l)** and so on.. and we could create the Listener beforehand and use it as a parameter or use a new Listener object that has a wierd syndax that will become more and more natural after using it for a while. When creating we will also implement all the functions of the interface (in an IDE it's pretty easy cause a icon appears on the left side).


Here two examples using the **ActionListener**:


**First Way:**



```
ActionListener l = new ActionListener(){
```


```
    @Override
```


```
    public void actionPerformed(ActionEvent event) {
```


```
        // TO DO
```


```
    }	
```


```
};
```


```
component_name.addActionListener(l);
```

  



**Second Way:**



```
component_name.addActionListener(new ActionListener() {
```


```
    @Override
```


```
    public void actionPerformed(ActionEvent event) {
```


```
        // TO DO
```


```
   }
```


```
});
```

  



# Coding Section:


    Let's first extend our previous GUI by adding a ActionListener on our Button and making it print the number of times it was pressed. After 50 times it will print a message using a JOptionPane and terminate our Programm.


## Code 1:



```
import javax.swing.*;
```


```
import java.awt.*;
```


```
import java.awt.event.*;
```


```
public class MyWindow {
```


```
    public static void main(String[] args) {
```


```
        // set up frame
```


```
	JFrame frame = new JFrame();
```


```
	frame.setSize(500, 500);
```


```
	frame.setTitle("MyWindow");
```


```
	frame.setBackground(Color.CYAN);
```


```
	frame.setLocationByPlatform(true);
```


```
	frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
```


```
  

```


```
	// set up panel
```


```
	JPanel panel = new JPanel();
```


```
	// set layout to 3x1 grid layout
```


```
	panel.setLayout(new GridLayout(3, 1));
```


```
  

```


```
	// set up label
```


```
	JLabel label = new JLabel("Hello World!");
```


```
	label.setHorizontalAlignment(JLabel.CENTER);
```


```
  

```


```
	// set up text field
```


```
	JTextField textfield = new JTextField();
```


```
	textfield.setText("Write what you want...");
```


```
  

```


```
	// set up button
```


```
	JButton button = new JButton();
```


```
	button.setBackground(Color.CYAN);
```


```
	button.setText("Press me!");
```


```
	// add ActionListener
```


```
	button.addActionListener(new ActionListener() {
```


```
		int times = 0;
```


```
		@Override
```


```
		public void actionPerformed(ActionEvent event) {
```


```
			times++;
```


```
			button.setText("You pressed me " + times + " times");
```


```
			// exit after 50 times
```


```
			if(times == 50){
```


```
				JOptionPane.showMessageDialog(null, "Enough!");
```


```
				System.exit(0);					
```


```
			}
```


```
		}
```


```
	});
```


```
  

```


```
	// add components to panel
```


```
	panel.add(label);
```


```
	panel.add(textfield);
```


```
	panel.add(button);
```


```
  

```


```
	// add panel to frame and make it visible
```


```
	frame.add(panel);
```


```
	frame.setVisible(true);
```


```
    }
```


```
}
```

  



    Let's now extend our previous GUI by setting the Text from our Label to be our TextField Text whenever we press the Button. If what we wrote was "Bye" then our Programm will terminate.


## Code 2:



```
import javax.swing.*;
```


```
import java.awt.*;
```


```
import java.awt.event.*;
```


```
public class MyWindow {
```


```
    public static void main(String[] args) {
```


```
	// set up frame
```


```
	JFrame frame = new JFrame();
```


```
	frame.setSize(500, 500);
```


```
	frame.setTitle("MyWindow");
```


```
	frame.setBackground(Color.CYAN);
```


```
	frame.setLocationByPlatform(true);
```


```
	frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
```


```
  

```


```
	// set up panel
```


```
	JPanel panel = new JPanel();
```


```
	// set layout to 3x1 grid layout
```


```
	panel.setLayout(new GridLayout(3, 1));
```


```
  

```


```
	// set up label
```


```
	JLabel label = new JLabel("Hello World!");
```


```
	label.setHorizontalAlignment(JLabel.CENTER);
```


```
  

```


```
	// set up text field
```


```
	JTextField textfield = new JTextField();
```


```
	textfield.setText("Write what you want...");
```


```
  

```


```
	// set up button
```


```
	JButton button = new JButton();
```


```
	button.setBackground(Color.CYAN);
```


```
	button.setText("Press me!");
```


```
	// add ActionListener
```


```
	button.addActionListener(new ActionListener() {
```


```
		@Override
```


```
		public void actionPerformed(ActionEvent event) {
```


```
			// set label text
```


```
			label.setText(textfield.getText());
```


```
			// exit if text is "Bye"
```


```
			if (label.getText().equals("Bye")) {
```


```
				JOptionPane.showMessageDialog(null, "Bye!");
```


```
				System.exit(0);
```


```
			}
```


```
		}
```


```
	});
```


```
  

```


```
	// add components to panel
```


```
	panel.add(label);
```


```
	panel.add(textfield);
```


```
	panel.add(button);
```


```
  

```


```
	// add panel to frame and make it visible
```


```
	frame.add(panel);
```


```
	frame.setVisible(true);
```


```
    }
```


```
}
```

  



That was the End of today's Post. Hope you enjoyed it. 


    I don't wanted to do more stuff than the basics today, but I will upload another Post tomorrow with some example GUI Programms and I will also use more Listeners and Events then the basic ActionListener and ActionEvent I used today. Bye :)


* * *

## Java Language

<br>

{% include programming/java_topics.html %}
  
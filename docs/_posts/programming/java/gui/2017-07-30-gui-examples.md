---
layout: default
title: GUI Examples
description: Java GUI Examples
thumbnail: /images/tutorials/programming/java.png
categories: [programming, java]
tags: [programming, java, gui]
permalink: /tutorials/:categories/:title
---

# Java GUI Examples

* * *


![](https://netbeans.org/images_www/articles/72/java/gui-functionality/Figure2.png)


    As promised this time I will show you some **example GUI's** using everything that we talked about! I will start out with an **simple Calculator**, then I will do an **Menu** and lastly I will make a **simple Game** where you have to find which Button is the winning one. So, without further do. Let's get started!


  



# **Code 1 (Calculator):**


I will create a GUI that let's you add, substract, multiply and divide 2 numbers. The 2 numbers will be double's and we will have two TextFields for the Number Input, 4 Buttons for each calculation and some Labels, where one will be for displaying the Answer or Error (we will surround our Code with a try-catch statement).



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
public class Calculator {
```


```
    static double num;
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
	frame.setTitle("Simple Calculator");
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
	// set layout to 5x2 grid layout
```


```
	panel.setLayout(new GridLayout(5, 2));
```


```
  

```


```
	// set up answer label
```


```
	JLabel answer = new JLabel();
```


```
  

```


```
	// set up number text fields
```


```
	JTextField num1 = new JTextField();
```


```
	JTextField num2 = new JTextField();
```


```
  

```


```
	// set up buttons
```


```
	JButton add = new JButton();
```


```
	add.setText("+");
```


```
	add.addActionListener(new ActionListener() {
```


```
		@Override
```


```
		public void actionPerformed(ActionEvent event) {
```


```
			try {
```


```
				num = Double.parseDouble(num1.getText())
```


```
				+ Double.parseDouble(num2.getText());
```


```
				answer.setText(Double.toString(num));
```


```
			} catch (Exception e) {
```


```
				answer.setText("Error!");
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
	JButton sub = new JButton();
```


```
	sub.setText("-");
```


```
	sub.addActionListener(new ActionListener() {
```


```
		@Override
```


```
		public void actionPerformed(ActionEvent event) {
```


```
			try {
```


```
				num = Double.parseDouble(num1.getText())
```


```
				- Double.parseDouble(num2.getText());
```


```
				answer.setText(Double.toString(num));
```


```
			} catch (Exception e) {
```


```
				answer.setText("Error!");
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
	JButton mul = new JButton();
```


```
	mul.setText("*");
```


```
	mul.addActionListener(new ActionListener() {
```


```
		@Override
```


```
		public void actionPerformed(ActionEvent event) {
```


```
			try {
```


```
				num = Double.parseDouble(num1.getText())
```


```
				* Double.parseDouble(num2.getText());
```


```
				answer.setText(Double.toString(num));
```


```
			} catch (Exception e) {
```


```
				answer.setText("Error!");
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
	JButton div = new JButton();
```


```
	div.setText("/");
```


```
	div.addActionListener(new ActionListener() {
```


```
		@Override
```


```
		public void actionPerformed(ActionEvent event) {
```


```
			try {
```


```
				num = Double.parseDouble(num1.getText())
```


```
				/ Double.parseDouble(num2.getText());
```


```
				answer.setText(Double.toString(num));
```


```
			} catch (Exception e) {
```


```
				answer.setText("Error!");
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
	panel.add(new JLabel("Number 1"));
```


```
	panel.add(new JLabel("Number 2"));
```


```
	panel.add(num1);
```


```
	panel.add(num2);
```


```
	panel.add(add);
```


```
	panel.add(sub);
```


```
	panel.add(mul);
```


```
	panel.add(div);
```


```
	panel.add(new JLabel("Answer"));
```


```
	panel.add(answer);
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

  



# Code 2 (Menu):


    Next Code will be a Switch Case like Menu that let's us do different kinds of stuff on an ArrayList of Integers. We will be able to fill list with random numbers,  add specific number to list, search for a number in list, print the list and exit the programm (we will be able to do it using X again tho).



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
import java.util.ArrayList;
```


```
public class Menu {
```


```
    public static void main(String[] args) {
```


```
	// define list
```


```
	ArrayList<Integer> list = new ArrayList<>();
```


```
  

```


```
	// set up frame
```


```
	JFrame frame = new JFrame();
```


```
	frame.setSize(300, 500);
```


```
	frame.setTitle("List Menu");
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
	// set layout to 5x1 grid layout
```


```
	panel.setLayout(new GridLayout(5, 1));
```


```
  

```


```
	// set up buttons
```


```
	JButton rand, add, search, print, exit;
```


```
	rand = new JButton("Fill List with Random Numbers");
```


```
	rand.addActionListener(new ActionListener() {
```


```
		@Override
```


```
		public void actionPerformed(ActionEvent e) {
```


```
			for (int i = 0; i < 20; i++) {
```


```
				// add random number of range [1,100)
```


```
				list.add((int) (1 + Math.random() * 100));
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
	add = new JButton("Add specific number to List");
```


```
	add.addActionListener(new ActionListener() {
```


```
		@Override
```


```
		public void actionPerformed(ActionEvent e) {
```


```
			int input;
```


```
			try {
```


```
				input = Integer.parseInt(JOptionPane.showInputDialog("Give me a number"));
```


```
				list.add(input);
```


```
			} catch (Exception ex) {
```


```
				JOptionPane.showMessageDialog(null, "An Error Occured!");
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
	search = new JButton("Search for a number in List");
```


```
	search.addActionListener(new ActionListener() {
```


```
		@Override
```


```
		public void actionPerformed(ActionEvent e) {
```


```
			int input;
```


```
			try {
```


```
				input = Integer.parseInt(JOptionPane.showInputDialog("Give me a number"));
```


```
				if (list.contains(input)) {
```


```
					JOptionPane.showMessageDialog(null, input + " was found!");
```


```
				} else {
```


```
					JOptionPane.showMessageDialog(null, input + " wasn't found!");
```


```
				}
```


```
			} catch (Exception ex) {
```


```
				JOptionPane.showMessageDialog(null, "An Error Occured!");
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
	print = new JButton("Print List");
```


```
	print.addActionListener(new ActionListener() {
```


```
		@Override
```


```
		public void actionPerformed(ActionEvent e) {
```


```
			String s = "";
```


```
			for (int i = 0; i < list.size(); i++) {
```


```
				s += list.get(i) + " ";
```


```
			}
```


```
			JOptionPane.showMessageDialog(null, "List: " + s);
```


```
		}
```


```
	});
```


```
	exit = new JButton("Exit");
```


```
	exit.addActionListener(new ActionListener() {
```


```
		@Override
```


```
		public void actionPerformed(ActionEvent e) {
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
	});
```


```
  

```


```
	// add components to panel
```


```
	panel.add(rand);
```


```
	panel.add(add);
```


```
	panel.add(search);
```


```
	panel.add(print);
```


```
	panel.add(exit);
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

  



# Code 3 (Game):


    We will have a 3x3 sized grid of tiles and one of those tiles/buttons will be defined as the winning one. To do this we will set the names of the buttons to be 0 and one Tile will be selected at random and get the name 1. We will start with 9 points and white buttons. The pressed ones will turn red if they are not the wining tile and our points will decrease by 1.



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
public class Game {
```


```
    static int points = 9;
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
	frame.setTitle("Game");
```


```
	frame.setLocationByPlatform(true);
```


```
	frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
```


```
	frame.setLayout(new BorderLayout());
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
	// set layout to 3x3 grid layout
```


```
	panel.setLayout(new GridLayout(3, 3));
```


```
  

```


```
	// set up point label
```


```
	JLabel point = new JLabel();
```


```
	point.setText("Points: 9");
```


```
  

```


```
	// set up buttons
```


```
	JButton[] buttons = new JButton[9];
```


```
	for (int i = 0; i < buttons.length; i++) {
```


```
		buttons[i] = new JButton();
```


```
		buttons[i].setName("0");
```


```
		buttons[i].setBackground(Color.WHITE);
```


```
		buttons[i].addActionListener(new ActionListener() {
```


```
			@Override
```


```
			public void actionPerformed(ActionEvent e) {
```


```
				// get source object
```


```
				JButton b = (JButton) e.getSource();
```


```
				// check if wining tile
```


```
				if (b.getName().equals("1")) {
```


```
					JOptionPane.showMessageDialog(null, "You won with " + points + " points");
```


```
					// set points
```


```
					point.setText("Points: 9");
```


```
					points = 9;
```


```
					// reset buttons
```


```
					for (int i = 0; i < buttons.length; i++) {
```


```
						buttons[i].setName("0");
```


```
						buttons[i].setBackground(Color.WHITE);
```


```
						buttons[i].setEnabled(true);
```


```
					}
```


```
					// random wining tile
```


```
					buttons[(int) (Math.random() * buttons.length)].setName("1");
```


```
					return;
```


```
				}
```


```
				// else
```


```
				points--;
```


```
				point.setText("Points: " + Integer.toString(points));
```


```
				b.setBackground(Color.RED);
```


```
				b.setEnabled(false);
```


```
			}
```


```
		});
```


```
	}
```


```
	// random wining tile
```


```
	buttons[(int) (Math.random() * buttons.length)].setName("1");
```


```
  

```


```
	// add components to panel
```


```
	for (int i = 0; i < buttons.length; i++) {
```


```
		panel.add(buttons[i]);
```


```
	}
```


```
  

```


```
	// add components to frame and make it visible
```


```
	frame.add(point, BorderLayout.NORTH);
```


```
	frame.add(panel, BorderLayout.CENTER);
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

  



That was the End of today's Post. I will upload C again for some days before going to vacation. We will do more Advanced Lists, Queues and Trees.


Hope you enjoyed it! Thank You! Bye :)


* * *

## Java Language

<br>

{% include programming/java_topics.html %}
  
---
layout: default
title: All-In-One Exercise Extended Solution
description: Java All-In-One Exercise Extended Solution
thumbnail: /images/tutorials/programming/java.png
categories: [programming, java]
tags: [programming, java, gui]
permalink: /tutorials/:categories/:title
---

# Java All-In-One Exercise Extended Solution

* * *


![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTQvbnBzsRDbsQ8GSmQQ39vljgrKKws0xkyx9Wi1yX-xLaSa6nN)


    I managed to fix some things so here the Solution to [this](https://steemit.com/programming/@drifter1/programming-java-all-in-one-exercise-extended) Exercise. [Here](https://steemit.com/programming/@drifter1/programming-java-all-in-one-exercise) you can find the previous Exercise and [here](https://steemit.com/programming/@drifter1/programming-java-all-in-one-exercise-solution) it's Solution. So, without further do, here comes the Solution.


# Solution:


    I already explained in the Exercise Post what I did to create all this. 


    Just to make things clear:


* There could be Bugs or Things everywhere, cause it is very difficult to test so many different things!
* You don't have to do everything exactly as I did it!
* This is just an example Solution and many things were edited very fast!
* This Exercise is not the exact same I had to do in my University, so I had to rewrite many things and it took a lot of time, so if anything doesn't work it is because I did some things fast, so that I can start out with different things for the upcoming days!


So, after this big shout out. Here the Coding :)


Address, Person, Owner and Administrator are the exact same as last time!


 Address:



```
import java.io.Serializable;
```


```
public class Address implements Serializable { // Address.java
```


```
    private String city;
```


```
    private String street;
```


```
    private int number;
```


```
    private int zip;
```


```
    // CONSTRUCTORS
```


```
    public Address() {
```


```
        city = null;
```


```
	street = null;
```


```
	number = -1;
```


```
	zip = -1;
```


```
    }
```


```
    public Address(String city, String street, int number, int zip) {
```


```
        this.city = city;
```


```
        this.street = street;
```


```
        this.number = number;
```


```
        this.zip = zip;
```


```
    }
```


```
    // GETTERS-SETTERS
```


```
    public String getCity() {
```


```
        return city;
```


```
    }
```


```
    public void setCity(String city) {
```


```
        this.city = city;
```


```
    }
```


```
    public String getStreet() {
```


```
        return street;
```


```
    }
```


```
    public void setStreet(String street) {
```


```
        this.street = street;
```


```
    }
```


```
    public int getNumber() {
```


```
        return number;
```


```
    }
```


```
    public void setStreetNumber(int number) {
```


```
        this.number = number;
```


```
    }
```


```
    public int getZip() {
```


```
        return zip;
```


```
    }
```


```
    public void setZip(int zip) {
```


```
        this.zip = zip;
```


```
    }
```


```
    // METHODS
```


```
    public String toString() {
```


```
        return city + "\n" + street + "\n" + number + " " + zip;
```


```
    }
```


```
}
```

Person:



```
import java.io.Serializable;
```


```
public class Person implements Serializable { // Person.java
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
    private Address a;
```


```
    // CONSTRUCTORS
```


```
    public Person() {
```


```
        id = -1;
```


```
        name = null;
```


```
        surname = null;
```


```
        a = null;
```


```
    }
```

`public Person(int id, String name, String surname, Address a) {`



```
        this.id = id;
```


```
        this.name = name;
```


```
        this.surname = surname;
```


```
	this.a = a;
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
    public void setId(int id) {
```


```
	this.id = id;
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
    public Address getA() {
```


```
        return a;
```


```
    }
```


```
    public void setA(Address a) {
```


```
	this.a = a;
```


```
    }	
```


```
    // METHODS
```


```
    public String toString() {
```


```
	return id + "\n" + name + "\n" + surname + "\n" + a.toString();
```


```
    }
```


```
}
```

Owner:



```
import java.io.Serializable;
```


```
public class Owner extends Person implements Serializable { // Owner.java
```


```
    private Apartment apartment;
```


```
    // CONSTRUCTORS
```


```
    public Owner() {
```


```
	   super();
```


```
    }
```


```
    public Owner(int id, String name, String surname, Address a) {
```


```
	super(id, name, surname, a);
```


```
    }
```


```
    // GETTERS-SETTERS
```


```
    public Apartment getApartment() {
```


```
	return apartment;
```


```
    }
```


```
    public void setApartment(Apartment apartment) {
```


```
	this.apartment = apartment;
```


```
    }
```


```
    // METHODS
```


```
    public String toString() {
```


```
	return super.toString();
```


```
    }	
```


```
}
```

Administrator:



```
import java.io.Serializable;
```


```
public class Administrator extends Person implements Serializable { // Administrator.java
```


```
    private Condominium condo;
```


```
    // CONSTRUCTORS
```


```
    public Administrator() {
```


```
	super();
```


```
    }
```


```
    public Administrator(int id, String name, String surname, Address a) {
```


```
    	super(id, name, surname, a);
```


```
    }
```


```
    // GETTERS-SETTERS
```


```
    public Condominium getCondo() {
```


```
	return condo;
```


```
    }
```


```
    public void setCondo(Condominium condo) {
```


```
	this.condo = condo;
```


```
    }
```


```
    // METHODS
```


```
    public String toString() {
```


```
	return super.toString();
```


```
    }
```


```
}
```

Apartment:



```
import java.io.Serializable;
```


```
import java.util.ArrayList;
```


```
import java.util.StringTokenizer;
```


```
public class Apartment implements Serializable { // Apartment.java
```


```
    private int condominiumID;
```


```
    private String apartmentID;
```


```
    ArrayList<Owner> owners = new ArrayList<>();
```


```
    private int squareMeters;
```


```
    private int millRate;
```


```
    private double propertyCharges;
```


```
    // CONSTRUCTORS
```


```
    public Apartment() {
```


```
        condominiumID = -1;
```


```
        apartmentID = null;
```


```
	squareMeters = -1;
```


```
	millRate = 0;
```


```
	propertyCharges = 0.0;
```


```
    }
```


```
    // 2 overloaded Constructors to make it easier for File Reading
```


```
    public Apartment(int condominiumID, String apartmentID, int squareMeters) {
```


```
	this.condominiumID = condominiumID;
```


```
	this.apartmentID = apartmentID;
```


```
	this.squareMeters = squareMeters;
```


```
	millRate = calculateMillRate();
```


```
	propertyCharges = 0;
```


```
    }
```


```
    public Apartment(int condominiumID, String apartmentID, int squareMeters, int millRate, double propertyCharges) {
```


```
	this.condominiumID = condominiumID;
```


```
	this.apartmentID = apartmentID;
```


```
	this.squareMeters = squareMeters;
```


```
	this.millRate = millRate;
```


```
	this.propertyCharges = propertyCharges;
```


```
    }
```


```
    // GETTERS-SETTERS
```


```
    public int getCondominiumID() {
```


```
	return condominiumID;
```


```
    }
```


```
    public void setCondominiumID(int condominiumID) {
```


```
	this.condominiumID = condominiumID;
```


```
    }
```


```
    public String getApartmentID() {
```


```
	return apartmentID;
```


```
    }
```


```
    public void setApartmentID(String apartmentID) {
```


```
	this.apartmentID = apartmentID;
```


```
    }
```


```
    public int getSquareMeters() {
```


```
	return squareMeters;
```


```
    }
```


```
    public void setSquareMeters(int squareMeters) {
```


```
	this.squareMeters = squareMeters;
```


```
    }
```


```
    public int getMillRate() {
```


```
	return millRate;
```


```
    }
```


```
    public void setMillRate(int millRate) {
```


```
	this.millRate = millRate;
```


```
    }
```


```
    public double getPropertyCharges() {
```


```
	return propertyCharges;
```


```
    }
```


```
    public void setPropertyCharges(double propertyCharges) {
```


```
	this.propertyCharges = propertyCharges;
```


```
    }
```


```
    // METHODS
```


```
    public int calculateMillRate() {
```


```
	int apartmentMilm;
```


```
	// find condo in which the apartment belongs
```


```
	Condominium c = null;
```


```
	for (int i = 0; i < Driver.driver.condos.size(); i++) {
```


```
		if (Driver.driver.condos.get(i).getId() == condominiumID) {
```


```
			c = Driver.driver.condos.get(i);
```


```
		}
```


```
	}
```


```
	int N = c.apartments.size();
```


```
	if (N == 0) {
```


```
		return 1000;
```


```
	}
```


```
	double[] weight = new double[N + 1];
```


```
	// loop all apartments to calculate weight
```


```
	for (int i = 0; i < N; i++) {
```


```
		weight[i] = c.apartments.get(i).getSquareMeters();
```


```
		// we use an object that does the same as strtok() in C
```


```
		// and splits the String where a specific character appears
```


```
                StringTokenizer strTok = new StringTokenizer(c.apartments.get(i).getApartmentID(), "_");
```


```
		// we get the first "number" that represents the floor
```


```
		// and convert it to an Integer
```


```
		int floor = Integer.parseInt(strTok.nextToken());
```


```
		weight[i] = weight[i] * (1 + ((floor - 1) * 0.2));
```


```
	}
```


```
	// the new apartment
```


```
	StringTokenizer strTok = new StringTokenizer(apartmentID, "_");
```


```
	int floor = Integer.parseInt(strTok.nextToken());
```


```
	weight[N] = squareMeters * (1 + ((floor - 1) * 0.2));
```


```
	// calculate sum of weights
```


```
	double sumWeight = 0;
```


```
	for (int i = 0; i < N + 1; i++) {
```


```
		sumWeight += weight[i];
```


```
	}
```


```
	// recalculate millRate of all apartments
```


```
	for (int i = 0; i < N; i++) {
```


```
		c.apartments.get(i).setMillRate((int) ((weight[i] / sumWeight)));
```


```
	}
```


```
	// calculate apartment's millRate
```


```
	apartmentMilm = (int) ((weight[N] / sumWeight));
```


```
	return apartmentMilm;
```


```
    }
```


```
    public String toString() {
```


```
	return condominiumID + "\n" + apartmentID + "\n" + squareMeters + " " + millRate + " " + propertyCharges;
```


```
    }
```


```
}
```

Condominium:



```
import java.io.Serializable;
```


```
import java.util.ArrayList;
```


```
import javax.swing.JOptionPane;
```


```
public class Condominium implements Serializable { // Condominium.java
```


```
    private int id;
```


```
    private Address a;
```


```
    ArrayList<Administrator> admins = new ArrayList<>();
```


```
    ArrayList<Owner> owners = new ArrayList<>();
```


```
    ArrayList<Apartment> apartments = new ArrayList<>();
```


```
    private double expenditure;
```


```
    // CONSTRUCTORS
```


```
    public Condominium() {
```


```
	id = -1;
```


```
	a = null;
```


```
	expenditure = 0.0;
```


```
    }
```


```
    public Condominium(int id, Address a) {
```


```
	this.id = id;
```


```
	this.a = a;
```


```
	expenditure = 0.0;
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
    public void setId(int id) {
```


```
	this.id = id;
```


```
    }
```


```
    public Address getA() {
```


```
	return a;
```


```
    }
```


```
    public void setA(Address a) {
```


```
	this.a = a;
```


```
    }
```


```
    // expenditure will be inputed with another method
```


```
    // METHODS
```


```
    public boolean findApartment(String apartmentcode) {
```


```
	for (int i = 0; i < apartments.size(); i++) {
```


```
		// checking equality of strings
```


```
		if (apartmentcode.equals(apartments.get(i).getApartmentID())) {
```


```
			JOptionPane.showMessageDialog(null, "Apartment:\n" + apartments.get(i));
```


```
			return true;
```


```
		}
```


```
	}
```


```
	return false;
```


```
    }
```


```
    public void printApartments() {
```


```
	String temp = "Condo " + id + " has:\n";
```


```
	for (int i = 0; i < apartments.size(); i++) {
```


```
		temp += apartments.get(i) + "\n";
```


```
	}
```


```
	JOptionPane.showMessageDialog(null, temp);
```


```
    }
```


```
    public void setCondominiumPropertyCharges(int condominiumCode, double expenditure) {
```


```
	if (condominiumCode == this.id) {
```


```
		this.expenditure = expenditure;
```


```
	} else {
```


```
		JOptionPane.showMessageDialog(null, "No Condominium has the id " + condominiumCode);
```


```
	}
```


```
    }
```


```
    public void apartmentPropertyCharges() {
```


```
	for (int i = 0; i < apartments.size(); i++) {
```


```
		apartments.get(i).setPropertyCharges(expenditure * apartments.get(i).getMillRate() / 1000);
```


```
	}
```


```
    }
```


```
    public String toString() {
```


```
	return id + "\n" + a.toString() + "\n" + expenditure;
```


```
    }
```


```
}
```

Now the Last 3 Are for the GUI


Driver:



```
import java.awt.GridLayout;
```


```
import java.io.*;
```


```
import java.util.ArrayList;
```


```
import javax.swing.*;
```


```
public class Driver extends JFrame { // Driver.java
```


```
    ArrayList<Condominium> condos = new ArrayList<>();
```


```
    static Driver driver;
```


```
    public static void main(String[] args) {
```


```
	driver = new Driver("Condominium Programm");
```


```
    }
```


```
    // CONSTRUCTOR
```


```
    public Driver(String title) {
```


```
	// set up frame
```


```
	this.setTitle(title);
```


```
	this.setSize(500, 700);
```


```
	this.setResizable(false);
```


```
	this.setLocationByPlatform(true);
```


```
	this.setDefaultCloseOperation(EXIT_ON_CLOSE);
```


```
	this.setLayout(new GridLayout(14, 1));
```


```
	// set up Custom "Choice" Buttons
```


```
	Choice[] choices = new Choice[14];
```


```
	for (int i = 0; i < choices.length; i++) {
```


```
		choices[i] = new Choice();
```


```
		choices[i].setName(Integer.toString(i));
```


```
	}
```


```
	choices[0].setText("1. Insert Administator/Condominium");
```


```
	choices[1].setText("2. Insert Owner/Apartment");
```


```
	choices[2].setText("3. Add an Admin to a Condominium");
```


```
	choices[3].setText("4. Add an Owner to an Apartment");
```


```
	choices[4].setText("5. Print All Apartments");
```


```
	choices[5].setText("6. Find Apartment using Code");
```


```
	choices[6].setText("7. Find Property charges of specific Owner");
```


```
	choices[7].setText("8. Calculate Expenditure of all Condos");
```


```
	choices[8].setText("9. Calculate/Print Property charges of all Apartments");
```


```
	choices[9].setText("10. Save to Text File");
```


```
	choices[10].setText("11. Load from Text File");
```


```
	choices[11].setText("12. Save to Serializable File");
```


```
	choices[12].setText("13. Load from Serializable File");
```


```
	choices[13].setText("0. Exit");
```


```
	for (int i = 0; i < choices.length; i++) {
```


```
		this.add(choices[i]);
```


```
	}
```


```
	this.setVisible(true);
```


```
    }
```


```
}
```

Choice:



```
import java.awt.event.ActionEvent;
```


```
import java.awt.event.ActionListener;
```


```
import java.io.*;
```


```
import java.util.Scanner;
```


```
import javax.swing.JButton;
```


```
import javax.swing.JOptionPane;
```


```
public class Choice extends JButton implements ActionListener {
```


```
    // CONSTRUCTOR
```


```
    Choice() {
```


```
	addActionListener(this);
```


```
    }
```


```
    @Override
```


```
    public void actionPerformed(ActionEvent e) {
```


```
	// get name of Button and run specified action
```


```
	switch (this.getName()) {
```


```
	// on all those Cases we create an "Input" JDialog Window
```


```
	case "0": // Insert Administator/Condominium
```


```
	case "1": // Insert Owner/Apartment
```


```
	case "2": // Add an Admin to a Condominium
```


```
	case "3": // Add an Owner to an Apartment"
```


```
		new Input(this.getName());
```


```
		break;
```


```
	case "4": // Print All Apartments
```


```
		printApartments();
```


```
		break;
```


```
	case "5": // Find Apartment using Code
```


```
		String apartmentcode = JOptionPane.showInputDialog("Give Apartment Code");
```


```
		findApartmentCharges(apartmentcode);
```


```
		break;
```


```
	case "6": // Find Property charges of specific Owner
```


```
		int id = Integer.parseInt(JOptionPane.showInputDialog("Give an Owner ID"));
```


```
		findPropertyCharges(id);
```


```
		break;
```


```
	// in this 2 Cases we create an "Input" JDialog Window
```


```
	case "7": // Calculate Expenditure of all Condos
```


```
	case "8": // Calculate/Print Property charges of all Apartments
```


```
		new Input(this.getName());
```


```
		break;
```


```
	case "9": // Save to Text File
```


```
		writeToTextFile();
```


```
		break;
```


```
	case "10": // Load from Text File
```


```
		readFromTextFile();
```


```
		break;
```


```
	case "11": // Save to Serializable File
```


```
		writeToSerializableFile();
```


```
		break;
```


```
	case "12": // Load from Serializable File
```


```
		readFromSerializableFile();
```


```
		break;
```


```
	case "13": // Exit
```


```
		System.exit(0);
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
    // METHODS
```


```
    public void printApartments() {
```


```
	if (Driver.driver.condos.size() == 0) {
```


```
		JOptionPane.showMessageDialog(null, "No Condos/Apartments Inserted");
```


```
		return;
```


```
	}
```


```
	for (int i = 0; i < Driver.driver.condos.size(); i++) {
```


```
		Driver.driver.condos.get(i).printApartments();
```


```
	}
```


```
    }
```


```
    public void findApartmentCharges(String id) {
```


```
	boolean found = false;
```


```
	for (int i = 0; i < Driver.driver.condos.size(); i++) {
```


```
		found = Driver.driver.condos.get(i).findApartment(id);
```


```
		if (found == true) {
```


```
			return;
```


```
		}
```


```
	}
```


```
	if (found == false) {
```


```
		JOptionPane.showMessageDialog(null, "No Apartment has the id " + id);
```


```
	}
```


```
    }
```


```
    public void findPropertyCharges(int id) {
```


```
	for (int i = 0; i < Driver.driver.condos.size(); i++) {
```


```
		for (int j = 0; j < Driver.driver.condos.get(i).owners.size(); j++) {
```


```
			// check equality of ids
```


```
			if (Driver.driver.condos.get(i).owners.get(j).getId() == id) {
```


```
				JOptionPane.showMessageDialog(null, "Owner with id " + id + " has to pay "
```


```
	+ Driver.driver.condos.get(i).owners.get(j).getApartment().getPropertyCharges());
```


```
				return;
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
	JOptionPane.showMessageDialog(null, "No Owner has the id " + id);
```


```
    }
```


```
    public void writeToTextFile() {
```


```
	try {
```


```
		PrintWriter writer = new PrintWriter(new FileOutputStream("condominium.txt"));
```


```
		// write num of Condos
```


```
		writer.println(Driver.driver.condos.size());
```


```
		// write each Condo separatly
```


```
		for (int i = 0; i < Driver.driver.condos.size(); i++) {
```


```
			Condominium c = Driver.driver.condos.get(i);
```


```
			writer.println(c.toString());
```


```
			// admin data
```


```
			writer.println(c.admins.size());
```


```
			for (int j = 0; j < c.admins.size(); j++) {
```


```
				writer.println(c.admins.get(j));
```


```
			}
```


```
			// apartment data
```


```
			writer.println(c.apartments.size());
```


```
			for (int j = 0; j < c.apartments.size(); j++) {
```


```
				Apartment a = c.apartments.get(j);
```


```
				writer.println(a.toString());
```


```
				// owner of apartments
```


```
				writer.println(a.owners.size());
```


```
				for (int k = 0; k < a.owners.size(); k++) {
```


```
					writer.println(a.owners.get(k));
```


```
				}
```


```
			}
```


```
			// we don't write the owner list
```


```
			// we will do it in another way
```


```
			// while reading
```


```
		}
```


```
		writer.close();
```


```
	} catch (IOException ioe) {
```


```
		JOptionPane.showMessageDialog(null, ioe.getMessage());
```


```
	}
```


```
    }
```


```
    public void readFromTextFile() {
```


```
	try {
```


```
		Scanner reader = new Scanner(new FileInputStream("condominium.txt"));
```


```
		// read size
```


```
		int num = Integer.parseInt(reader.nextLine());
```


```
		// read each Condo seperately
```


```
		for (int i = 0; i < num; i++) {
```


```
			// read condo data
```


```
			int tempCondoID = Integer.parseInt(reader.nextLine());
```


```
			// address
```


```
			String tempCity = reader.nextLine();
```


```
			String tempStreet = reader.nextLine();
```


```
			int tempStreetNumber = reader.nextInt();
```


```
			int tempPostalCode = reader.nextInt();
```


```
			reader.nextLine();
```


```
			Address tempA = new Address(tempCity, tempStreet, tempStreetNumber, tempPostalCode);
```


```
			Condominium condo = new Condominium(tempCondoID, tempA);
```


```
			// expenditure
```


```
			condo.setCondominiumPropertyCharges(tempCondoID, Double.parseDouble(reader.nextLine()));
```


```
			// admin data
```


```
			int num2 = Integer.parseInt(reader.nextLine());
```


```
			for (int j = 0; j < num2; j++) {
```


```
				int tempAdminID = Integer.parseInt(reader.nextLine());
```


```
				String tempName = reader.nextLine();
```


```
				String tempSurname = reader.nextLine();
```


```
				// address
```


```
				tempCity = reader.nextLine();
```


```
				tempStreet = reader.nextLine();
```


```
				tempStreetNumber = reader.nextInt();
```


```
				tempPostalCode = reader.nextInt();
```


```
				reader.nextLine();
```


```
				Address tempA2 = new Address(tempCity, tempStreet, tempStreetNumber, tempPostalCode);
```


```
				// add admin to condo
```


```
				Administrator admin = new Administrator(tempAdminID, tempName, tempSurname, tempA2);
```


```
				condo.admins.add(admin);
```


```
			}
```


```
			// apartment data
```


```
			int num3 = Integer.parseInt(reader.nextLine());
```


```
			for (int j = 0; j < num3; j++) {
```


```
				tempCondoID = Integer.parseInt(reader.nextLine());
```


```
				String tempApartmentID = reader.nextLine();
```


```
				int tempSquareMeters = reader.nextInt();
```


```
				int tempMillRate = reader.nextInt();
```


```
				double tempPropertyCharges = Double.parseDouble(reader.nextLine());
```


```
				Apartment a = new Apartment(tempCondoID, tempApartmentID, 
```


```
tempSquareMeters, tempMillRate, tempPropertyCharges);
```


```
				// read owner data
```


```
				int num4 = Integer.parseInt(reader.nextLine());
```


```
				for (int k = 0; k < num4; k++) {
```


```
					int tempOwnerID = Integer.parseInt(reader.nextLine());
```


```
					String tempName = reader.nextLine();
```


```
					String tempSurname = reader.nextLine();
```


```
					// address
```


```
					tempCity = reader.nextLine();
```


```
					tempStreet = reader.nextLine();
```


```
					tempStreetNumber = reader.nextInt();
```


```
					tempPostalCode = reader.nextInt();
```


```
					reader.nextLine();
```


```
					Address tempA3 = new Address(tempCity, tempStreet, tempStreetNumber, tempPostalCode);
```


```
					// add owner to apartment and condo
```


```
					Owner tempOwner = new Owner(tempOwnerID, tempName, tempSurname, tempA3);
```


```
					a.owners.add(tempOwner);
```


```
					condo.owners.add(tempOwner);
```


```
				}
```


```
				// add apartment to condo
```


```
				condo.apartments.add(a);
```


```
			}
```


```
			// add condo to condo list
```


```
			Driver.driver.condos.add(condo);
```


```
		}
```


```
		reader.close();
```


```
	} catch (IOException ioe) {
```


```
		JOptionPane.showMessageDialog(null, ioe.getMessage());
```


```
	}
```


```
    }
```


```
    public void writeToSerializableFile() {
```


```
	try {
```


```
		ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("condominium.dat"));
```


```
		// write condos
```


```
		oos.writeInt(Driver.driver.condos.size());
```


```
		for (int i = 0; i < Driver.driver.condos.size(); i++) {
```


```
			oos.writeObject(Driver.driver.condos.get(i));
```


```
		}
```


```
		oos.close();
```


```
	} catch (IOException ioe) {
```


```
		JOptionPane.showMessageDialog(null, ioe.getMessage());
```


```
	}
```


```
    }
```


```
    public void readFromSerializableFile() {
```


```
	try {
```


```
		ObjectInputStream ois = new ObjectInputStream(new FileInputStream("condominium.dat"));
```


```
		// read condos
```


```
		int num = ois.readInt();
```


```
		for (int i = 0; i < num; i++) {
```


```
			Driver.driver.condos.add((Condominium) ois.readObject());
```


```
		}
```


```
		ois.close();
```


```
	} catch (IOException | ClassNotFoundException ioe) {
```


```
		JOptionPane.showMessageDialog(null, ioe.getMessage());
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

Input:



```
import java.awt.GridLayout;
```


```
import javax.swing.*;
```


```
import java.awt.event.ActionEvent;
```


```
import java.awt.event.ActionListener;
```


```
public class Input extends JDialog {
```


```
    // CONSTRUCTOR
```


```
    public Input(String name) {
```


```
	// get name of button that called it
```


```
	// to create the right type of Input
```


```
	switch (name) {
```


```
	case "0": // Insert Administator/Condominium
```


```
		this.setTitle("Insert Administrator/Condiminium");
```


```
		this.setSize(600, 400);
```


```
		this.setLayout(new GridLayout(8, 2));
```


```
		// add Labels
```


```
		this.add(new JLabel("Admin"));
```


```
		this.add(new JLabel("Condo"));
```


```
		// add TextFields
```


```
		JTextField[] texts = new JTextField[12];
```


```
		for (int i = 0; i < texts.length; i++) {
```


```
			texts[i] = new JTextField();
```


```
			texts[i].setText("");
```


```
		}
```


```
		for (int i = 0; i < 10; i++) {
```


```
			this.add(texts[i]);
```


```
		}
```


```
		this.add(texts[10]);
```


```
		this.add(new JLabel(""));
```


```
		this.add(texts[11]);
```


```
		// add Button
```


```
		JButton button = new JButton("OK");
```


```
		button.addActionListener(new ActionListener() {
```


```
			@Override
```


```
			public void actionPerformed(ActionEvent e) {
```


```
				for (int i = 0; i < texts.length; i++) {
```


```
					if (texts[i].getText().equals("")) {
```


```
						JOptionPane.showMessageDialog(null, "Please Fill All TextFields!");
```


```
						return;
```


```
					}
```


```
				}
```


```
				// get Text from TextFields and convert it if needed
```


```
				Address a1 = new Address(texts[6].getText(), texts[8].getText(),
```


```
				Integer.parseInt(texts[10].getText()), Integer.parseInt(texts[11].getText()));
```


```
				Address a2 = new Address(texts[3].getText(), texts[5].getText(),
```


```
				Integer.parseInt(texts[7].getText()), Integer.parseInt(texts[9].getText()));
```


```
				Administrator admin = new Administrator(Integer.parseInt(texts[0].getText()), texts[2].getText(),
```


```
				texts[4].getText(), a1);
```


```
				Condominium condo = new Condominium(Integer.parseInt(texts[1].getText()), a2);
```


```
				// set composition partners
```


```
				admin.setCondo(condo);
```


```
				condo.admins.add(admin);
```


```
				// add Condo to Driver
```


```
				Driver.driver.condos.add(condo);
```


```
				Input.this.setVisible(false);
```


```
				Input.this.dispose();
```


```
			}
```


```
		});
```


```
		this.add(button);
```


```
		this.setVisible(true);
```


```
		break;
```


```
	case "1": // Insert Owner/Apartment
```


```
		this.setTitle("Insert Owner/Apartment");
```


```
		this.setSize(600, 400);
```


```
		this.setLayout(new GridLayout(8, 2));
```


```
		// add Labels
```


```
		this.add(new JLabel("Owner"));
```


```
		this.add(new JLabel("Apartment"));
```


```
		// add TextFields
```


```
		JTextField[] texts2 = new JTextField[10];
```


```
		for (int i = 0; i < texts2.length; i++) {
```


```
			texts2[i] = new JTextField();
```


```
			texts2[i].setText("");
```


```
		}
```


```
		for (int i = 0; i < 7; i++) {
```


```
			this.add(texts2[i]);
```


```
		}
```


```
		this.add(new JLabel(""));
```


```
		this.add(texts2[7]);
```


```
		this.add(new JLabel(""));
```


```
		this.add(texts2[8]);
```


```
		this.add(new JLabel(""));
```


```
		this.add(texts2[9]);
```


```
		// add Button
```


```
		JButton button2 = new JButton("OK");
```


```
		button2.addActionListener(new ActionListener() {
```


```
			@Override
```


```
			public void actionPerformed(ActionEvent e) {
```


```
				for (int i = 0; i < texts2.length; i++) {
```


```
					if (texts2[i].getText().equals("")) {
```


```
						JOptionPane.showMessageDialog(null, "Please Fill All TextFields!");
```


```
						return;
```


```
					}
```


```
				}
```


```
				// get Text from TextFields and convert it if needed
```


```
				Address a3 = new Address(texts2[6].getText(), texts2[7].getText(),
```


```
				Integer.parseInt(texts2[8].getText()), Integer.parseInt(texts2[9].getText()));
```


```
				Owner owner = new Owner(Integer.parseInt(texts2[0].getText()), texts2[2].getText(),
```


```
				texts2[4].getText(), a3);
```


```
				Apartment a = new Apartment(Integer.parseInt(texts2[1].getText()), texts2[3].getText(),
```


```
				Integer.parseInt(texts2[5].getText()));
```


```
				// set composition partners
```


```
				owner.setApartment(a);
```


```
				a.owners.add(owner);
```


```
				// add Owner and Apartment to Condo
```


```
				for (int i = 0; i < Driver.driver.condos.size(); i++) {
```


```
					if (Driver.driver.condos.get(i).getId() == a.getCondominiumID()) {
```


```
					Driver.driver.condos.get(i).owners.add(owner);
```


```
					Driver.driver.condos.get(i).apartments.add(a);
```


```
						Input.this.setVisible(false);
```


```
						Input.this.dispose();
```


```
						return;
```


```
					}
```


```
				}
```


```
				JOptionPane.showMessageDialog(null, "No Condominium has this ID!");
```


```
			}
```


```
		});
```


```
		this.add(button2);
```


```
		this.setVisible(true);
```


```
		break;
```


```
	case "2": // Add an Admin to a Condominium
```


```
		this.setTitle("Add an Admin to a Condominium");
```


```
		this.setSize(600, 500);
```


```
		this.setLayout(new GridLayout(8, 1));
```


```
		// add Textfields
```


```
		JTextField[] texts3 = new JTextField[7];
```


```
		for (int i = 0; i < texts3.length; i++) {
```


```
			texts3[i] = new JTextField();
```


```
			texts3[i].setText("");
```


```
			this.add(texts3[i]);
```


```
		}
```


```
		// add Button
```


```
		JButton button3 = new JButton("OK");
```


```
		button3.addActionListener(new ActionListener() {
```


```
			@Override
```


```
			public void actionPerformed(ActionEvent e) {
```


```
				Address a4 = new Address(texts3[3].getText(), texts3[4].getText(),
```


```
				Integer.parseInt(texts3[5].getText()), Integer.parseInt(texts3[6].getText()));
```


```
				Administrator admin2 = new Administrator(Integer.parseInt(texts3[0].getText()), texts3[1].getText(),
```


```
				texts3[2].getText(), a4);
```


```
				int condo_id = Integer.parseInt(JOptionPane.showInputDialog("Give Condo ID"));
```


```
				for (int i = 0; i < Driver.driver.condos.size(); i++) {
```


```
					Condominium c = Driver.driver.condos.get(i);
```


```
					if (c.getId() == condo_id) {
```


```
						c.admins.add(admin2);
```


```
						Input.this.setVisible(false);
```


```
						Input.this.dispose();
```


```
						return;
```


```
					}
```


```
				}
```


```
				JOptionPane.showMessageDialog(null, "No Condo has this ID");
```


```
			}
```


```
		});
```


```
		this.add(button3);
```


```
		this.setVisible(true);
```


```
		break;
```


```
	case "3": // Add an Owner to an Apartment"
```


```
		this.setTitle("Add an Owner to an Apartment");
```


```
		this.setSize(600, 500);
```


```
		this.setLayout(new GridLayout(8, 1));
```


```
		// add Textfields
```


```
		JTextField[] texts4 = new JTextField[7];
```


```
		for (int i = 0; i < texts4.length; i++) {
```


```
			texts4[i] = new JTextField();
```


```
			texts4[i].setText("");
```


```
			this.add(texts4[i]);
```


```
		}
```


```
		// add Button
```


```
		JButton button4 = new JButton("OK");
```


```
		button4.addActionListener(new ActionListener() {
```


```
			@Override
```


```
			public void actionPerformed(ActionEvent e) {
```


```
				Address a5 = new Address(texts4[3].getText(), texts4[4].getText(),
```


```
				Integer.parseInt(texts4[5].getText()), Integer.parseInt(texts4[6].getText()));
```


```
				Owner owner = new Owner(Integer.parseInt(texts4[0].getText()), texts4[1].getText(),
```


```
				texts4[2].getText(), a5);
```


```
				String apartment_id = JOptionPane.showInputDialog("Give Apartment ID");
```


```
				for (int i = 0; i < Driver.driver.condos.size(); i++) {
```


```
					Condominium c = Driver.driver.condos.get(i);
```


```
					for (int j = 0; j < c.apartments.size(); j++) {
```


```
						if (c.apartments.get(j).getApartmentID().equals(apartment_id)) {
```


```
							c.owners.add(owner);
```


```
						c.apartments.get(j).owners.add(owner);
```


```
							Input.this.setVisible(false);
```


```
							Input.this.dispose();
```


```
							return;
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
				JOptionPane.showMessageDialog(null, "No Apartment has this ID");
```


```
			}
```


```
		});
```


```
		this.add(button4);
```


```
		break;
```


```
	case "7": // Calculate Expenditure of all Condos
```


```
		this.setTitle("Calculate Expenditure of all Condos");
```


```
		this.setSize(400, 300);
```


```
		this.setLayout(new GridLayout(Driver.driver.condos.size() + 1, 2));
```


```
		// add TextFields
```


```
		JTextField[] texts5 = new JTextField[Driver.driver.condos.size()];
```


```
		for (int i = 0; i < texts5.length; i++) {
```


```
			texts5[i] = new JTextField();
```


```
			texts5[i].setText("");
```


```
			this.add(new JLabel("Condo " + Driver.driver.condos.get(i).getId()));
```


```
			this.add(texts5[i]);
```


```
		}
```


```
		// add Button
```


```
		JButton button5 = new JButton("OK");
```


```
		button5.addActionListener(new ActionListener() {
```


```
			@Override
```


```
			public void actionPerformed(ActionEvent e) {
```


```
				for (int i = 0; i < texts5.length; i++) {
```


```
					if (texts5[i].getText().equals("")) {
```


```
						JOptionPane.showMessageDialog(null, "Please Fill All TextFields!");
```


```
						return;
```


```
					}
```


```
				}
```


```
				// get Text from TextFields and convert it if needed
```


```
				for (int i = 0; i < texts5.length; i++) {
```


```
					Condominium c = Driver.driver.condos.get(i);
```


```
					c.setCondominiumPropertyCharges(c.getId(), Double.parseDouble(texts5[i].getText()));
```


```
				}
```


```
				Input.this.setVisible(false);
```


```
				Input.this.dispose();
```


```
			}
```


```
		});
```


```
		this.add(button5);
```


```
		this.setVisible(true);
```


```
		break;
```


```
	case "8": // Calculate/Print Property charges of all Apartments
```


```
                this.setTitle("Calculate/Print Property charges of all Apartments");
```


```
		this.setSize(300, 600);
```


```
		int num = 0;
```


```
		for (int i = 0; i < Driver.driver.condos.size(); i++) {
```


```
			num += Driver.driver.condos.get(i).apartments.size();
```


```
			// calculate charges
```


```
			Driver.driver.condos.get(i).apartmentPropertyCharges();
```


```
		}
```


```
		this.setLayout(new GridLayout(num + 1, 2));
```


```
		// print charges into Layout
```


```
		for (int i = 0; i < Driver.driver.condos.size(); i++) {
```


```
			Condominium c = Driver.driver.condos.get(i);
```


```
			for (int j = 0; j < c.apartments.size(); j++) {
```


```
				this.add(new JLabel(c.apartments.get(i).getApartmentID()));
```


```
				this.add(new JLabel(Double.toString(c.apartments.get(i).getPropertyCharges())));
```


```
			}
```


```
		}
```


```
		JButton button6 = new JButton("OK");
```


```
		button6.addActionListener(new ActionListener() {
```


```
			@Override
```


```
			public void actionPerformed(ActionEvent e) {
```


```
				Input.this.setVisible(false);
```


```
				Input.this.dispose();
```


```
			}
```


```
		});
```


```
		this.add(button6);
```


```
		this.setVisible(true);
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
}
```

    You can see that I don't put more Labels that indicate what Kind of Input needs to be Inserted for Admin, Owner and so on, cause it would get even more complicated. You can try it out using numbers if you want tho :) I also don't check if some Choice is already made so that it is not allowed to run another one too. So, the GUI can look like [this](http://imgur.com/a/TH2yD)


  



    This was the End of Today's Post. The GUI Code is too large and that's why we get too many Scrollbars. That's why I will stop with Java (for now), cause Coding in other languages is more compact. I will upload 2 Exercises in C for Queues and Stacks and then we will start taking a look into Assembly :D  

Hope you enjoyed this Solution/Post :)


* * *

## Java Language

<br>

{% include programming/java_topics.html %}
  
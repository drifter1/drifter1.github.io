---
layout: default
title: All-in-One Exercise Solution
description: Java All-in-One Exercise Solution
thumbnail: /images/tutorials/programming/java.png
categories: [programming, java]
tags: [programming, java, basics]
permalink: /tutorials/:categories/:title
---

# Java All-in-One Exercise Solution

* * *

![](https://vignette2.wikia.nocookie.net/logopedia/images/6/6a/Java-logo.jpg/revision/latest/scale-to-width-down/640?cb=20150321072347)


# [Exercise Post](https://steemit.com/programming/@drifter1/programming-java-all-in-one-exercise)


    After more than one week I now present to you the **Solution** of the Exercise that I uploaded for you. This is an edited Task and it was much more difficult the way our professor told us to do it. I will upload this Exercise again when we have talked about GUI's and stuff, and that will be the real Task I had to do (almost). So, without further do, here the Solution of the Exercise.


  



# Solution:


   When I tried to solve the problem I first began creating the Classes and created the variables (data) and basic functions (getters-setters, constructors, toString) that are needed. Afterwards, I began creating the menu in the Driver class and defined function there (as static ones) or in the Condominium, Apartment Class and called them in the menu using the objects of type Condominium and the Apartment ArrayList of the Condominum. One little trick I used is that I set the ArrayList of Apartment to public static, so that it can be accessed anywhere. Finally, before showing the Code I wanted to tell that I use different Kinds of Constructors and not everything in the toString() method of the class get's printed so that it is easier for the textfile functions (you could use a separate function that prints in another way like printtoFile() or something). 


So, here comes the **Code**:


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
    private Owner owner;
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
    public Apartment(int condominiumID, String apartmentID, Owner owner, int squareMeters, 
```


```
    int millRate, double propertyCharges) {
```


```
	this.condominiumID = condominiumID;
```


```
	this.apartmentID = apartmentID;
```


```
	this.owner = owner;
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
    public Owner getOwner() {
```


```
	return owner;
```


```
    }
```


```
    public void setOwner(Owner owner) {
```


```
	this.owner = owner;
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
	    int N = Condominium.apartments.size();
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
                weight[i] = Condominium.apartments.get(i).getSquareMeters();
```


```
		// we use an object that does the same as strtok() in C
```


```
		// and splits the String where a specific character appears
```


```
		StringTokenizer strTok = new StringTokenizer(Condominium.apartments.get(i).getApartmentID(), "_");
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
		Condominium.apartments.get(i).setMillRate((int) ((weight[i] / sumWeight)));
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
	return condominiumID + "\n" + apartmentID + "\n" + owner.toString() + "\n" 
```


```
        + squareMeters + " " + millRate + " " + propertyCharges;
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
public class Condominium implements Serializable { // Condominium.java
```


```
    private int id;
```


```
    private Address a;
```


```
    private Administrator admin;
```


```
    // we make it public static so that is visible everywhere
```


```
    public static ArrayList<Apartment> apartments = new ArrayList<>();
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
    public Administrator getAdmin() {
```


```
	return admin;
```


```
    }
```


```
    public void setAdmin(Administrator admin) {
```


```
	this.admin = admin;
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
    public void findApartment(String apartmentcode) {
```


```
	boolean found = false;
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
			System.out.println("Apartment:\n" + apartments.get(i));
```


```
			found = true;
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
	if (found != true) {
```


```
		System.out.println("No apartment found with id " + apartmentcode);
```


```
	}
```


```
    }
```


```
    public void printApartments() {
```


```
	System.out.println("Apartments:");
```


```
	for (int i = 0; i < apartments.size(); i++) {
```


```
		System.out.println(apartments.get(i));
```


```
	}
```


```
    }
```


```
    public void printApartmentCharges() {
```


```
	System.out.println("Apartment Charges:");
```


```
	for (int i = 0; i < apartments.size(); i++) {
```


```
		System.out.println(apartments.get(i).getApartmentID() + ": " +
```


```
                 apartments.get(i).getPropertyCharges());
```


```
	}
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
		System.out.println("No Condominium has the id " + condominiumCode);
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
	return id + "\n" + a.toString() + "\n" + admin.toString() + 
```


```
        "\n" + expenditure ;
```


```
    }
```


```
}
```

  



Driver:



```
import java.io.*;
```


```
import java.util.ArrayList;
```


```
import java.util.Scanner;
```


```
public class Driver { // Driver.java
```


```
    public static void main(String[] args) {
```


```
	Scanner scan = new Scanner(System.in);
```


```
	int choice;
```


```
	ArrayList<Owner> owners = new ArrayList<>();
```


```
	Administrator admin = null;
```


```
	Condominium condo = null;
```


```
	while (true) {
```


```
		// print menu
```


```
		System.out.println("1. Insert Administator/Condominium");
```


```
		System.out.println("2. Insert Owner/Apartment");
```


```
		System.out.println("3. Print All Apartments");
```


```
		System.out.println("4. Find Apartment using Code");
```


```
		System.out.println("5. Find Property charges of specific Owner");
```


```
		System.out.println("6. Calculate Expenditure of Condominium");
```


```
		System.out.println("7. Calculate/Print Property charges of all Apartments");
```


```
		System.out.println("8. Save to Text File");
```


```
		System.out.println("9. Load from Text File");
```


```
		System.out.println("10. Save to Serializable File");
```


```
		System.out.println("11. Load from Serializable File");
```


```
		System.out.println("0. Exit");
```


```
		System.out.print("Choice: ");
```


```
		choice = scan.nextInt();
```


```
		switch (choice) {
```


```
		case 0:
```


```
			scan.close(); // close scanner
```


```
			System.exit(0); // exit programm
```


```
		case 1:
```


```
			admin = insertAdmin();
```


```
			condo = insertCondo();
```


```
			// set the compositionPartners
```


```
			admin.setCondo(condo);
```


```
			condo.setAdmin(admin);
```


```
			break;
```


```
		case 2:
```


```
			if (condo == null || admin == null) {
```


```
				System.out.println("run 1. first");
```


```
				break;
```


```
			}
```


```
			Owner owner;
```


```
			Apartment apartment;
```


```
			owner = insertOwner();
```


```
			apartment = insertApartment();
```


```
			// set the compositionPartners
```


```
			owner.setApartment(apartment);
```


```
			apartment.setOwner(owner);
```


```
			// insert in lists
```


```
			owners.add(owner);
```


```
			condo.apartments.add(apartment);
```


```
			break;
```


```
		case 3:
```


```
			condo.printApartments();
```


```
			break;
```


```
		case 4:
```


```
			System.out.print("ApartmentID: ");
```


```
			String apartmentcode = scan.next();
```


```
			condo.findApartment(apartmentcode);
```


```
			break;
```


```
		case 5:
```


```
			System.out.print("Owner ID: ");
```


```
			int id = scan.nextInt();
```


```
			findPropertyCharges(id);
```


```
			break;
```


```
		case 6:
```


```
			System.out.println("Expenditure: ");
```


```
			double expenditure = scan.nextDouble();
```


```
			condo.setCondominiumPropertyCharges(condo.getId(), expenditure);
```


```
			break;
```


```
		case 7:
```


```
			// calculate charges
```


```
			condo.apartmentPropertyCharges();
```


```
			// print charges
```


```
			condo.printApartmentCharges();
```


```
			break;
```


```
		case 8:
```


```
			try {
```


```
				PrintWriter writer = new PrintWriter(new FileOutputStream("condominium.txt"));
```


```
				// condo data that contains admin data
```


```
				writer.println(condo.toString());
```


```
				// apartment data that contains owner data
```


```
				writer.println(Condominium.apartments.size());
```


```
				for (int i = 0; i < Condominium.apartments.size(); i++)
```


```
                                    writer.println(Condominium.apartments.get(i).toString());
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
				System.out.println(ioe.getMessage());
```


```
			}
```


```
			break;
```


```
		case 9:
```


```
			try {
```


```
				Scanner reader = new Scanner(new FileInputStream("condominium.txt"));
```


```
				// Condo Data
```


```
				int tempCondoID = Integer.parseInt(reader.nextLine());
```


```
				// Condo Address
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
				condo = new Condominium(tempCondoID, tempA);
```


```
				// Admin Data
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
				// Admin Address
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
				admin = new Administrator(tempAdminID, tempName, tempSurname, tempA2);
```


```
				condo.setCondominiumPropertyCharges(tempCondoID, Double.parseDouble(reader.nextLine()));
```


```
				// set the compositionPartners
```


```
				admin.setCondo(condo);
```


```
				condo.setAdmin(admin);
```


```
				// Apartment Data
```


```
				int apartmentsCount = Integer.parseInt(reader.nextLine());
```


```
				for (int i = 0; i < apartmentsCount; i++) {
```


```
					Apartment tempApartment;
```


```
					Owner tempOwner;
```


```
					tempCondoID = Integer.parseInt(reader.nextLine());
```


```
					String tempApartmentID = reader.nextLine();
```


```
					// Owner Data
```


```
					int tempOwnerID = Integer.parseInt(reader.nextLine());
```


```
					tempName = reader.nextLine();
```


```
					tempSurname = reader.nextLine();
```


```
					// Owner Address
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
					tempOwner = new Owner(tempOwnerID, tempName, tempSurname, tempA3);
```


```
					owners.add(tempOwner);
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
					// add Apartment to list
```


```
                                        tempApartment = new Apartment(tempCondoID, tempApartmentID, tempOwner, tempSquareMeters, tempMillRate, tempPropertyCharges);
```


```
                                        condo.apartments.add(tempApartment);
```


```
                                }
```


```
				// set the compositionPartners
```


```
                                for (int i = 0; i < owners.size(); i++){
```


```
                                    for (int j = 0; j < condo.apartments.size(); j++) {
```


```
                                        // if owner id is equal to apartments owner
```


```
                                        if (owners.get(i).getId() == condo.apartments.get(j).getOwner().getId()) {
```


```
                                          owners.get(i).setApartment(condo.apartments.get(j));
```


```
                                            condo.apartments.get(j).setOwner(owners.get(i));
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
				reader.close();
```


```
			} catch (IOException ioe) {
```


```
				System.out.println(ioe.getMessage());
```


```
			}
```


```
			break;
```


```
		case 10:
```


```
			try {
```


```
				ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("condominium.dat"));
```


```
				// condo data that contains admin data
```


```
				oos.writeObject(condo);
```


```
				// apartment data that contains owner data
```


```
				oos.writeInt(Condominium.apartments.size());
```


```
				for (int i = 0; i < Condominium.apartments.size(); i++) {
```


```
					oos.writeObject(Condominium.apartments.get(i));
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
				System.out.println(ioe.getMessage());
```


```
			}
```


```
			break;
```


```
		case 11:
```


```
			try {
```


```
				ObjectInputStream ois = new ObjectInputStream(new FileInputStream("condominium.dat"));
```


```
				// Condo Data
```


```
				condo = (Condominium) ois.readObject();
```


```
				// Fill Admin with Condo's Admin
```


```
				admin = condo.getAdmin();
```


```
				// set the compositionPartners
```


```
				admin.setCondo(condo);
```


```
				condo.setAdmin(admin);
```


```
				// Apartment Data
```


```
				int apartmentsCount = ois.readInt();
```


```
				for (int i = 0; i < apartmentsCount; i++) {
```


```
					Apartment tempApartment = (Apartment) ois.readObject();
```


```
					// add to ArrayList of Condominium
```


```
					Condominium.apartments.add(tempApartment);
```


```
					// Fill Owner ArrayList with Owners of apartment
```


```
					owners.add(Condominium.apartments.get(i).getOwner());
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
				System.out.println(ioe.getMessage());
```


```
			}
```


```
			break;
```


```
		default:
```


```
			System.out.println("Wrong Choice!");
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
    // METHODS
```


```
    public static Administrator insertAdmin() {
```


```
        Scanner scan = new Scanner(System.in);
```


```
	// get information for admin
```


```
	System.out.print("Admin id: ");
```


```
	int id = scan.nextInt();
```


```
	System.out.print("Admin name: ");
```


```
	String name = scan.next();
```


```
	System.out.print("Admin surname: ");
```


```
	String surname = scan.next();
```


```
	// get information for address
```


```
	System.out.println("City: ");
```


```
	String city = scan.next();
```


```
	System.out.println("Street: ");
```


```
	String street = scan.next();
```


```
	System.out.println("Number: ");
```


```
	int number = scan.nextInt();
```


```
	System.out.println("ZIP: ");
```


```
	int zip = scan.nextInt();
```


```
	Address a = new Address(city, street, number, zip);
```


```
	return new Administrator(id, name, surname, a);
```


```
    }
```


```
    public static Condominium insertCondo() {
```


```
	Scanner scan = new Scanner(System.in);
```


```
	// get information for condo
```


```
	System.out.print("Condo id: ");
```


```
	int id = scan.nextInt();
```


```
	// get information for address
```


```
	System.out.println("City: ");
```


```
	String city = scan.next();
```


```
	System.out.println("Street: ");
```


```
	String street = scan.next();
```


```
	System.out.println("Number: ");
```


```
	int number = scan.nextInt();
```


```
	System.out.println("ZIP: ");
```


```
	int zip = scan.nextInt();
```


```
	Address a = new Address(city, street, number, zip);
```


```
	return new Condominium(id, a);
```


```
    }
```


```
    public static Owner insertOwner() {
```


```
	Scanner scan = new Scanner(System.in);
```


```
	// get information for owner
```


```
	System.out.print("Owner id: ");
```


```
	int id = scan.nextInt();
```


```
	System.out.print("Owner name: ");
```


```
	String name = scan.next();
```


```
	System.out.print("Owner surname: ");
```


```
	String surname = scan.next();
```


```
	// get information for address
```


```
	System.out.println("City: ");
```


```
	String city = scan.next();
```


```
	System.out.println("Street: ");
```


```
	String street = scan.next();
```


```
	System.out.println("Number: ");
```


```
	int number = scan.nextInt();
```


```
	System.out.println("ZIP: ");
```


```
	int zip = scan.nextInt();
```


```
	Address a = new Address(city, street, number, zip);
```


```
	return new Owner(id, name, surname, a);
```


```
    }
```


```
    public static Apartment insertApartment() {
```


```
	Scanner scan = new Scanner(System.in);
```


```
	// get information for apartment
```


```
	System.out.print("Condo id: ");
```


```
	int condo_id = scan.nextInt();
```


```
	System.out.print("Apartment id: ");
```


```
	String apartment_id = scan.next();
```


```
	System.out.print("Square Meters: ");
```


```
	int squareMeters = scan.nextInt();
```


```
	return new Apartment(condo_id, apartment_id, squareMeters);
```


```
    }
```


```
    public static void findPropertyCharges(int id) {
```


```
	for (int i = 0; i < Condominium.apartments.size(); i++) {
```


```
		// check equality of ids
```


```
		if (Condominium.apartments.get(i).getOwner().getId() == id) {
```


```
			System.out.println(
```


```
						"Owner with id " + id + " has to pay " + Condominium.apartments.get(i).getPropertyCharges());
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
}
```

  



  



    You don't have to do everything exactly the way I did it and there could be also some Bugs and things I didn't see and so on... But, I think it is a pretty good Exercise that shows you how to set-up and use most of the Java Stuff I showed you until now. I will post you the same Exercise extended with GUI and other Stuff, before I leave for Vacation and when I return I will post the Solution exactly the same way as I did this time.


That was the end of today's post. Hope you enjoyed it! :)


* * *

## Java Language

<br>

{% include programming/java_topics.html %}
  

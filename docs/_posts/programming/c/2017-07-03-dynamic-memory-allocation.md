---
layout: default
title: Dynamic Memory Allocation
description: C Dynamic Memory Allocation
thumbnail: /images/tutorials/programming/c.png
categories: [programming, c]
tags: [programming, c, basics]
permalink: /tutorials/:categories/:title
---

# C Dynamic Memory Allocation

* * *

In this post we will discuss how we can use dynamic Arrays in C. We will use the **stdlib.h** functions for memory management called **malloc()** and **realloc()**. This 2 functions return a pointer to a memory location of a requested size. You have to set up a pointer and save the return value to this pointer. 

![](http://www.zentut.com/wp-content/uploads/2009/12/c-dynamic-memory-allocation.jpg)

**For example:** Suppose we want an dynamic integer array. We will create a pointer to an integer as follow **int *A;**  

Then using malloc() we can setup the first size of the array with <code>**A = (int*)malloc(N*sizeof(int));</code> where you have to put an typecasting to int* because it returns void* by default and put the size you want as N * sizeof(int), with N being the number of items you want it to have. You can change it afterwards using **A = (int*)realloc(A,  M*sizeof(int));** making it smaller or bigger setting a new M size value. This is how you can allocate memory at runtime and by the needs of your programm.

# **Code:**

We want to get informations infinitely until we stop it (ID will equal 00000) about taxpayer's for their tax payment.

Informations:

*   ID (it has to be of length 5 and has only numbers), 
*   name (string), 
*   surname (string), 
*   birthday as string (we will "extract" the age and he will need to be atleast 18), 
*   category (self_employed, wage_earner),
*   income as float
*   taxes to pay as float.

Taxes go as follows:

    self_employed always 30% of it's income

    wage_earner with Staggered charge:

*   0% until 10.000
*   20% for 10.000 to 30.000
*   30% for 30.000 and upwards

When the infinite loop stops we print all the informations as a table. Because the number of taxpayers is not known we will have to use dynamic arrays for all of them. 

```c++
    #include <stdio.h>

    #include <stdlib.h>

    #include <string.h>

    #define Y 2017

    int main(){

        int *ids; //dynamic array of ids

        char **names; //dynamic array of names

        char **surnames; //dynamice array of surnames

        int *ages; //dynamic array of ages

        char *category; //dynamic array of categories of the taxpayers

        float *incomes; //dynamic array of incomes

        float *taxes; //dynamic array of taxes

        char id[6]; //reading as string to have it be of length 5

        char name[30], surname[30]; //temporary name, surname variables

        char date[11]; //for reading birthday date in format DD/MM/YYYY

        char *p; //pointer for spliting the birthday

        int day, month, year; //birthday seperated and in integer form

        float income, tax; //for reading income and calculating tax temporary 

        char cat; //temporary category

        int i; //loop variable

        int flag; //flag for checking

        int count = 0; //count of taxpayer's we inserted

        printf("TAX PROGRAMM:\n");

    	while(1){

    		//insert id (5 integers)

    		while(1){

    			flag = 1; //if it gets 0 it will reask the id

       	 		printf("id: ");

        		scanf("%5s", id);

    			fflush(stdin);

    			if( strlen(id) < 5) flag = 0; //check length

    			else{

    				for(i = 0; i < 5; i++){	//check it has only numbers

       	    			if( (id[i]<'0') || (id[i]>'9') ){

       	    				flag = 0;

       	    				break;

    					}

    		    	}

    			}			

    			if(flag == 1) break;

        	}

        	if(atoi(id) == 0){ //stop looping when its 00000

        		break; 

    		}

        	if(count == 0){ //first one

        		ids = (int*)malloc(1*sizeof(int));

    		}

    		else{ //every other one

    			ids = (int*)realloc(ids, (count+1)*sizeof(int));

    		}

    		ids[count] = atoi(id);

    		//name and surname input		

       		printf("name: ");

       		scanf("%29s", name);

       		fflush(stdin);

       		printf("surname: ");

       		scanf("%29s", surname);

       		fflush(stdin);

      		if(count == 0){ //first one

        		names = (char**)malloc(1*sizeof(char*));

        		surnames = (char**)malloc(1*sizeof(char*));

    		}

    		else{ //every other one

    			names = (char**)realloc(names, (count+1)*sizeof(char*));

    			surnames = (char**)realloc(surnames, (count+1)*sizeof(char*));

    		}

      		names[count] = (char*)malloc((strlen(name) + 1) * sizeof(char)); //allocate memory for name

      		strcpy(names[count], name);

      		surnames[count] = (char*)malloc((strlen(surname) + 1) * sizeof(char)); //allocate memory for surname

      		strcpy(surnames[count], surname);

      		//birthday input

    		while(1){

       			flag = 1;	//if it gets 0 it will reask the date

    			printf("DD/MM/YYYY: ");

    			scanf("%10s",date);

    			fflush(stdin);

    			day = atoi(date);

    			p=strchr(date,'/');

    			p=p+1;

    			month=atoi(p);

    			p=strchr(p,'/');

    			p=p+1;

    			year=atoi(p);			

    			if( (day<=0) || (day>31 ) ) flag = 0; //check reality of day

    			if( (month<=0) || (month>12) ) flag = 0; //check reality of month

    			if (year > Y - 18) flag = 0; //check year for age (easy way)

    			if(flag == 1) break;

      		}

      		if(count == 0){ //first one

        		ages = (int*)malloc(1*sizeof(int));

    		}

    		else{ //every other one

    			ages = (int*)realloc(ages, (count+1)*sizeof(int));

    		}

      		ages[count] = Y - year; //save the age into the array

      		//income input

      		while (1){ //need to be positive

           		printf("yearly income: ");

           		scanf("%f" ,&income);

           		fflush(stdin);

          		if(income > 0) break;

       		}

       		if(count == 0){ //first one

        		incomes = (float*)malloc(1*sizeof(float));

    		}

    		else{ //every other one

    			incomes = (float*)realloc(incomes, (count+1)*sizeof(float));

    		}

    		incomes[count] = income;

    		//category

    		while(1){

    			printf("Are you self employer(s) or wage earner(w): ");

    			scanf("%c", &cat);

    			fflush(stdin);

    			if(cat == 's' || cat == 'w') break;

    		}

    		if(count == 0){ //first one

        		category = (char*)malloc(1*sizeof(char));

    		}

    		else{ //every other one

    			category = (char*)realloc(category, (count+1)*sizeof(char));

    		}

    		category[count] = cat;

    		//calculate tax

    		if(cat == 's'){ //self employed

    			tax = income * 0.3;

    		}

    		else{

    			if(income <= 10000){

    				tax = 0;

    			}

    			else if(income > 10000 && income <= 30000){

    				tax = 0 + (income - 10000) * 0.2;

    			}

    			else{ //if > 30000

    				tax = 0 + 20000*0.2 + (income - 30000) * 0.3;

    			}

    		}

    		printf("You have to pay %.2f tax!\n", tax);

    		if(count == 0){ //first one

        		taxes = (float*)malloc(1*sizeof(float));

    		}

    		else{ //every other one

    			taxes = (float*)realloc(taxes, (count+1)*sizeof(float));

    		}

    		taxes[count] = tax;

    		count++; //increment count  		

    	}

    	//print informations

    	printf("TAXPAYERS:\n");

    	printf("ID\tNAME\tSURNAME\t\tAGE\tCATEGORY\tINCOME\t\tTAXES\n");

    	for(i = 0; i < count; i++){

    		printf("%d\t%s\t%s\t%d\t", ids[i], names[i], surnames[i], ages[i]);

    		if(category[i] == 's') printf("Self employed\t");

    		else printf("Wage earner\t");

    		printf("%.2f\t%.2f\n", incomes[i], taxes[i]);				

    	}

    	//its difficult to keep them all in one line when names are too big

           //so you should split the information array into two or three parts

    }
```

This task actually had statistics like some previous posts of myself, but because this one is only showing of dynamic arrays I took them off.  

Next time we will do something similar to store information, but with a dynamic struct and save and load from file.
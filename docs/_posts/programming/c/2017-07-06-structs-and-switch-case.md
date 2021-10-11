---
layout: default
title: Structs and Switch Case
description: C Structs and Switch Case
thumbnail: /images/tutorials/programming/c.png
categories: [programming, c]
tags: [programming, c, basics]
permalink: /tutorials/:categories/:title
---

# C Structs and Switch Case
* * *
# ![](http://www.tenouk.com/clabworksheet/labworksheet14_files/cstructprogramming020.png)

# Switch Case Statement:

    Continuing on we will take a look at the switch-case statement and how you can make an interface with it so that you can do stuff infinitely. The switch-case statement is one of the basic ones and is present in most languages without any need of libraries. It's actually a better way of creating an if-else statement for specific input values and when every value is corresponding to a specific "function" in the programm. 

**For example**, when you want to set up a way of doing something when x is 0 and something else when x is 1 you can do it with ease with an if-else if statement like this:

    if(x == 0){

        //do something

    }

    else if( x == 1){

        //do something else

    }

You can do it even when you have many of those statements but an easier way is creating an switch case statement that works with most types of variables like integers, floats and even strings! When a is an integer you do it like this:

    switch(a){

        case 1:

            //do something

           break;

       case 2:

           //do something else

           break;

      ...

      default:

          //default function

    }

We put break cause else it will "fall down" and run other cases to. Sometimes it may be helpfull tho when you want to run many cases at once.  The default one is like the else statement of the if-else statement and stands for every other value a could have. So you could put something that tells the user that the value was not right and so on.

# Structs:

Structs are a way of defining user variable types where you can put anything you like, like integer's, float's, char's, Array's, Pointer's and even other Structs. They are a way of setting up a variable that will act as a location of saving many things at once and so you can create an Array of not only Integer's or String's but and MultiArray that stores many informations. They are declared like this in C:

    struct struct_name {   type member1;   type member2;   ...

    }struct_name is the name of the struct and you can put as many member's as you wish doing stuff like:

    int a; 

    char b[20]; 

    float *p; 

and so on.

Setting it up like that you have to use **struct struct_name s; ** to create a struct variable s of type struct_name.

To get rid of the struct every time you can use **typedef**.

    typedef struct struct_name {   type member1;   type member2;

       ...} struct_alias;

The struct_alias is the way you want to call it when creating a variable. So using typedef we can now create a struct variable s of type struct_name using **struct_alias s; ** The struct_name is optional when you are using typedef so you could also use only struct_alias. 

Finishing of let me tell you that you can use **struct pointers** (that will be really helpfull when we get into lists), create a **struct array** that will be todays Code and that you have to use the **'.' modifier** to access each specific member and to do stuff with it afterwards like this:

    #include<stdio.h>

    #include<string.h>

    typedef struct{

        int id;

        char name[20];

    }Student;

    int main(){

        Student s;

       //setting the variable

        s.id = 10;

       //getting it as input

       scanf("%19s", s.name);

       //printing the variables

       printf("%d %s\n", s.id, s.name);   

    }

# Code:

We want to create an interface in command line (menu with switch case) that lets you work with informations about Musical Groups and their Album's. We'll have to save the Group's ID, Name, Foundation Year and 2 of the Album's from which we want to know the Name, Release Date and Sales Count. The Group and Album need to be Structs and we want to save infinitely informations (dynamic struct array).

The Interface needs to have the following:

* let us load from and save to a file

* let us add Groups

* let us search for a specific Group based on the ID or Name

* let us display all Groups

* let us find the Albums of a given Group after a given Year

* let us find the best-selling Album of a given Group

* let us sort the Group's Alphabetically

All of those Options will be accessed with a switch case statement inside of an infinite while loop.

All of the Options need to be called via Function.

The groups.txt should look like this:

2 //this is the group_count

100 Scorpions 1965 //group 1 information

Blackout 1982 1100000 //album 1 information of group 1

Sting_in_the_tale 2010 18500 //album 2 information of group 1

101 Dive_Straits 1977   //group 2 information

Making_Movies 1980 1000000 //album 1 information of group 2

Brother_in_arms 1985 9000000 //album 2 information of group 2

```c++

    #include <stdio.h> //input output

    #include <stdlib.h> //malloc, realloc

    #include <string.h> //strcmp 

    //Defining Structs Album and Group

    typedef struct{

    	char album_name[21];

    	int release_year;

    	long int sales;

    }Album;

    typedef struct{

    	int group_id;

    	char group_name[21];

    	int year;

    	Album album[2]; //2 albums to make it easier

    }Group;

    //Function Declaration

    Group* load_groups_from_file(Group *group, int *group_count);

    void save_groups_to_file(Group *group, int group_count);

    Group* add_group_to_struct(Group *group, int *group_count);

    void search_group_id(Group *group,int temp, int group_count);

    void search_group_name(Group *group, char buf[], int group_count);

    void print_groups(Group *group, int group_count);

    void find_album_after_year(Group *group, int temp, int search);

    void find_best_selling_album(Group *group, int search);

    Group* sort_groups(Group *group, int group_count);

    int input_group_pos(Group *group, int group_count);

    int main(){

    	int group_count = 0;//group count

    	int a;				//switch case variable

    	Group *group;		//dynamic array of struct group

    	char buf[50];		//for string input

    	long int temp;		//for integer input

    	int search;			//for searching at case 7 and 8

    	while(1){	//infinite loop

    		system("cls"); //clear the console

    		//print menu

    		printf("1\. Load groups from file\n");

    		printf("2\. Save groups to file\n");

    		printf("3\. Add a group\n");

    		printf("4\. Search/Display a group by group id\n");

    		printf("5\. Search/Display a group by group name\n");

    		printf("6\. Display all groups\n");

    		printf("7\. Find the albums of a given group after a given year\n");

    		printf("8\. Find the best-selling album of a given group\n");

    		printf("9\. Sort group array by group name\n");

    		printf("0\. Exit\n");

    		printf("Choice: ");

    		scanf("%d", &a);		

    		switch (a){

    			case 0:

    				exit(0); //terminate programm

    			case 1:	//open file "groups.txt" and copy the groups into the array

    				group = load_groups_from_file(group, &group_count); //because group_count is not a pointer we pass it's address

    				break;	

    			case 2:	//one file "groups.txt" and save the groups into the file

    				save_groups_to_file(group, group_count);

    				break;							

    			case 3:	//add new group into the group array

    				group = add_group_to_struct(group, &group_count);

    				break;						

    			case 4:	//search and display group with this specific id

    				printf("Give a ID: ");

    				scanf("%d",&temp);

    			    search_group_id(group, temp, group_count);

    				break;			

    			case 5:	//search and display group with specific name

    				printf("Give a Groupname: ");

    				scanf("%49s",buf);

    				search_group_name(group, buf, group_count);

    				break;

    			case 6:	//diplay all groups

    				print_groups(group, group_count);

    				break;	

    			case 7:	//display all album of an group after a specific date

    				search=input_group_pos(group, group_count);

    				if(search == -1){

    					printf("No Groups Added!\n");

    					break;

    				}

    				printf("Give a Year: ");

    				scanf("%d",&temp);

    				find_album_after_year(group, temp, search);

    				break;			

    			case 8:	//display album of specific group with best sales out of the 2

    				search=input_group_pos(group, group_count);

    				if(search == -1){

    					printf("No Groups Added!\n");

    					break;

    				}

    				find_best_selling_album(group, search);			

    				break;		

    			case 9:	//sort the groups alphabetically

    				group = sort_groups(group, group_count);

    				break;						

    			default:{

    				printf("You must select something from above!!!\n");

    				break;

    			}

    		}

    		sleep(2); //sleep for 2 seconds

    	}		

    }

    //FUNCTIONS

    Group* load_groups_from_file(Group *group, int *group_count){

    	int i;

    	FILE *fp; //file pointer to read from "groups.txt"

    	if((fp = fopen("groups.txt", "r")) == NULL){ //checking if file exists

    		perror ("groups.txt");

    		return group;

    	}

    	fscanf(fp, "%d", group_count); //read group_count as pointer doesn't need &

    	group = (Group*)malloc(*group_count * sizeof(Group)); //we need *group_count cause it's a pointer

    	for(i=0; i<*group_count; i++){

    		fscanf(fp, "%d %s %d", &group[i].group_id, group[i].group_name, &group[i].year);

    		fscanf(fp, "%s %d %ld", group[i].album[0].album_name, &group[i].album[0].release_year, &group[i].album[0].sales);

    		fscanf(fp, "%s %d %ld", group[i].album[1].album_name, &group[i].album[1].release_year, &group[i].album[1].sales);

    	}

    	return group;	

    }

    void save_groups_to_file(Group *group, int group_count){

    	int i;

    	FILE *fp; //file pointer to write into "groups.txt"

    	fp = fopen("groups.txt", "w"); //for saving you don't need to check existance cause it will create it

    	fprintf(fp, "%d\n", group_count);

    	for(i=0; i<group_count; i++){

    		fprintf(fp, "%d %s %d\n", group[i].group_id, group[i].group_name, group[i].year);

    		fprintf(fp, "%s %d %ld\n", group[i].album[0].album_name, group[i].album[0].release_year, group[i].album[0].sales);

    		fprintf(fp, "%s %d %ld\n", group[i].album[1].album_name, group[i].album[1].release_year, group[i].album[1].sales);

    	}			

    	fclose(fp);

    }

    Group* add_group_to_struct(Group *group, int *group_count){

    	long int temp;

    	char buf[50];

    	if(*group_count == 0){ //if it was not created it needs malloc

    		group = (Group*)malloc( (*group_count + 1) * sizeof(Group) );

    	}else{

    		group = (Group*)realloc(group, (*group_count + 1) * sizeof(Group));

    	}

    	printf("Group ID: ");

    	scanf("%d",&temp);

    	group[*group_count].group_id=temp;

    	do {

    	printf("Groupname: ");

    	scanf("%49s",buf);

    	} while(strlen(buf)>=20);

    	strcpy(group[*group_count].group_name, buf);

    	printf("Foundation Year: ");

    	scanf("%d",&temp);

    	group[*group_count].year=temp;

    	printf("Now give 2 Albums in this Order: Name Release_Date Sale_Count\n");

    	printf("Album 1: \n");

    	scanf("%19s %d %ld", group[*group_count].album[0].album_name, &group[*group_count].album[0].release_year, &group[*group_count].album[0].sales);

    	printf("Album 2: \n");

    	scanf("%19s %d %ld", group[*group_count].album[1].album_name, &group[*group_count].album[1].release_year, &group[*group_count].album[1].sales);

    	(*group_count)++; //increment group_count

    	return group;

    }

    void search_group_id(Group *group, int temp, int group_count){

    	int i;

    	if(group_count == 0){ //checking emptyness

    		printf("No Groups Added!\n");

    		return;

    	}

    	for(i=0; i<group_count; i++){

    		if(temp==group[i].group_id){

    			printf("%d %s %d\n", group[i].group_id, group[i].group_name, group[i].year);

    			printf("%s %d %ld\n", group[i].album[0].album_name, group[i].album[0].release_year, group[i].album[0].sales);

    			printf("%s %d %ld\n", group[i].album[1].album_name, group[i].album[1].release_year, group[i].album[1].sales);

    			printf("\n");			

    			break;	

    		}

    	}

    	if(i==group_count) printf("No Group has this ID!\n");

    }

    void search_group_name(Group *group, char buf[], int group_count){

    	int i;

    	if(group_count == 0){ //checking emptyness

    		printf("No Groups Added!\n");

    		return;

    	}

    	for(i=0; i<group_count; i++){

    		if( strcmp(buf, group[i].group_name)==0 ){

    			printf("%d %s %d\n", group[i].group_id, group[i].group_name, group[i].year);

    			printf("%s %d %ld\n", group[i].album[0].album_name, group[i].album[0].release_year, group[i].album[0].sales);

    			printf("%s %d %ld\n", group[i].album[1].album_name, group[i].album[1].release_year, group[i].album[1].sales);

    			printf("\n");

    			break;

    		}

    	}

    	if(i==group_count) printf("No Group has this Name!\n");

    }

    void print_groups(Group *group, int group_count){

    	int i;

    	if(group_count == 0){ //checking emptyness

    		printf("No Groups Added!\n");

    		return;

    	}

    	printf("Groups: \n");

    	for(i=0; i<group_count; i++){

    		printf("%d %s %d\n", group[i].group_id, group[i].group_name, group[i].year);

    		printf("%s %d %ld\n", group[i].album[0].album_name, group[i].album[0].release_year, group[i].album[0].sales);

    		printf("%s %d %ld\n", group[i].album[1].album_name, group[i].album[1].release_year, group[i].album[1].sales);

    		printf("\n");

    	}	

    }

    void find_album_after_year(Group *group, int temp, int search){

    	int i;

    	for(i=0; i<2; i++){

    		if(group[search].year>=temp){

    			printf("%s %d %ld\n", group[search].album[i].album_name, group[search].album[i].release_year, group[search].album[i].sales);

    		}

    	}

    }

    void find_best_selling_album(Group *group, int search){

    	if(group[search].album[0].sales>group[search].album[1].sales){

    		printf("%s %d %ld\n", group[search].album[0].album_name, group[search].album[0].release_year, group[search].album[0].sales);

    	}

    	else{

    		printf("%s %d %ld\n", group[search].album[1].album_name, group[search].album[1].release_year, group[search].album[1].sales);

    	}

    }

    Group* sort_groups(Group *group, int group_count){

    	int i,j;

    	Group swap;

    	if(group_count == 0){ //checking emptyness

    		printf("No Groups Added!\n");

    		return group;

    	}

    	for(i=0; i<group_count; i++){

    		for(j=0; j<group_count; j++){

    			if( strcmp(group[j].group_name, group[i].group_name)>0 ){

    				swap=group[i];

    				group[i]=group[j];

    				group[j]=swap;				

    			}

    		}

    	}

    	return group;

    }

    int input_group_pos(Group *group, int group_count){

    	int i;

    	int search;

    	char buf[50];

    	if(group_count == 0){ //checking emptyness

    		return -1;

    	}

    	do {	

    		printf("Give Groupname: ");

    		scanf("%49s",buf);

    		search=0;

    		for(i=0; i<group_count; i++){

    			if( strcmp(buf, group[i].group_name)==0 ){

    				search=i;

    				break;

    			}

    		}

    		if(search==0) printf("No Group has this Name!\n");

    	} while(search==0);

    	return search;

    }

```

You can see that I return a pointer everytime I change something in the dynamic struct array. You could also do it via reference (using **group instead of *group) and using *something and passing the address of the pointer(!) when calling the function. But, to make it simple let's stick with returning cause it's more C-Like and putting it by reference is easier in Object-oriented Programming like Java or C#, cause working with pointer's is difficult and knowning when to put &, * or nothing at a scanf or printf statement gets a little difficult.

* * *

## C Language

<br>

{% include programming/c_topics.html %}

---
layout: default
title: Hashtables with Chaining
description: C Hashtables with Chaining
thumbnail: /images/tutorials/programming/c.png
categories: [programming, c]
tags: [programming, c, datastructures]
permalink: /tutorials/:categories/:title
---

# C Hashtables with Chaining
* * *


![](https://s26.postimg.org/jr9cpmrt5/CSb6_Y.png)


    Hello again! We will now get again into Programming and talk about **Hashing** and **Hashtables**. I will split the talk in two posts, the first (this one) will contain the **Theory** behind Hashing and the **implementation** **using** **Chaining** **in** **C** and the second one will contain an implementation of Hashtables using Linear Probing! So, why wait any more? Let's get started!


  



# Hashing Theory:


    **Hashtables** are another **Datastructure** beside Arrays, Lists and Trees that we talked off earlier. It is used when we want to quickly find a data record given a search key. The records get stored to the specific index the **Hashfunction** gave for the specific value. We mostly **implement** them **using** **Static** **Arrays** (that become greating with **Rehashing** if needed) and use simple **modulo** **hashfunctions** (**XmodN**) so that the values get stored depending on their modulo with the length of the Array. That way we know exactly were the value was stored and can get it much faster instead of having to search a whole Array, List or Tree!


   The problem comes when there already is a value stored inside of the index that the value belongs to. Then we have a **Collision** that can be handled in many different ways! We will have to use another way of finding the index in which the value will be put in. Collision bring also a slight performance loss depending on how we solve our problem. 


## Clustering:


    When two many values belong to an specific index we form **clusters** of records. **Clustering** is not good, cause it decreases the search time! Think about an Hashtable of 10 Indexes and that we store 5 values that are for example 5, 15, 25, 35, 45. Let's say we solve the Collisions by putting the values one index after (Linear Probing, more into that later on) so that we put all in the Hashtable. When we now want to search for 45 we will now have to start off from 5 and then go to 15, 25, 35 and lastly to 45. What happens if we then want to put for example another value in that has a hashing index that is where we put the 5 Colliders in? Well, than it will be put at the end of this Cluster and the performance fells for another key. So, you can see directly that we lost the quick search and that the performance fell dramatically forming those Clusters.


    But, what to we do when Collisions happen? The answers is we use specific **Collision** **Handling** **Techniques** that are good in specific datasets. When for example many values fall into the same key, some techniques may have better result then others. As we saw before the Collision Handling using Linear Probing was not so effective. Let's now get into which Collision Handling Techniques are available and easy to setup!


## Collision Handling:


    In Code we will talk only about 2 of those Techniques, but here are those and some others that may come handy in your Hashtable datasets. 


We split those in 2 Categories that are:


1. **Open** **Addresing** (Linear Probing, Quadratic Probing, Double Hashing)
2. **Chaining**


Let's get more in depth in all of those:


* **Linear** **Probing**, maybe the most simple one. It solves the Collisions by inserting the value to the next free space after the hashindex the hashfunction gave us. It works great when the values end up on different indexes. When clusters are formed they will decrease the performance dramatically
* **Quadratic** **Probing**, that is similar to linear probing. It solves the Collisions by inserting the value not only in the next free space directly, but following the i^2 steps, starting i from 1. So, it will put the value in the next free space or 4 spaces later or 9 spaces later etc. When the next space is empty it will cause again cluster forming, but if it is occupied it will put the value some spaces later and so prevent cluster forming. This Method works great when only some of the values have similar hashkeys.
* **Double** **Hashing**, that is again similar to the others. When the first hashfunction fails we then use a new one, that mostly has a different modulo value. This value will represent the steps in which we will move on from the first hashindex until we find an empty space. So, it is similar to Quadratic Probing, but the step will be static and we will get this step from a second hashfunction.
* **Chaining**. Lastly this way is the most easiest of all. Each Index will be it's own List and so the values with the same hashindexes will be put on the same List. Again, we have a performance increase when many values fall into the same key, but we don't have bad clusters like in Linear Probing. That means that we don't have values from other key's in between, but search only in the specific key List. So, the perfromance will only be affected on those key's that have many values and the others will continue working just fine!


  



Lastly I want to give some Tipps that help us make our Hashing Function better.


## Hash Function Tipps:


* The **size** of our Hashtable and so the number with which we do our modulo calculation, should be a **prime** **number** that is only divisible with itself or 1. That way we prevent stacking of many values in one place like 2 when the numbers are even!
* The **Collision** **Handling** Method we choose **depends** **on** the **application**. So, choose it wisely depending on your **Dataset**. Also, remember that all those that I showed you are pretty easy to setup, but you could also come up with your own idea!
* When the Hashtable if half full the performance start to shrink, thats when we do **Rehashing**! Rehashing is when we enlargen our Hashtable's size (that should again be a prime number) and then call the new hash function on each of the previous values to put those values again i ther right spot of the new Hashtable!


  



So, after all that Theory let's now get into Chaining!


# Chaining Implementation:


    Chaining is pretty easy to implement. We have to create an Array whose indexes point to different Lists. We will use a simple modulo hashfunction with an prime number for that and the size of the Hashtable that can be set as an define parameter! I will use all the List stuff we already talked about. To insert we insert the value to the corresponding  List. To search we simply have to search the specific List for the value. I will put the whole Code and some Comments for you to understand it better!



```
#include <stdio.h>
```


```
#include <stdlib.h>
```


```
#include <string.h>
```


```
#define N 31 // prime number for size of array
```


```
#define h(x) (x % m) //h(x) = x mod m
```


```
  

```


```
// Node for List
```


```
typedef struct Node{
```


```
    int val;
```


```
    struct Node *next;
```


```
}Node;
```


```
  

```


```
//function's declaration
```


```
Node *fill_table(Node *table, int table_range, int number);
```


```
Node *insert(Node *table, int hash_index, int val);
```


```
Node *del(Node *table,int table_range,int val);
```


```
void print_table(Node *table, int table_range);
```


```
void search_table(Node *table, int table_range, int val);
```


```
  

```


```
int main(){
```


```
    Node *table; // hashtable
```


```
    int n, i, j, choice, search;
```


```
    int hash_num, val;	 	
```


```
  

```


```
    // allocate table
```


```
    table = (Node*) malloc(N*sizeof(Node));
```


```
    //make table "heads" NULL
```


```
    for(i = 0; i < N; i++){
```


```
    	table[i].next = NULL;
```


```
    }
```


```
	
```


```
    printf("--h(x) = xmod%d--\n",N);
```


```
    printf("\n\n");	 
```


```
  

```


```
    while(1){
```


```
    	printf("1.Insert random numbers\n");
```


```
    	printf("2.Delete a number\n");
```


```
	printf("3.Search a number\n");
```


```
	printf("4.Show Hash Table\n");
```


```
	printf("0.Exit Programm\n");		
```


```
	printf("\n--------\n");
```


```
	printf("Choice: ");
```


```
	scanf("%d",&choice);
```


```
	
```


```
	switch(choice){
```


```
		case 0: return;
```


```
		case 1:
```


```
			// insert random numbers
```


```
			printf("Lot to insert: ");
```


```
			scanf("%d", &n);
```


```
			table = fill_table(table, N, n);
```


```
			printf("Filled HashTable with %d random values\n", n);
```


```
			printf("\n--------\n");
```


```
			break;
```


```
		case 2:
```


```
			// delete a number
```


```
			printf("Give a number: ");
```


```
			scanf("%d",&search);
```


```
			table = del(table, N, search);
```


```
			printf("\n--------\n");	
```


```
			break;
```


```
		case 3:
```


```
			// search for a number
```


```
			printf("Give a number: ");
```


```
			scanf("%d",&search);			
```


```
			search_table(table, N, search);
```


```
			printf("\n--------\n");	
```


```
			break;
```


```
		case 4:
```


```
			//print hashtable
```


```
			printf("-HASHTABLE-\n\n");
```


```
			print_table(table, N);
```


```
			printf("\n--------\n");	
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
	return 0;
```


```
}
```


```
  

```


```
// FUNCTIONS
```


```
Node *fill_table(Node *table, int table_range, int number){
```


```
    int i;
```


```
    int num;
```


```
    for(i=0; i<number; i++){
```


```
	num = rand()%10000; // random number from 0 to 9999
```


```
	table = insert(table, num % table_range, num);
```


```
    }
```


```
    return table;
```


```
}
```


```
  

```


```
void print_table(Node *table, int table_range){
```


```
    int i;
```


```
    Node* cur;
```


```
    for(i = 0; i < table_range; i++){ // for each list
```


```
	if(table[i].next == NULL){ // if empty
```


```
                printf("Table[%d] is empty!\n", i);
```


```
		continue;
```


```
	}
```


```
	cur = table[i].next;
```


```
	printf("Table[%d]", i);
```


```
	while(cur!=NULL){ // else print all the values
```


```
		printf("->%d",cur->val);
```


```
		cur=cur->next; //cur=cur+1;
```


```
	}
```


```
	printf("\n");	
```


```
    }
```


```
}
```


```
  

```


```
Node *insert(Node *table, int hash_index, int val){
```


```
    Node *nn, *cur;
```


```
  

```


```
    nn = (Node*)malloc(sizeof(Node));
```


```
    nn->val=val;
```


```
    nn->next=NULL;
```


```
	
```


```
    if(table[hash_index].next == NULL){
```


```
	table[hash_index].next = nn;
```


```
	return table;
```


```
    }
```


```
	
```


```
    cur = table[hash_index].next;
```


```
    while(cur->next != NULL){
```


```
	cur=cur->next; //cur=cur+1;
```


```
    }
```


```
    cur->next = nn;
```


```
    return table;
```


```
}
```


```
  

```


```
void search_table(Node *table, int table_range, int val){
```


```
    int index = val % table_range;
```


```
    Node *cur;
```


```
	
```


```
    if(table[index].next == NULL){ // if empty
```


```
		printf("Value %d not found cause Table[%d] is emtpy!\n", val,index);
```


```
                return;
```


```
    }
```


```
  

```


```
    cur = table[index].next;
```


```
    while(cur!=NULL){
```


```
	if(cur->val == val){
```


```
		printf("Value %d was found!\n", val);
```


```
		return;
```


```
	}
```


```
	cur = cur->next;
```


```
    }
```


```
    printf("Value %d not found in Hashtable!\n", val);
```


```
}
```


```
  

```


```
Node *del(Node *table, int table_range, int val){
```


```
    int index = val % table_range;
```


```
    Node *prev;
```


```
	
```


```
    if(table[index].next == NULL){ // if empty
```


```
	printf("Value %d not found cause Table[%d] is emtpy!\n", val,index);
```


```
	return table;
```


```
    }
```


```
	
```


```
    if(table[index].next->val == val){ // if first item
```


```
	printf("Value %d was found at table[%d] and Deleted!\n", val,index);
```


```
	table[index].next = table[index].next->next;
```


```
	return table;
```


```
    }
```


```
  

```


```
    prev = table[index].next;
```


```
    while(prev->next!=NULL){
```


```
	if(prev->next->val == val){
```


```
		prev->next = prev->next->next;
```


```
		printf("Value %d was found at table[%d] and Deleted!\n", val,index);
```


```
		return table;
```


```
	}
```


```
	prev = prev->next;
```


```
    }
```


```
    printf("Value %d was not found in Hashtable!\n", val);
```


```
    return table;
```


```
}
```

  



An Example run looks like this:


![](https://s26.postimg.org/tm0hvuvrd/examplerun.png)


  



Hope you enjoyed it!


I will upload the Linear Probing Implementation also, later in the day!


See ya later!


* * *

## C Language

<br>

{% include programming/c_topics.html %}

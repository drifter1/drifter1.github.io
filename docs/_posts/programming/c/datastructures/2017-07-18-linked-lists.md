---
layout: default
title: Linked Lists
description: C Linked Lists
thumbnail: /images/tutorials/programming/c.png
categories: [programming, c]
tags: [programming, c, datastructures]
permalink: /tutorials/:categories/:title
---

# C Linked Lists
* * *

![](https://people.engr.ncsu.edu/efg/210/s99/Notes/LLdefs.gif)

   In today's post we will talk about **Linked Lists** in C Language. I will show you how to **create a List**, **insert** and **remove** an Item. Also, how to **search** for a **specific Item** in the List and we will also do some more advanced stuff that includes **printing** in **normal and reverse order** using recursive algorithms that are pretty simple if you get the hang of it. So, without further do, let's start out with the representation in Code of an List.

* * *
# List Representation:

    An **Lis**t is an **Data Structure** that can be of infinite length were an Item called **head** points to another item in the list, that points to another item and so on... Every item contains a **pointer to the next Item** and Data that can be everything. So, an List in C is an **struct** that is defined like that:

```c++
typedef struct Node{

    //DATA

    struct Node *next; //pointer to next Item

}Node; 

```

    Every Item is a **Node** of the List. We **store** the **Pointer to the first Item** in memory in our function so that we can afterwards use it in another variable called **current_pointer**, without losing it to get the information of all of our Nodes. So, the main function will use an Node of this kind initialized to NULL:

```c++
Node *head = NULL;
```

    Let's now talk about **functions** that will do stuff on our List like: insert, remove, search, sort, print.

* * *
# Insert:

    For inserting we will use an Item called **new_node** or **nn** that will **temporary store** our new Node and that we will **afterwards insert** to our List to the **front** or **rear**. This Item will be created using the memory allocation function **malloc(**) for dynamic memory allocation that we already know and because it is a **struct** we will then access each **member** of the struct using the **'->' modifier**. We use an **arrow** instead of the dot, because we are now going to member's of an struct pointer! So, our **new_node Code** will look like this:

```c++
Node* nn; 

nn = (Node*) malloc (sizeof(Node)); 

// for every Data Variable we do

nn->Data = value; 

// we set the next pointer to NULL

nn->next = NULL; 

```

    When inserting we always make sure if it is the first Item inserted, checking if our **List is NULL** that means it is **empty**. 

## Insert at Front:

    Inserting to the **front** is pretty simple cause we simply **set** our **next pointer to head** and afterwards set the **nn to** by our **new head** like this:

```c++
Node *insertFirst(Node *head, int val){

	Node *nn;

	// create our new node

	nn = (Node*)malloc(sizeof(Node));

	nn->val = val;

	nn->next = NULL;

	// check if list is empty

	if(head == NULL){

		// return pointer to nn

		return nn;

	}

	// set head to by our next pointer 

	nn->next = head;

	// return pointer to nn

	return nn;	

}
```

## Insert at Rear:

    To insert in the **rear** we have to go to our last Item using a **current_node** checking if the **next pointer is NULL** and setting the **next to** our **new_node** like this:

```c++
Node *insertLast(Node *head, int val){

	Node *nn, *cur;

	// create our new node

	nn = (Node*)malloc(sizeof(Node));

	nn->val = val;

	nn->next = NULL;

	// check if list is empty

	if(head == NULL){

		// return pointer to nn

		return nn;

	}

	// set cur to point to our list

	cur = head;

	//use a while loop to find the last Item

	while(cur->next != NULL){

		// set cur to next Item

		cur = cur->next; 

	}

	// next of last Item will be our new node

	cur->next = nn;

	// return head

	return head;	

}

```

    To **insert in a Specific location** in between you have to first search the Item after it should be inserted. You can find it out by yourself after I show you searching. 

* * *

# Delete:

    To delete an Item we have to **check if** the **List is Empty** cause else we will cause an Error.

## Delete at Front:

    To delete the item in **front** we simply **set the head** **to** it's **next pointer** like this:

```c++
Node* deleteFirst(Node *head){

	// check if list is empty

	if(head == NULL){

		// simply return it back after printing

		printf("Empty List!");

		return head;

	}

	// return the next pointer

	return head->next;

}
```

## Delete at Rear:

    To delete in **rear** we have to find the Item that **points to the last Item** and set the **next pointer to NULL** like this:

```c++
Node* deleteLast(Node *head){

	Node *cur;

	// check if list is empty

	if(head == NULL){

		// simply return it back after printing

		printf("Empty List!");

		return head;

	}

	// check if first Item is the only Item

	if(head->next == NULL){

		// make the list NULL

		return NULL;		

	}

	// set cur to point to our list

	cur = head;

	// use a while loop to find the Item that points to our last Item

	while(cur->next->next != NULL){

		// set cur to next Item

		cur = cur->next; 

	}

	// set the next pointer of it to NULL

	cur->next = NULL;

	// return head

	return head;

}

```

  To **delete a Specific Item** in between you have to first search the **Item that points to it** and afterwards **set** it's **next pointer** **to** be the **next pointer** **of** the **Item** that should be **deleted**. (that was a mouthful xD). I guess you can do it by yourself after I show you searching that comes next.

* * *

# Search:

    Searching is pretty simple you just **loop through all Nodes** and **check** the specific Data **value** and print if it was found or not, but I will r**eturn the Node** to make it more interesting. If it returns NULL we know that it was not found. So, the Code will look like this:

```c++
Node* searchList(Node *head, int val){

	Node *cur;

	// check if list is empty

	if(head == NULL){

		// simply return it back after printing

		printf("Empty List!");

		return head;

	}

	// set cur to point to our list

	cur = head;

	// use a while loop to find the Item

	while(cur != NULL){

		// check equality

		if(cur->val == val){

			// return the cur Node

			return cur;

		}		

		// set cur to next Item

		cur = cur->next; 

	}

	// if not found return NULL

	return NULL;	

} 
```

* * *
# Print:

    Printing is Last and I will show you how you implement it using recursive algorithms.

## Normal Printing:

    **Normal** Printing can be done simple using the concept that I showed you before like this:

```c++
void printList(Node *head){

	Node *cur;

	// check if list is empty

	if(head == NULL){

		printf("Empty List!");

	}

	// set cur to point to our list

	cur = head;

	//use a while loop to loop through each Item

	while(cur != NULL){

		//print with -> to make it look like a List

		printf("%d->",cur->val);

		// set cur to next Item

		cur = cur->next;

	}

	printf("NULL\n");	

}

```

    But, to make it more interesting let's show it with an **recursive function** too. The Code will **check emptyness** as an stop condition and afterwards **print the value** and **recall with next pointer** like this:

```c++
void printList(Node *head){

	// check if list is empty

	if (head == NULL){ 

		// stop condition

		printf("NULL\n");

    	return;

	}

	//print with -> to make it look like a List

	printf("%d->", head->val);

        // call again using next pointer

        printList(head->next);

}
```

    As you can see the Code is much smaller and when you know to use recursion you can create more advanced functions that do more complicated stuff that will be a pain using non-recursive functions.

## Reverse Printing:

    For reverse printing we use the **same Code** but we **switch places** of printing and recalling! So simple:

```c++
void reversePrintList(Node *head){

	// check if list is empty

	if (head == NULL){ 

		// stop condition

		printf("NULL");

                return;    

    }

    // call again using next pointer

    reversePrintList(head->next); 

    //print with <- to make it look like a List

    printf("<-%d", head->val); 

}

```

    Off course, you can do more stuff like **sorting**, but what I told you here is I think more than enough to start out using Lists in C. A simple programm that uses all off those functions is tha following:

* * *

# **Code:**

	int main(int argc, char *argv[]){
		// the head is initialized as NULL first

		Node *head = NULL;

		// insert 5 first and print list

		head = insertFirst(head, 5);

		printList(head);

		// insert 6 last and print list

		head = insertLast(head, 6);

		printList(head);

		// insert 3 last and print list

		head = insertLast(head, 3);

		printList(head);

		// search for 5	

		Node *search;

		search = searchList(head, 5);

		// if not found

		if(search == NULL){

			printf("Not Found!\n");

		}

		else{

			printf("%d was Found!\n", search->val);

		}

		// print in reverse order

		reversePrintList(head);	
	}

    I don't included the structs and stuff cause I told you how you set the up before. Also, this is the end of today's post. Hope you enjoyed it and next time prepare for Trees in C!

* * *

## C Language

<br>

{% include programming/c_topics.html %}

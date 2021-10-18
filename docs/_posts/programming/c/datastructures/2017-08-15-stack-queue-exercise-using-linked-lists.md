---
layout: default
title: Stack-Queue Exercise using Linked Lists
description: C Stack-Queue Exercise using Linked Lists
thumbnail: /images/tutorials/programming/c.png
categories: [programming, c]
tags: [programming, c, datastructures]
permalink: /tutorials/:categories/:title
---

# C Stack-Queue Exercise using Linked Lists
* * *


![](http://1.bp.blogspot.com/-Cb5cQnnbwvk/ViKhgiDXP2I/AAAAAAAAA8o/LcII9oEehsY/s1600/linkedlist.gif)


    Here the promised second part! Today, we will make a **similar Exercise** to the last one that you can find [here](https://steemit.com/programming/@drifter1/programming-c-stack-queue-exercise-using-dynamic-arrays), where we will create Stack and Queue Ferry Boats that carry Cars using **Linked Lists**! We will not do the exact same Exercise, but It's tweaked a little bit. I will explain everything the same way I explained it last time! So, without further do. Let's get started!


  



# Task:


    In the same way as last time we will have two different kinds of Ferry Boats and Cars that want to get on board of them. One Boat will work like a Stack and one like a Queue and both will use a Linked List Structure. But, this time the Cars don't choose in which Ferry Boat they want to go in (the text file remains the same tho!). The Cars will first go into Boat S, move into Boat Q and then finish their Sailing!


Our Boats will contain the following:


* the capacity (to check if the Boats are full)
* the sailing number (to write into files)
* the number of elements inserted
* a Top Node Pointer for the Stack and a Front and Rear Node Pointer for the Queue


The Node will contain a car\_id and a pointer to the next one inside of the Linked List.


 The Cars will be a part of a text file called cars.txt (we will get the name as input) and this file will contain the car\_id and the boat preference (that doesn't matter here) like this:


## cars.txt:


ZZA9896 S


MIN5689 Q


NHI9098 S


KNM4545 Q


IPO8987 Q 


  



The Programm will:


1. get the capacity of each boat and the file name as user input
2. initialize the boats
3. start reading from the file and then manage the sailings
4. the cars will first get into Boat S, be written into file when S is full, moved into Q where it fills up, until S is empty and gets written into a file aswell when it gets full (can be more times then S, when for example S has capacity of 2 and Q of 1)
5. the reading loop will stop when there are no more cars in the file
6. then we will check if there are some remainders in the Boats to write them in a "sailing" file aswell


 The Stack-Queue Functions need to be Functions that are called from the main function! 


  



# Solution:



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
  

```


```
// List Node
```


```
typedef struct Node{
```


```
	char car_id[10];
```


```
	struct Node *next;
```


```
}Node;
```


```
// Stack struct
```


```
typedef struct Stack{
```


```
	int sail_num;
```


```
	int capacity;
```


```
	int numElements;
```


```
	Node *Top;
```


```
}Stack;
```


```
// Queue struct
```


```
typedef struct Queue{
```


```
	int sail_num;
```


```
	int capacity;
```


```
	int numElements;
```


```
	Node *front;
```


```
	Node *rear;		
```


```
}Queue;
```


```
  

```


```
// Function Declarations
```


```
void push(Stack *S, char *x);
```


```
void StacktoFile(Stack S);
```


```
void add(Queue *Q, char *x);
```


```
void delete(Queue *Q, char *car_id);
```


```
void QueuetoFile(Queue *Q);
```


```
  

```


```
int main(){
```


```
	// Boat variables
```


```
	Stack S;
```


```
	Queue Q;
```


```
	// helping variables
```


```
	Node *cur;
```


```
	char input_file[20];
```


```
	int i;
```


```
	FILE *fp;
```


```
	// temporary file reading buffers
```


```
	char car_id[10];
```


```
	char ship;
```


```
	
```


```
	// read capacity values
```


```
	printf("Capacity of S: ");
```


```
	scanf("%d", &S.capacity);
```


```
	printf("Capacity of Q: ");
```


```
	scanf("%d", &Q.capacity);
```


```
	
```


```
	// read file name
```


```
	printf("Input File: ");
```


```
	scanf("%19s", input_file);
```


```
  

```


```
	// open file for reading
```


```
	if(!(fp=fopen(input_file, "r"))){ 
```


```
		perror("fopen");
```


```
		return 1;
```


```
	} 
```


```
	
```


```
	// initialize Stack
```


```
	S.Top=NULL;
```


```
	S.numElements=0;
```


```
	S.sail_num=0;
```


```
	
```


```
	// initialize Queue
```


```
	Q.front=Q.rear=NULL;
```


```
	Q.numElements=0;
```


```
	Q.sail_num=0;
```


```
	
```


```
	// loop for reading from file and writing into new ones
```


```
	while(fscanf(fp, "%9s %c", car_id, &ship)!=EOF){
```


```
		push(&S, car_id);
```


```
		// if full write to file
```


```
		if(S.numElements==S.capacity){
```


```
			StacktoFile(S);
```


```
			// insert to other Ferry Boat
```


```
			cur=S.Top;
```


```
			while(cur!=NULL){
```


```
				add(&Q, cur->car_id);
```


```
				// if full write to file
```


```
				if(Q.numElements==Q.capacity){
```


```
					QueuetoFile(&Q);
```


```
				}
```


```
				cur=cur->next;
```


```
			}
```


```
			// reset Stack
```


```
			S.sail_num++;
```


```
			S.Top=NULL;
```


```
			S.numElements=0;
```


```
		}		
```


```
	}
```


```
	// check if boats are left
```


```
	if(S.numElements!=0){
```


```
		StacktoFile(S);
```


```
		// insert to other Ferry Boat
```


```
		cur=S.Top;
```


```
		while(cur!=NULL){
```


```
			add(&Q,cur->car_id);
```


```
			// if full write to File
```


```
			if(Q.numElements!=0){
```


```
				QueuetoFile(&Q);
```


```
			}
```


```
			cur=cur->next;
```


```
		}
```


```
	}
```


```
	if(Q.numElements!=0) QueuetoFile(&Q);
```


```
	fclose(fp);
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
//Stack Functions
```


```
void push(Stack *S, char x[]){
```


```
	Node *cur, *nn;
```


```
	nn=(Node*)malloc(sizeof(Node));
```


```
	strcpy(nn->car_id, x);
```


```
	nn->next=NULL;
```


```
	if(S->Top==NULL){
```


```
		S->Top=nn;
```


```
		S->numElements++;
```


```
		return;
```


```
	}
```


```
	if(S->numElements < S->capacity){
```


```
		nn->next=S->Top;
```


```
		S->Top=nn;
```


```
		S->numElements++;
```


```
	}
```


```
}
```


```
void pop(Stack *S, char *car_id){
```


```
	if(S->Top==NULL){
```


```
		printf("Stack is empty!\n");
```


```
	}
```


```
	else{
```


```
		strcpy(car_id, S->Top->car_id);
```


```
		S->Top=S->Top->next;
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
void StacktoFile(Stack S){
```


```
	FILE *fp;
```


```
	Node *cur;
```


```
	char output_file[10];
```


```
	char buffer[2];
```


```
	char car_id[10];
```


```
	itoa(S.sail_num, buffer, 10);
```


```
	strcpy(output_file, "s");
```


```
	strcat(output_file, buffer);
```


```
	strcat(output_file, ".txt");
```


```
	fp=fopen(output_file, "w");
```


```
	while(S.Top!=NULL){
```


```
			pop(&S, car_id);
```


```
			fprintf(fp, "%s\n", car_id);
```


```
	}
```


```
	fclose(fp);
```


```
}
```


```
  

```


```
//Queue Functions
```


```
void add(Queue *Q, char x[]){
```


```
	Node *cur, *nn;
```


```
	nn=(Node*)malloc(sizeof(Node));
```


```
	strcpy(nn->car_id, x);
```


```
	nn->next=NULL;
```


```
	if(Q->front == NULL){
```


```
		Q->front=Q->rear=nn;
```


```
		Q->numElements++;
```


```
	}
```


```
	if(Q->numElements<Q->capacity){
```


```
		cur=Q->front;
```


```
		while(cur->next!=NULL){
```


```
			cur=cur->next;
```


```
		}
```


```
		cur->next=nn;
```


```
		Q->rear=nn;
```


```
		Q->numElements++;
```


```
	}
```


```
	else{
```


```
		QueuetoFile(Q);
```


```
	}
```


```
}
```


```
void delete(Queue *Q, char *car_id){
```


```
	if(Q->front==NULL){
```


```
		printf("Queue is Empty!\n");
```


```
	}
```


```
	else{
```


```
		if(Q->front==Q->rear){
```


```
			strcpy(car_id, Q->front->car_id);
```


```
			Q->front=Q->rear=NULL;
```


```
			Q->numElements=0;
```


```
		}
```


```
		else{
```


```
			strcpy(car_id, Q->front->car_id);
```


```
			Q->front=Q->front->next;
```


```
			Q->numElements--;
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
void QueuetoFile(Queue *Q){
```


```
	Node *cur;
```


```
	FILE*fp;
```


```
	int i;
```


```
	char output_file[10];
```


```
	char buffer[2];
```


```
	char car_id[10];
```


```
	itoa(Q->sail_num, buffer, 10);
```


```
	strcpy(output_file, "q");
```


```
	strcat(output_file, buffer);
```


```
	strcat(output_file, ".txt");
```


```
	fp=fopen(output_file, "w");
```


```
	while(Q->front!=NULL){
```


```
		delete(Q, car_id);
```


```
		fprintf(fp, "%s\n", car_id);
```


```
	}
```


```
	Q->sail_num++;
```


```
	Q->numElements=0;
```


```
	fclose(fp);
```


```
}
```

  



    You again could do some things in another way! I had limited time and used some things that were not so good in some regions! Remember I had like 2 weeks with changes in the Tasks in between for this and the last Exercise! The only thing that matters is that the Code worked fine and got me the best grade I could get! I don't changed the Code so that you see what kind of Code structure happens when you have to finish something in a specific Time Limit. Off course, I would have changed many many things if I had more time!


  



This was the end of today's Post! Hope you enjoyed it :)  

Thanks!


* * *

## C Language

<br>

{% include programming/c_topics.html %}

---
layout: default
title: Advanced Lists and Queues
description: C Advanced Lists and Queues
thumbnail: /images/tutorials/programming/c.png
categories: [programming, c]
tags: [programming, c, datastructures]
permalink: /tutorials/:categories/:title
---

# C Advanced Lists and Queues
* * *

 ![](http://www.tutorialsteacher.com/Content/images/csharp/csharp-queue.png)


   After talking about Basic Linked Lists and Queues that are implemented using them let's take a look today at more Advanced Lists and Queues. We will talk about **Double Linked Lists,** **Circular Linked Lists** and **Priority Queues** in **C Language**. If you want haven't seen it yet [here](https://steemit.com/programming/@drifter1/programming-c-linked-lists) the post I uploaded that explains the Basic Linked List Structures. Now, without further do, let's get started!


# Double Linked Lists:


    As we already know a basic Linked Lists contains Nodes from which one called head points to all the Items of the List. Every Node has a pointer to the next Item in the List. Our struct was defined like that:



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

    All that changes from going into Double Linked Lists is that we also point to our previous Item. So, now our struct contains also a Pointer called prev like this:



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
    struct Node *prev;
```


```
}Node;
```

    So, now we can find our previous Item in an much easier way and our Delete Function will become much easier and we will also don't need an Recursion to print our List backwards!


All the Functions that we used last time will work again, except that we now have to tweak some stuff on our prev pointer to! 


  



The Way we insert a new Node looks like this:



```
Node *nn;
```


```
// create our new node
```


```
nn = (Node*)malloc(sizeof(Node));
```


```
nn->val = val;
```


```
nn->next = NULL;
```


```
nn->prev = NULL;
```

  



Now let's take a look at all **function**s:



```
Node *insertFirst(Node *head, int val){
```


```
	Node *nn;
```


```
	// create our new node
```


```
	nn = (Node*)malloc(sizeof(Node));
```


```
	nn->val = val;
```


```
	nn->next = NULL;
```


```
	nn->prev = NULL;
```


```
	// check if list is empty
```


```
	if(head == NULL){
```


```
		// return pointer to nn
```


```
		return nn;
```


```
	}
```


```
	// set head to be our next pointer
```


```
	nn->next = head;
```


```
	// return pointer to nn
```


```
	return nn;	
```


```
}
```

  




```
Node *insertLast(Node *head, int val){
```


```
	Node *nn, *cur;
```


```
	// create our new node
```


```
	nn = (Node*)malloc(sizeof(Node));
```


```
	nn->val = val;
```


```
	nn->next = NULL;
```


```
	// check if list is empty
```


```
	if(head == NULL){
```


```
		// return pointer to nn
```


```
		return nn;
```


```
	}
```


```
	// set cur to point to our list
```


```
	cur = head;
```


```
	// use a while loop to find the last Item
```


```
	while(cur->next != NULL){
```


```
		// set cur to next Item
```


```
		cur = cur->next; 
```


```
	}
```


```
	// next of last Item will be our new node
```


```
	cur->next = nn;
```


```
	// prev of nn will be our cur pointer
```


```
	nn->prev = cur;
```


```
	// return head
```


```
	return head;	
```


```
}
```

  



DeleteFirst() doesn't change!


  




```
Node* deleteLast(Node *head){
```


```
	Node *cur;
```


```
	// check if list is empty
```


```
	if(head == NULL){
```


```
		// simply return it back after printing
```


```
		printf("Empty List!");
```


```
		return head;
```


```
	}
```


```
	// check if first Item is the only Item
```


```
	if(head->next == NULL){
```


```
		// make the list NULL
```


```
		return NULL;		
```


```
	}
```


```
	// set cur to point to our list
```


```
	cur = head;
```


```
	// use a while loop to find the last Item
```


```
	while(cur->next != NULL){
```


```
		// set cur to next Item
```


```
		cur = cur->next; 
```


```
	}
```


```
	// set the prev pointer's next pointer to NULL
```


```
	cur->prev->next = NULL;
```


```
	// return head
```


```
	return head;
```


```
}
```

  



Tweaking some things we can make the previous function work for specific value deletion like this:



```
Node* deleteVal(Node *head, int val){
```


```
	Node *cur;
```


```
	int found = 0;
```


```
	// check if list is empty
```


```
	if(head == NULL){
```


```
		// simply return it back after printing
```


```
		printf("Empty List!");
```


```
		return head;
```


```
	}
```


```
	// check if first Item is the only Item
```


```
	if(head->next == NULL){
```


```
		//check if value is the same
```


```
		if(head->val == val){
```


```
			return NULL;
```


```
		}		
```


```
		printf("%d was not found!\n", val);
```


```
		return head;	
```


```
	}
```


```
	// set cur to point to our list
```


```
	cur = head;
```


```
	// use a while loop to find the Item
```


```
	while(cur->next != NULL){
```


```
		// check val
```


```
		if(cur->val == val){
```


```
			found = 1;
```


```
			break;
```


```
		}
```


```
		// set cur to next Item
```


```
		cur = cur->next; 
```


```
	}
```


```
	// check if not found
```


```
	if(found == 0){
```


```
		printf("%d was not found!\n", val);
```


```
		return head;
```


```
	}	
```


```
	// set the prev pointer's next pointer 
```


```
	// to the next pointer of Node to be deleted
```


```
	cur->prev->next = cur->next;	
```


```
	// return head
```


```
	return head;
```


```
}
```

  



SearchList() doesn't change and we can do our Printing and Reverse Printing the same way we did before. We can also go to the last item and start going back for reverse printing!


  



# Circular Linked Lists:


    A Circular List is a Linked List where the last Item points to the First Item and so we can go round and round. I won't go very deep into them, but to let you know it is pretty easy to insert cause when inserting first we set the last item to point to the item just inserted and when inserting last we set this item to point to our head.


    The problem comes in the functions is that we could iterate infinitely if we don't do it right. The best way I think is to check if the head and the current Item are the same in a do-while loop, so that it iterates the first time, but when we get to it again we will stop. This can work with every function we talked about in our Basic Linked List Tutorial. We could also make it be a Double Linked List, to make things easier in some parts (like deleting).


  



# Priority Queues:


    We already know how to set up a Queue using Linked Lists and Arrays, cause we talked about them in previous posts. When going into priorities we will have to define what kind of priority we want to give. In Java we used a Priority Queue, for example, that putted the Items in priority using the alphabetic or natural ordering of the String Representations.


    We could do it in an similar way in C again, by having each Item inserted have a priority "number" (that doesn't have to be a variable, cause as we saw in Java we just used a variable of the Object itself) that puts the Item inserted in the right spot in the Queue directly or have the Queue sort itself after inserting using an ordering/sorting algorithm that puts the Items in order. 


    When getting an Item from the Queue we then get the Item that has the biggest priority by simply getting the Item in the front.


    Let's get into some Coding now. We will use an Linked List Implementation and our Node struct will contain an priority variable that we will declare when inserting it in the queue using our Enqueue function that I will leave for last. So, our structs look like this:



```
typedef struct Node{ 
```


```
	int val;
```


```
	int priority;
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
typedef struct Queue{
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

 The dequeue and print functions will be exactly the same as last time.



```
int dequeue(Queue *Q){
```


```
	int val;
```


```
	// check if empty
```


```
	if(Q->front == NULL){
```


```
		return -1;
```


```
	}
```


```
	// get value in front
```


```
	val = Q->front->val;
```


```
	// check if one item inside
```


```
	if(Q->front == Q->rear){
```


```
		Q->front = Q->rear = NULL;
```


```
	}
```


```
	// basic case
```


```
	else{
```


```
		// make front point to next
```


```
		Q->front = Q->front->next;
```


```
	}
```


```
	//return the value 
```


```
	return val;	
```


```
}
```

  




```
void print(Queue Q){
```


```
	int val;
```


```
	// check if empty
```


```
	if(Q.front == NULL){
```


```
		printf("Queue is Empty!\n");
```


```
		return;
```


```
	}
```


```
	// call dequeue as long as there are items
```


```
	while((val= dequeue(&Q)) != -1){
```


```
		printf("%d ", val);
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

    Now into the new Stuff: Our Enqueue function will find the right spot by sorting our List based on priority after each insertion. To make it easier and faster we will insert our new Node at the Front and afterwards sort our Queue.



```
void enqueue(Queue *Q, int val, int priority){
```


```
    Node *cur, *nn, temp;
```


```
    // create new node
```


```
    nn = (Node*)malloc(sizeof(Node));
```


```
    nn->val = val;
```


```
    nn->priority = priority;
```


```
    nn->next = NULL;
```


```
    // check if empty
```


```
    if(Q->front == NULL){
```


```
	Q->front = Q->rear = nn;
```


```
	return;
```


```
    }
```


```
    // insert new Node at front
```


```
    nn->next = Q->front;
```


```
    Q->front = nn;
```


```
	
```


```
    // order using priorities
```


```
    cur = Q->front;
```


```
    while(cur->next != NULL){
```


```
	// check priorities
```


```
	if(cur->priority < cur->next->priority){
```


```
		// swap Node values and priorities
```


```
		temp = *cur;
```


```
		cur->val = cur->next->val;
```


```
		cur->priority = cur->next->priority;
```


```
		cur->next->val = temp.val;
```


```
		cur->next->priority = temp.priority;
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
}
```

  



Last but not least here a programm that uses those functions:



```
int main(){
```


```
	// initialize Queue
```


```
	Queue Q;
```


```
	Q.front = Q.rear = NULL;
```


```
	print(Q);
```


```
	// add 5 to queue
```


```
	enqueue(&Q, 5, 2);
```


```
	print(Q);
```


```
	// add 10 to queue
```


```
	enqueue(&Q, 10, 5);
```


```
	print(Q);
```


```
	// add 3 to queue
```


```
	enqueue(&Q, 3, 1);
```


```
	print(Q);
```


```
	// remove from queue
```


```
	int val;
```


```
	val = dequeue(&Q);
```


```
	if(val == -1){
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
		printf("%d\n", val);
```


```
	}
```


```
	print(Q);		
```


```
}
```



That was the end of today's post. Hope you enjoyed it! :)


* * *

## C Language

<br>

{% include programming/c_topics.html %}

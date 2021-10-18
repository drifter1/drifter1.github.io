---
layout: default
title: Function Comparison
description: C Function Comparison
thumbnail: /images/tutorials/programming/c.png
categories: [programming, c]
tags: [programming, c, other]
permalink: /tutorials/:categories/:title
---

# C Function Comparison
* * *


![](https://cdn.intellipaat.com/mediaFiles/2015/12/C-Tutorial1.png)


    Hello again, its me! This time we will talk about how we **compare Funtions** to see which one is better! I will compare **using time** that the function takes from start to finish. And also explain what you have to do to **calculate** other stuff like **iterations** or **specific calculations** of any algorithm or **comparations** and **swaps** of sorting algorithms. So, without further let's get started!


  



# Getting Time:


    To get the Time that a function runs we will use some methods from the time.h C Library! We will get the time before and the time after, and then find the time that has passed subtracting end from start!


    We use 2 Variables of type **clock\_t** called **start** and **end**, and a double Variable double **time\_passed** that will store the difference in seconds (including floating point) from start to end. To get the clocktime we will use the function **clock()** that returns a Variable of type clock\_t. And finally then the time\_passed will not be exactly the subtraction, but we will also need to divide this number with an constant number called **CLOCKS\_PER\_SEC**, cause we actually calculate the number of clocks passed and not the number of seconds passed and then convert it using that!


So, our **Code** looks like this:



```
clock_t start, end;
```


```
double time_passed;
```


```
start = clock();
```


```
// call function
```


```
end = clock();
```


```
time_passed = (double)(end-start)/CLOCKS_PER_SEC;
```

  



# Calculating something inside of a function:


    When this something is inside of an non-recursive function we simply use another variable and calculate it. But, when we are in an **recursive** function we have to **either** use **global** variables, so that the variable is visible everywhere, or use **static** variables that we declare in this function. Static variables are those whose **value doesn't change in different invocations** **of the function in which they are declared**! Its pretty simple to use this concept for calculating Swaps inside of an Recursive Sorting Function like QuickSort or MergeSort, but I will use only 2 different versions of InsertionSort to keep it simple!


  



# Compare Functions using Time:


    I will use 2 different implementations of the **InsertionSort** Algorithm, one is **non-recursive** and one will be **recursive**. We will calculate the time that the algorithms need to finish!


**Code:**



```
#include <stdio.h>
```


```
#include <stdlib.h>
```


```
#include <time.h>
```


```
  

```


```
#define N 20000
```


```
  

```


```
// non-recursive
```


```
void insertionSort(int arr[], int n)
```


```
{
```


```
   int i, j, key;
```


```
   
```


```
   for (i = 1; i < n; i++)
```


```
   {
```


```
       key = arr[i];
```


```
       j = i-1;
```


```
       
```


```
       while (j >= 0 && arr[j] > key)
```


```
       {
```


```
           arr[j+1] = arr[j];
```


```
           j = j-1;
```


```
       }
```


```
       arr[j+1] = key;
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
// recursive
```


```
void insertionSortRecursive(int arr[], int n)
```


```
{
```


```
    if (n <= 1)
```


```
        return;
```


```
 
```


```
    insertionSortRecursive(arr, n-1);
```


```
 
```


```
    int last = arr[n-1];
```


```
    int j = n-2;
```


```
 
```


```
    while (j >= 0 && arr[j] > last)
```


```
    {
```


```
        arr[j+1] = arr[j];
```


```
        j--;
```


```
    }
```


```
    arr[j+1] = last;
```


```
}
```


```
  

```


```
int main(){
```


```
	int A[N], B[N];
```


```
	int i;
```


```
	// fill both with same Random Numbers
```


```
	for(i = 0; i < N; i++){
```


```
		B[i] = A[i] = 1 + rand()%1000;
```


```
	}
```


```
	printf("\n");
```


```
	
```


```
	clock_t start, end;
```


```
	double time_passed;
```


```
	
```


```
	printf("InsertionSort non-recursive:\n");
```


```
	start = clock();
```


```
	insertionSort(A, N);
```


```
	end = clock();
```


```
	time_passed = (double)(end-start)/CLOCKS_PER_SEC;	
```


```
	printf("Time: %fs\n", time_passed);
```


```
	
```


```
	printf("InsertionSort recursive:\n");
```


```
	start = clock();
```


```
	insertionSortRecursive(B, N);
```


```
	end = clock();
```


```
	time_passed = (double)(end-start)/CLOCKS_PER_SEC;
```


```
	printf("Time: %fs\n", time_passed);
```


```
}
```

  



# Compare Functions using Calculations:


    I will compare two function that find the **GCD (Greatest Common Divisor)**. The first is one the algorithm we all known called **Euklid Algorithm** and the second one is an **Consecutive integer checking algorithm**. We will count the **number of mod calculations** those algorithms do and see which one is better (it's obvious that Euklid is the fastest!).


**Code:**



```
#include <stdio.h>
```


```
#include <stdlib.h>
```


```
  

```


```
void gcd(int m, int n){ // euklid algorithm
```


```
    int r;
```


```
    static int calc_num = 0; // mod count actually
```


```
	
```


```
    if(n == 0){
```


```
	printf("GCD: %d\n", m);
```


```
	printf("Calculations: %d\n", calc_num);
```


```
	calc_num = 0; //reset calc_num
```


```
	return;
```


```
    }
```


```
    r = m % n;
```


```
    calc_num++; // mod count
```


```
    gcd(n, r);
```


```
}
```


```
  

```


```
void gcd2(int m, int n){ // consecutive integer checking algorithm
```


```
    int t;
```


```
    int calc_num = 0; // mod count actually
```


```
	
```


```
    if(m < n){
```


```
	t = m;
```


```
    }
```


```
    else{
```


```
	t = n;
```


```
    }
```


```
	
```


```
    while(t > 0){
```


```
	calc_num++; // mod count 
```


```
	if(m % t == 0){
```


```
		calc_num++; // mod count 2
```


```
		if(n % t == 0){
```


```
			printf("GCD: %d\n", t);
```


```
			printf("Calculations: %d\n", calc_num);
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
	t--;
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
int main(){	
```


```
    srand(time(NULL));	
```


```
	
```


```
    int m = 100000 + rand() % (200000 - 100000 + 1);
```


```
    int n = 100000 + rand() % (200000 - 100000 + 1);
```


```
		
```


```
    printf("m: %d, n: %d\n", m, n);
```


```
		
```


```
    printf("Euclid algorithm:\n");		
```


```
    gcd(m, n);
```


```
		
```


```
    printf("Consecutive integer checking algorithm:\n");
```


```
    gcd2(m, n);
```


```
	
```


```
    return 0;
```


```
}
```

  



This is the end of today's post! Hope you enjoyed this change!


    I wanted to get away from the everyday Logic Design Posts for one day, and upload something else. Also, tomorrow I may not be able to upload something, cause I will not be home and I don't know if I will find the time to have something ready to just post it!


Until next time...Bye!


* * *

## C Language

<br>

{% include programming/c_topics.html %}

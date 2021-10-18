---
layout: default
title: Pointers, Strings and Files
description: C Pointers, Strings and Files
thumbnail: /images/tutorials/programming/c.png
categories: [programming, c]
tags: [programming, c, basics]
permalink: /tutorials/:categories/:title
---

# C Pointers, Strings and Files

* * *

In this post I will continue in C with a programm that reads from a textfile, does some String stuff on it (using String functions) and also uses Pointers (because of those functions).

# ![](http://www.codewithc.com/wp-content/uploads/2014/06/pointer-amperstand-asterisk.png)

# **Pointers: **

    As the name describes them, they are "pointing" to a _specific memory address_. They **don't** save any value information, but only the **location** of this value in memory. The _Array_ on its own (A) is also an pointer and the first item of an _Array_ (A[0]) is equal to the value the Array is pointing at. **For example**, if an char Array (or String) is saved at the location 12000 and we want to get the item in index 5 (first one is at index 0) we will go to the location 12000 + 5 * _sizeof(char)_ = 12005, with _sizeof(char)_ being a method in C that returns the size of one char variable (it actually is not necessary in this one , because sizeof(char) = 1). This is how the A[index] stuff actually works in the background.

**Simple Calculation Stuff with Pointers: **

_We will not use much of it today,  but you should know some stuff for the next post._

Let's take an char *p pointer as example. (*name is how you tell if something is a pointer)

**Go to the next value:** if you do something like p++ that increments it by 1, you change the location its looking at. _For example_ if p is pointing at 1000 then with p++ you go to the next "save" address of an value and so p will point at 1000 + 1*sizeof(char) that equals 1001 and is the same as doing p[1] (you can use a pointer as an array to and that's how you should think about it in the beginning to). You can do the same with negative numbers like p = p - 2.

**Change the value it's pointing at:** If you use *p then u are looking at the value of the pointer in some point. _For example,_ if you want to change the value to 5, not at the beginning but at the 3rd index p is pointing at the you have to do: *(p + 3) = 5\. This works because the * modifier is called after the math stuff and so we first go to position p + 3*sizeof(char) and then change the value of that to 5, like doing p[3] = 5. 

**Making it look at something:** To make it point something you just make it equal the value's address in memory. _For example,_ if we have a char variable called c with value 'a' then if we do: p = &c (& is used to get the address of the variable) we make p point at it. Afterwards, we could change the value of the char variable c only by changing the value p is pointing at like: *p ='b' and so on.

# ![](https://www.tutorialspoint.com/cprogramming/images/string_representation.jpg)

# **Strings: **

    They are just char arrays with a little difference from normal arrays. You put an \0 or NULL at the last index so that the functions ( like printf("%s", string) ) know where it ends. You can set it up in to ways: 

1.  char string[N], with N being the number of characters it will have - 1, because of the NULL Value at the end. 
2.  char *string, with it being an dynamic string that will need dynamic memory allocation (do it in next post).

We will use the **string.h** library functions to do some cool stuff with them.

# ![](https://upload.wikimedia.org/wikipedia/commons/thumb/2/23/Text-txt.svg/400px-Text-txt.svg.png)

# **Files: **

    Files are documents saved in **physical storage** like HDD Drives and not in the RAM and are a method of saving stuff the programm calculated to use it the next time the programm runs or for viewing it afterwards in the same programm (for information that is statistic and isn't saved in an array or something like that and can be "reloaded" to the programm). Also, you can use the information of a file, as a text and find words, letters and other stuff on it and print some stuff about it out on screen or on another file, and exactly this is what we will do at the Coding Section. 

    Files are "pointers" in c. To create a variable for files you do:  **FILE *fp**, that is a file pointer called fp of type FILE, a specific datatype used for reading from and writing into files from the stdio.h library. To make it read a file or write/create a file you do **fp = fopen(name, mode**). The name parameter is the name it should have (when writing) or the name it has in the disk (when reading), mode can be: "r", "w", "a", "r+", "w+" or "a+". We will use only "r" for reading and "w" for creating and writing. Later on maybe even "a" for putting the new stuff at the end of the file without overwriting it from the start. You can look at [http://www.cplusplus.com/reference/cstdio/fopen/](http://www.cplusplus.com/reference/cstdio/fopen/) for more information. For reading and writing we will use **fscanf** and **fprintf**.

# **Code:**

Suppose we have the text:

`"Wedlock suits you," he remarked. "I think, Watson, that you have`

`put on seven and a half pounds since I saw you."`

`"Seven!" I answered.`

We want to:

*   find how many times a word (at least 2 characters and no numbers inside) appears in it
*   find how many words start with a specific character (input from user) and print them out
*   find how many words end with a specific character (input from user) and print them out
*   find how many times a specific character of the alphabet appears in the text
*   print all the words in a new textfile called words.txt, with them being in alphabetic order and having the first and last character capitalized.

_Note:_ We will use Functions for most stuff to make it easier to read. Functions can be really tough, but we will make them much easier having many arguments as global variables. **Functions** are just lines of Code that are reused or do a specific job and can be called in the main function, exactly like we used the printf(), scanf() function, but are written by the programmer and are not already made. 

First make sure to have a textfile called "text.txt". You can use another location, but to make it easier we will put it in the same directory as our programm's .c file. After running it you should find the file in the Explorer.

```c++
    #include <stdio.h> //for input, output, files

    #include <string.h> //for string functions

    char text[1000]; //text string of size 1000

    char words[100][20]; //string array for 100 strings with max of 20-1=19 size

    int words_freq[100]; //array for max of 100 word frequency's (they can be less)

    int letters_freq[26]; //array with the frequency's of the letters of the alphabet in the text

    int word_count = 0; //word counter

    char *p; //pointer for char functions

    void read_text_from_file(); //function to read the text from the file

    void letter_frequency(); //find letter frequencies

    void separate_words(); //find the words from the text, without repeat and with frequency's

    void sort_words(); //sorts the words array alphabetically

    void print_words_to_file(); //print words to file with first and last letter being caps

    int main(){

    	int i;

    	int count;

    	char letter; //letter to search for

    	read_text_from_file();

    	printf("Text:\n%s", text); //print text

    	letter_frequency();

    	separate_words();

    	sort_words();

    	//print words

    	printf("\nWords:\n");

    	for(i = 0; i < word_count; i++){

    		printf("words[%d] = %s (freq = %d)\n", i, words[i], words_freq[i]);

    	}

    	print_words_to_file();

    	printf("\nSearch for words starting with: ");

    	scanf("%c", &letter);

    	fflush(stdin);

    	if(letter <= 'Z'){ //if they give big one

    		letter = letter + 32;

    	}

    	count = 0;

    	for(i = 0; i < word_count; i++){ //search all words

    		if( words[i][0] == letter ){ //check first letter

    			printf("%s starts with %c\n", words[i], letter);

    			count++;

    		}

    	}

    	if(count == 0){ //if nothing found

    		printf("No word starts with %c!\n", letter);

    	}else{

    		printf("%d words start with %c!\n", count, letter);

    	}

    	printf("\nSearch for words ending with: ");

    	scanf("%c", &letter);

    	fflush(stdin);

    	if(letter <= 'Z'){ //if they give big one

    		letter = letter + 32;

    	}

    	count = 0;

    	for(i = 0; i < word_count; i++){ //search all words

    		if( words[i][strlen(words[i])-1] == letter ){ //check last letter

    			printf("%s starts with %c\n", words[i], letter);

    			count++;

    		}

    	}

    	if(count == 0){ //if nothing found

    		printf("No word ends with %c!\n", letter);

    	}else{

    		printf("%d words end with %c!\n", count, letter);

    	}

    }

    void read_text_from_file(){

    	char buf[80]; //buffer for reading line by line

    	FILE *fp; //file pointer

    	fp = fopen("text.txt", "r"); //open the text for reading

    	if(fp == NULL){ //error checking

    		printf("File not found!\n"); 

    	}

    	fgets(buf, 80, fp); //read from the file

    	strcpy(text, buf); //set the text to the first buffer

    	while( fgets(buf, 100, fp) != NULL){ //read until end of file

    		strcat(text, buf); //add buffer at the end of the string, concatenating them

    	}	

    	fclose(fp); //close the file	

    }

    void letter_frequency(){

    	int i, j;

    	char letter = 'a';

    	for(i = 0; i < 26; i++){ //for every letter in the alphabet

    		letters_freq[i] = 0;

    		for(j = 0; j < strlen(text); j++){

    			if(text[j] == letter || text[j] == letter - 32){ //if it is the small or cap letter

    				letters_freq[i]++;

    			}

    		}	

    		letter++; //go to next letter

    	}

    	letter = 'a';

    	printf("\nFrequency of Letters:\n");

    	for(i = 0; i < 26; i++){

    		printf("%c: %d\n", letter, letters_freq[i]);

    		letter++;

    	}

    }

    void separate_words(){

    	int i;

    	int number, min_length, same; //flags for words

    	p = strtok(text," \"\n\t\r,.-;!"); //p will point at the next address that is not one of the tokens (second parameter)

    	while (p != NULL){ //while not at the end of the text

    		number = 0; //no number in "word"

    		min_length = 1; //length must be at least 2 to be a word

    		if(strlen(p) > 1); //if enough do nothing

    		else min_length = 0; //too small length

    		for(i = 0; i < strlen(p); i++){ //search whole "word" for numbers

    			if(p[i] >= '0' && p[i] <= '9'){ //numbers are in character form and because of ASCII one after another

    				number = 1; //there is a number inside

    			}

    		}

    		//make all capital letters small letters

    		if( p[0] <= 'Z'){ //in ASCII all characters are in alphabetic order 

    				p[0] = p[0] + 32; //small ones are 32 "higher" then capital ones

    		}

    		if(number == 0 && min_length == 1){  //if it is doesn't have numbers and is at least of length two

    			same = 0; //words is not inserted yet

    			//search for the word in all the inserted words

    			for(i = 0; i <word_count; i++){ 

    				if( strcmp(p, words[i]) == 0 ){ //if p and words[i] are equal it will return 0

    					same = 1; //word already inserted

    					words_freq[i]++; //increment the frequency of the word

    					break; //break the for loop, cause you can't find it another time

    				}

    			}

    			if(same == 0){ //if it was not inserted

    				strcpy(words[word_count], p); //insert word into array

    				words_freq[word_count] = 1; //set frequency to 1

    				word_count++; //update word counter

    			}			

    		}

    		p = strtok(NULL," \"\n\t\r,.-;!"); //continue from where you stopped at the text searching for words

    	}

    }

    void sort_words(){

    	int i, j;

    	char word[20]; //temporary word for swapping

    	for(i = 0; i < word_count; i++){

    		for(j = i; j < word_count; j++){

    			if( strcmp(words[i], words[j]) > 0 ){ //when it returns > 0 it means first one is higher alphabetically

    				//swap using temporary variable

    				strcpy(word, words[i]);

    				strcpy(words[i], words[j]);

    				strcpy(words[j], word);

    			}

    		}

    	}

    }

    void print_words_to_file(){

    	FILE *fp; //file pointer

    	int i;

    	char word[20]; //temporary word for editing

    	fp = fopen("words.txt", "w"); //open file for writing

    	for(i = 0; i < word_count; i++){

    		strcpy(word, words[i]);

    		if(words[i][0] >= 'a') word[0] = word[0] - 32; //if first letter small then make it cap with -32

    		if(words[i][ strlen(words[i])-1 ] >= 'a') word[strlen(words[i])-1] = word[strlen(words[i])-1] - 32; //if last one is small do the same

    		fprintf(fp, "%s\n", word); //write word to file

    	}

    	fclose(fp); //close file

    }
```

* * *

## C Language

<br>

{% include programming/c_topics.html %}
---
layout: default
title: Beginner Codes
description: C Beginner Codes
thumbnail: /images/tutorials/programming/c.png
categories: [programming, c]
tags: [programming, c, basics]
permalink: /tutorials/:categories/:title
---

# C Beginner Codes
* * *

I will not explain every single thing like what is an if, while, for statement, how you can print in the Console and so on. You can look that all up in the Internet searching for C Basics. Here, we will start with some Codes that implement those things and shows you exactly what you can do with them in practice.

* * *

## Code1:

Suppose we have a Tollbooth and we want to count the number of Cars, Bikes and Trucks that passed by. We also want to calculate how much we earned in total, total for every Vehicletype and the avg of all, when a Car pays fee of 5, a Bike fee of 3 and a Truck fee of 10. We will get the Vehicletype as Input and have some kind of specialtype that means terminate the program after printing the results. 

```c++
#include <stdio.h> //for input and output methods
int main(){

    int vehicles=0, cars=0, bikes=0, trucks=0; //counter variables for each type and all together(optional)

    char type; //we will get input from the user and 'c' will be Car, 'b' Bike and 't' Truck (maybe even Capitals)

    int fee; //fee the current Vehicle has to pay

    int total, total_cars, total_bikes, total_trucks; //total payment for all together and each type at it's own

    float avg; //floating point number for the average

    printf("Tollbooth Counter for Cars(c), Bikes(b) and Trucks(t)\n"); //printing message

    do{ //do-while loop because we want to run it at least one time and check afterwards the Condition

        printf("Vehicle Type: ");

        scanf("%c", &type); //getting input from user

        fflush(stdin); //clearing the keyboard buffer...DONT EVER FORGET IT WHEN YOU USE CHAR'S

       //checking the input 

        if( type == 'c'){

            fee = 5;

            cars++; //cars counter goes 1 up

        }

        else if( type == 'b'){

            fee = 3;

            bikes++; //bikes counter goes 1 up

        }

        else if(type == 't'){

            fee = 10;

            trucks++; //trucks counter goes 1 up

        }

        else{ //this is for every other type like 'x'

            fee = 0;

            continue; //with this statement we make sure that is dont continue downwards 

            //but gets back to the start of the do-while loop 

        }

        vehicles ++; //counter for vehicles goes 1 up

        printf("You have to pay %d!\n", fee); //we print how much it has to pay

    }while(type != 'x'); //we will continue getting input until we get a 'x' Type

    printf("A total of %d Vehicles passed by\n", vehicles); //print how many passed by

    printf("Cars: %d, Bikes %d, Trucks %d\n", cars, bikes, trucks);

    //for the total amount we got paid we can put statements at every single car

    //but because we know how many passed of each type 

    //and the fee is the same we can make the calculations down here

    //calculating for each type

    total_bikes = bikes * 3;

    total_cars = cars * 5;

   total_trucks = trucks * 10; 

   //total is the sum of the above

   total = total_bikes + total_cars + total_trucks; 

   avg = (float) total / vehicles; //typecasting to convert the integers to floats and get the right answer

    printf("We earned %d in total\n", total);

    printf("From Cars: %d, Bikes: %d, Trucks: %d\n", total_cars, total_bikes, total_trucks);

    printf("Average is %.2f\n", avg); //we use %.2f to have only 2 floating point precision

    //when you put like %a.bf you have a a-sized integer value and b-sized floating point precision

}

```

* * *

## Code2:

Let's make the same as in Code1 but with some stuff more. Everybody has to pay in cash, with card or both to pay the fee. We want to calculated how many paid with Card, In Cash and both, and how much we earned from Card and in Cash. Also, we will not get the Type as an input anymore but the ID value of the Driver (id is an integer with up to 5 numbers) and this will impact to it's Type to make it more interesting. Last number is 1, 4 or 7 means it's a Bike, 2, 5 or 8 it's a Car and 3,6,9 it's a Truck. If it's 0 it will impact as the stop point and the program will print the results and finish.

```c++
#include <stdio.h> //for input and output methods

#include <stdlib.h> //for the atoi() method

int main(){

    int vehicles=0, cars=0, bikes=0, trucks=0; //counter variables for each type and all together(optional)

    int card=0, cash=0, both=0; //counter variables for each payment type

    char driver_id[6]; //id of the driver

    int id; //converted value of id from char

    char type; //we get a value for each driver id

    int fee; //fee the current Vehicle has to pay

    int balance, money; //the card balance and money to pay (if card empty or not enough)

    int total, total_cars, total_bikes, total_trucks; //total payment for all together and each type at it's own

    int total_card=0, total_cash=0; //total payment for each payment type

    float avg; //floating point number for the average

    printf("Tollbooth Counter for Cars(c), Bikes(b) and Trucks(t)\n"); //printing message

    do{ //do-while loop because we want to run it at least one time and check afterwards the Condition

        printf("Driver ID: ");

        scanf("%5s", driver_id); //getting input from user as a string with %5s so that NULL is at the end of the string

       id = atoi(driver_id); //convert string to integer

       //checking the inputs last number with modulo 10

       if(id % 10 == 1 || id % 10 == 4 || id % 10 == 7) {

           type = 'b';

       }

        else if(id % 10 == 2 || id % 10 == 5 || id % 10 == 8) {

           type = 'c';

       }

      else if(id % 10 == 3 || id % 10 == 6 || id % 10 == 9) {

           type = 't';

       }

       else{

           type = 'x';

       }

        //checking type

        if( type == 'c'){

            fee = 5;

            cars++; //cars counter goes 1 up

        }

        else if( type == 'b'){

            fee = 3;

            bikes++; //bikes counter goes 1 up

        }

        else if(type == 't'){

            fee = 10;

            trucks++; //trucks counter goes 1 up

        }

        else{ //this is for every other type like 'x'

            break; //with this statement we make sure that it stops the loop

        }

        vehicles ++; //counter for vehicles goes 1 up

        printf("You have to pay %d!\n", fee); //we print how much it has to pay

       do{ //getting the balance with do-while

       printf("Card Balance: ");

        scanf("%d", &balance);

       }while(balance < 0); //making sure its not negative

       //checking balance status

       if (balance >= fee){ //pay with card

           balance = balance - fee;

           printf("New balance is %d!\n", balance);

           card++; //counter for card payment goes 1 up

           total_card += fee; //total payment from card goes up by fee

       }

       else if(balance == 0){ //pay with cash

           printf("Pay %d with Cash!\n", fee);

           cash++; //cash counter goes 1 up

           total_cash += fee; //total payment from cash goes up by fee

       }

       else{ //pay with both

           money = fee - balance; //cash to pay

           total_cash += money; //total payment from cash goes up by "money"

           total_card += balance; //total payment from card goes up by balance

           both++; //counter for both goes up by 1

           balance = 0;

           printf("New balance is %d!\n", balance);

           printf("Pay %d with Cash!\n", money);

      }        

    }while(type != 'x'); //we will continue getting input until we get a 'x' Type

    printf("A total of %d Vehicles passed by\n", vehicles); //print how many passed by

    printf("Cars: %d, Bikes %d, Trucks %d\n", cars, bikes, trucks);

    //calculating for each type

    total_bikes = bikes * 3;

    total_cars = cars * 5;

   total_trucks = trucks * 10;

   //total is the sum of the above

   total = total_bikes + total_cars + total_trucks; 

   avg = (float) total / vehicles; //typecasting to convert the integers to floats and get the right answer

    printf("We earned %d in total\n", total);

    printf("From Cars: %d, Bikes: %d, Trucks: %d\n", total_cars, total_bikes, total_trucks);

    printf("Average is %.2f\n", avg); //we use %.2f to have only 2 floating point precision

    //Card and Cash stuff

    printf("%d paid with Cash, %d with Card and %d with Both\n", cash, card, both);

    printf("We earned %d from Cash and %d from Card\n", total_cash, total_card);

}
```

* * *

## C Language

<br>

{% include programming/c_topics.html %}
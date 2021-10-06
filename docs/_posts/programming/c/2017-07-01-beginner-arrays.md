---
layout: default
title: Beginner Arrays
description: C Beginner Arrays
thumbnail: /images/tutorials/programming/c.png
categories: [programming, c]
tags: [programming, c, basics]
permalink: /tutorials/:categories/:title
---

# C Beginner Arrays

* * *

## Code:

We will extend the last one adding Arrays that will save the vehicle informations and print them all out.
All the values will be randomized and so the program doesn't need any user input. Also, we now don't have an driver_id but we will have a numberplate for each vehicle and the type will be also random. Last but not least we will count how many of each vehicletype paid with a specific payment type (like how many Cars paid only with Cash). 

```c++
#include <stdio.h> //for input and output functions
#include <stdlib.h> //rand() function
#define N 100 //making the value tweakable so that the programm will terminate after N=100 vehicles

int main(){

   int i=0; //vehicle counter variable
   int vehicles=0, cars=0, bikes=0, trucks=0; //counter variables for each type and all together
   int card=0, cash=0, both=0; //counter variables for each payment type
   int card_b=0, cash_b=0, both_b=0; // counter for payment type if Bike
   int card_c=0, cash_c=0, both_c=0; // if Car
   int card_t=0, cash_t=0, both_t=0; //  if Truck

   int plate; //plate of current vehicle
   int plates[N]; //plate array of all vehicles

   int fee; //fee the current Vehicle has to pay
   int balance_bef[N], balance_aft[N]; //array for balance before and after payment of fee

   int total, total_cars, total_bikes, total_trucks; //total payment for all together and each type at it's own
   int total_card=0, total_cash=0; //total payment for each payment type
   int fees[N], cash_p[N], card_p[N]; //array of fees, payment with cash and payment with card for each vehicle
   int r; //random number for generating random type

   char type; //we get the value randomly with 'r'
   char types[N]; //type array of all vehicles
   char p_types[N]; //payment type array of all vehicles

   float avg; //floating point number for the average

   srand(time(NULL)); //rand() function seed set to current time, so that each time runned the program gives other values
   
  while(i<N){ //run until i equals N, so for N vehicles
       //plate will be random number between 10000...90000
       plate = 10000 + rand()%(90000 - 10000 + 1);  //random_value = start + rand()%(end - start +1)
       plates[i] = plate; //save the current plate to the array

       //balance will be random between 0...10
       balance_bef[i] = rand()%11;

       //random type and find it's fee
       r  = 1 + rand()%3; //value will be 1, 2 or 3
      if(r == 1){
          type = 'b'; //bike
          bikes++;
          fee = 3;
      }
      else if(r == 2){
           type = 'c'; //car
           cars++;
           fee = 5;
      }
      else{ //if 3
          type = 't'; //truck
          trucks++;
          fee = 10;
      }
      types[i] = type; //saving type to array
      fees[i] = fee; //fee to array
      vehicles++;

      //payment
      if ( balance_bef[i] >= fee){ //pay with card
          balance_aft[i] =  balance_bef[i] - fee; //new balance
          cash_p[i] = 0; //nothing paid in cash
          card_p[i] = fee; //fee paid with card
          card++; //counter for card payment goes 1 up
          total_card += fee; //total payment from card goes up by fee
          p_types[i] = 'c'; //card payment type
   }

   else if( balance_bef[i] == 0){ //pay with cash
       balance_aft[i] = 0; //balance remains 0
       cash_p[i] = fee; //fee paid with cash
       card_p[i] = 0; //nothing paid with card
       cash++; //cash counter goes 1 up
       total_cash += fee; //total payment from cash goes up by fee
       p_types[i] = 'm'; //cash payment type (money)
   }

   else{ //pay with both
       balance_aft[i] = 0; //new balance is 0
       cash_p[i] = fee -  balance_bef[i];
       card_p[i] = balance_bef[i];
       both++; //counter for both goes up by 1
       total_cash += cash_p[i] ; //total payment from cash goes up by cash paid
       total_card += balance_bef[i]; //total payment from card goes up by balance
       p_types[i] = 'b'; //both payment type (cash and card)
  }        

  i++; //counter goes up by one to go to the next vehicle
}
//Print Table with Information about all Vehicles
//I use \t to tab space them
printf("Plate\tType\tBalance bef.\tFee\tBalance aft/\tCash\tCard\tPayment Type\n\n");
for(i = 0; i < N; i++){

    printf("%d\t",plates[i]);
    if(types[i]=='b') printf("Bike\t");
    else if(types[i]=='c') printf("Car\t");
    else if(types[i]=='t') printf("Truck\t");
    printf("%d\t%d\t%d\t%d\t%dt", balance_bef[i], fees[i],balance_aft[i], cash_p[i], card_p[i]);
    if(p_types[i]=='c') printf("Card Only\n");
    else if(p_types[i]=='m') printf("Cash Only\n");
    else if(p_types[i]=='b') printf("Card and Cash\n");

}

//Statistics

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

//Separated for each vehicletype and payment type

for(i = 0; i < N; i++){ 
    if(types[i]=='b'){  
        if(p_types[i]=='c') card_b++;
        else if(p_types[i]=='m') cash_b++;
        else if(p_types[i]=='b') both_b++;  
     }
    else if(types[i]=='c'){
        if(p_types[i]=='c') card_c++;
        else if(p_types[i]=='m') cash_c++;
        else if(p_types[i]=='b') both_c++;      
    }
    else if(types[i]=='t'){
        if(p_types[i]=='c') card_t++;
        else if(p_types[i]=='m') cash_t++;
        else if(p_types[i]=='b')    both_t++;       
    }
}   

printf("Payment Type Counters:\n");
printf("Bikes:\nCard Only: %d,Cash Only: %d,Card and Cash: %d\n", card_b, cash_b, both_b);
printf("Cars:\nCard Only: %d,Cash Only: %d,Card and Cash: %d\n", card_c, cash_c, both_c);
printf("Trucks:\nCard Only: %d,Cash Only: %d,Card and Cash: %d\n", card_t, cash_t, both_t);
printf("All Together:\nCard Only: %d,Cash Only: %d,Card and Cash: %d\n", card, cash, both);
}
```
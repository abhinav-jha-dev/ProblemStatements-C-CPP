# C-CPP-Problem-Statements
I have tried to solve some of the problems that I have faced in C-CPP development to learn in deep concepts.

## Setting up Visual Studio Code for C C++ Development
If you have not setup your C CPP Development Environment then this will help you.

Download [MinGW](http://www.mingw.org/) by following Download tab. Install all the packages that MinGW Offers. For reference follow this [link](https://www.youtube.com/watch?v=DIw02CaEusY).

## Problem 1
Write a parallel program using pthread to accomplish the same as the following serial program. For the following serial program, the user enters a line and the program outputs the number of occurrences of each character.
For the parallel program if we have n threads we should divide the line into n segments and let each thread counts the characters of its segment.

**Note: Do not count the space or the tab characters.**

```
//File name: a.c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define ASCIIs		127		//ASCII characters from 0 to 127
#define atmost		1000


char letters[atmost + 1];	//Extra location for the string terminator '\0'
int count[ASCIIs];

int main(){
  int i, index;

  for(i = 0; i < ASCIIs; i++)
    count[i] = 0;

  printf("Enter a line not larger than 100 characters.\n");
  fgets(letters, atmost+1, stdin);//Read a line into array letters. This function adds '\0' to the end of the string

  for(i = 0; i < strlen(letters); i++){
    index = (int)letters[i];
    (count[index])++;
  }

  for(i = 33; i <  ASCIIs; i++)
    if(count[i] != 0)
      printf("Number of %c is: %d\n", i, count[i]); 
  return 0;
}

For example:

Enter a line not larger than 100 characters.
for(i = 0; i < strlen(letters); i++){
Number of ( is: 2
Number of ) is: 2
Number of + is: 2
Number of 0 is: 1
Number of ; is: 2
Number of < is: 1
Number of = is: 1
Number of e is: 3
Number of f is: 1
Number of i is: 3
Number of l is: 2
Number of n is: 1
Number of o is: 1
Number of r is: 3
Number of s is: 2
Number of t is: 3
Number of { is: 1

The boldfaced line is what the user entered.

```

**For solution run *solutions/problem1.cpp***


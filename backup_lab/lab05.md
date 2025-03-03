---
num: lab05
ready: true
desc: "Card game using Binary Search Trees"
assigned: 2024-02-14 09:00:00.00-8
due: 2024-02-23 23:59:00.00-8
---

# Collaboration policy
* This assignment can be done with a partner and must be completed in the true pair programming style as described in the syllabus. This means you and your partner should work on the same code base and you should be both present when developing your code.
* To learn more about pair programming, watch the following video (it takes less than 10 minutes): [http://bit.ly/pair-programming-video](http://bit.ly/pair-programming-video)

# Introduction

* Create a GitHub repo following the correct naming convention.
* Minimal starter code is provided for this lab, but be sure to grab it 
from GitHub

# Goal of this assignment

* Practice using Binary Search Trees
* Learn to organize a project's code structure on your own (not just 
filling in a template)
* Learn to design classes using good OOP design principles discussed in 
class
* Learn to refactor an existing solution to improve its design
* Learn to practice defensive coding strategies


# Instructions

In this lab you will implement a game in two different ways: one that uses the STL `set` container class and another that uses your custom implementation of a BST (based on the code your wrote for lab02)

## Starter code and required files

Refer to lab01 for instructions on how to set up a GitHub repository and 
pull the starter code for this lab.
Obtain the starter code from this repo: 
<https://github.com/ucsb-cs24-w24/STARTER-lab05>

Check that you have the following files:

**Common files for both implementations of the game**
* card.cpp, card.h   // These files should define any structures needed to represent a single card and associated operators. The classes you define here should be useful for both implementations of the game.

* Makefile // Generates two executables- the  first should be called `game_set` and the second should be called `game` (the expected output for game_set and game are the same and described later). The key difference is that `game_set` is the executable obtained by compiling `main_set.cpp` as a stand-alone program (which implements the game using the `std::set` container class), while `game` is the executable obtained from compiling the files `main.cpp` and `cards.cpp` which relies on your custom implementation of a BST.


**Implemenation 1: implementation of the game using std::set**  
* main_set.cpp

**Implementation 2: implementation of the game using your custom BST**
* card_list.cpp, card_list.h // These files should contain your implementation 
of the binary search tree to store a sequence of cards representing a player's hand
* main.cpp

Note: The files `main_set.cpp` and `main.cpp` should read in the cards of the two players from input files and put everything together to play the game. The key difference is that `main_set.cpp` only makes use of the STL `std::set` container class and the definitions in `card.h/cpp` to code the game (described later) while `main.cpp` uses definitions in `card.h/cpp` and `card_list.h/cpp` which contain your implementation of a BST (from lab01) modified for the purposes of this assignment. Implement main_set.cpp first!

* Text files used for testing

Create the following files:
* tests.cpp // These files should contain test code for all the classes 
and methods you used in your game with the custom BST (main.cpp). We recommend at least 5 test cases for 
each public member function. While the test file will not be evaluated, 
there is an expectation that you will produce test code that causes 
failues when seeking help from TAs/ULAs. Course staff help you more 
effectively if you show how your program fails on a local test case rather than pointing to test failures on Gradescope.

## The game

Alice and Bob are playing a game a bit like Go Fish, although neither of 
them is very good at it. The players are dealt two sets of cards which are 
provided in two separate files as inputs to your program. Although the 
cards in each player's hand is unique, duplicates exist in the other 
player's hand.

Once you have the sets of cards, the game begins. Alice and Bob take turns 
playing the game. Alice iterates forward through her hand in increasing 
order of the card values (see next section on how cards are ordered), 
checking whether Bob has that card. Once a matching card is found, your 
program should print the line "Alice picked matching card <card suit as a 
character> <card value as a number/character>". The card should then be 
removed from both players hands. 

The process then repeats, except this time, Bob looks through his cards 
starting with the largest card and working towards the smallest card. This 
means that while the first card Alice finds should be the first shared 
card (in order), the first card Bob finds should be the last shared card 
(in order). The game ends once they do not have any cards in common and 
you should print out the final hands of both players. Note that players do 
not draw any new cards during this process. 

The ordering of cards is described in the next section.

## Card ordering

The ordering of cards is determined first by its suit and then by the 
value:  

1. The ordering least to greatest is: **clubs, diamonds, spades, hearts**. 
Thus a club of any value is less than a diamond of any value.

2. The ordering within each suit is determined by the value from **least 
to greatest** as follows: 
ace, 2, 3, . . . 10, jack, queen, king. 

Based on the above two rules, the ordering of the following cards

h 9, c k, s 3, c a, h j, d 3

from smallest to largest would be

c a, c k, d 3, s 3, h 9, h j

## Your approach for the set-based implementation of the game

At the start of the program, you will read in Alice and Bob's starting 
hands from two files. The names of these files are provided as command 
line arguments with Alice's file in `argv[1]` and Bob's in `argv[2]`. The 
starter code opens the files for you as `ifstream` objects, which you can 
treat much like `cin`. You should read Alice and Bob's cards into two 
binary search trees. **In your first implementation of the game in (main_set.cpp)**, you should use std::set to store each players hand. Define a class and associated operators needed to represent a single card in `card.h/cpp`. When you run make, you should get an executable `game_set` that you can test with the text files available to you.

After you have a correct implementation that is based on std::set, test your program with the given input files


## Example run of the program

Contents of `alice_cards.txt`:
```
h 3
s 10
c a
c 3
s 5
h 10
d a
```

Contents of `bob_cards.txt`:
```
c 2
d a
h 10
c 3
d j
s 10
h a
```

Correct output after running `make` and then running `./game_set alice_cards.txt bob_cards.txt`:
```
Alice picked matching card c 3
Bob picked matching card h 10
Alice picked matching card d a
Bob picked matching card s 10

Alice's cards:
c a
s 5
h 3

Bob's cards:
c 2
d j
h a
```

Note: a=ace, k=king, q=queen, j=jack

## Approach for the custom BST implementation of the game

**In your second implementation of the game**, you must implement the binary search trees yourself in `card_list.h` and `card_list.cpp`. 
Don't worry about balancing the binary search trees (though you can try 
and optimize this if you like). Your binary search tree class should obey 
the card ordering rules given above. While implementing this, you may find 
it helpful to overload the operators `==`, `<`, and `>` on your card class 
so that you can easily choose which branches to go down on your binary 
tree. Note that you need to correctly handle the case of cards with the 
value 10 (which has two characters) and separately compare the value and 
suit, so storing the cards as strings is probably not the best approach.

Once you have implemented the bst that represents a player's hand, you must use it and put it altogether in `main.cpp` that implements the game using your custom implementation (your logic for this program should be very similar to `main_set.cpp` except you should not use std::set and use your custom BST implementation instead).

Correct output after running `make` and then running `./game alice_cards.txt bob_cards.txt` should produce the exact same output as before (when you ran `game_set` with the given input files).

## Testing your custom BST
An additional requirement is that you write a set of unit tests for your 
binary search tree. These should be in a file called `tests.cpp`, which 
you will submit, and you should write your Makefile so that running `make 
test` compiles and runs these tests. Note that there will be no Gradescope 
tests for these unit tests, so you can have the output in whatever format 
you find most helpful. You should test each of the functions on your 
binary search tree, which will include, at the very least, `find()`, 
`delete()`, `insert()`, `successor()`, and `predecessor()`. You should 
write these tests BEFORE implementing the full game to ensure that your 
binary search tree works correctly. Debugging one set of code is much 
easier than debugging two at the same time. This will also ensure that 
your are correctly separating your binary tree class from the rest of your 
program logic.


## Requirements

For this lab, you will have a lot of flexibility on your implementation 
(which just means we won't be providing a code framework for you to fill 
in). However, there are a few requirements that your mentor will check for 
when they look at your code. Keep these in mind as you think about your 
solution:

* You must use a binary search tree you implemented yourself to solve the 
problem, not another data structure or a class in the standard library. 
You must provide two implementations (one that is based on STL set (which is a balanced BST) and another that uses your custom binary search tree implementation (modified from lab02))
* Your binary search tree must implement a constructor, a destructor and 
other other methods as needed
* You code should be readable
* Your classes should define clear interfaces and hide implementation 
details as much as possible. 
* Your program must properly free all memory it allocates, including your 
binary tree nodes and any dynamically allocated data stored inside them. 
We will also check this with valgrind when you turn in your code to 
Gradescope.
* You do not need to worry about having multiple instances of the same 
card. Each card will appear only once per hand.

# Submission instructions 
You and your partner only need to make a single submission. Add your partner to Gradescope before you submit (or before the deadline).
Submit your code on Gradescope. You must organize your program in the 
files: main_set.cpp,  main.cpp, card.cpp, tests.cpp, card.h, card_list.cpp and card_list.h, Makefile
  
  



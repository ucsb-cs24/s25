---
layout: lab
num: lab05
ready: true
desc: "Implementing a min-heap"
assigned: 2025-05-09 9:00:00.00-8
due: 2025-05-23 23:59:00.00-8
---

# Collaboration policy
The lab may be done solo or with a partner. 

# Goals for this lab

By the time you have completed this lab, you should be able to

* Understand the purpose and behavior of a priority queue
* Understand how to implement a vector-based binary heap implementation.

## Step by Step Instructions

 
## Step 1: Get the starter code
Use scp to copy the starter code from CSIL from the following directory:

<https://github.com/ucsb-cs24-s25/STARTER-binaryheaplab/>


You should have the following files:

```
-bash-4.3$ ls
examheap.cpp heap.cpp heap.h
```

First look at heap.h to see the basic operations for a heap. You will implement all of these operations of a min-heap in this lab. Also notice the storage mechanism we will be using for the heap: a [http://www.cplusplus.com/reference/vector/](http://www.cplusplus.com/reference/vector/). It will probably be a good idea to read through the documentation for this standard library class (linked above) if you are not familiar with it.

Now look at examheap.cpp. This file will test your heap's behavior. The first test is quite simple and just adds a couple elements to your heap. For larger numbers of inputs, it uses the `std::priority_queue` class from the standard library as ground truth to test your code against. The first thing you need to do is compose your Makefile to compile `examheap.cpp` with `heap.cpp` to executable `examheap`. Then, feel free to compile and run `examheap` before starting on your code. However, note that all the tests will fail and say "Aborted (core dumped)".

## Step 2: Implement the functions of heap.cpp

There are four functions you need to implement in heap.cpp: `push`, `pop`, `top`, and `empty`. Note that only `push` and `pop` modify the heap, while `empty` and `top` only return values. When testing your code, be sure to run the large tests (4 and 5) to find any minor bugs in your code that may not show up on the smaller tests.

You are allowed to add helper functions in heap.h and heap.cpp if you need them. However, you should use the vector in heap.h as the underlying storage for your heap.

## Step 3: Submit heap.cpp and heap.h

Submit the files heap.cpp, heap.h, and Makefile to the assignment on Gradescope.

## Evaluation and Grading

Each student must accomplish the following to earn full credit for this lab:
heap.cpp and heap.h are saved, with your name(s) in a comment at the top and other evidence of your work. Both of these files should compile and execute properly too.


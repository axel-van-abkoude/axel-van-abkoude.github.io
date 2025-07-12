---
layout: post
title:  "Code Benchmarking"
categories: roadmap
tags: benchmarking cpu-performance caches
---

## Chapter 0: Hardware & Software
# What do we have??
TODO: Intro
- Make your experiments reproducable and gain insights in differences
    in reproduced results from others.

TODO: How to get hardware info
- lscpu (clock speed, architecture)
- lshw  (cache/ram info)

TODO: Latency of instructions
- Arithmatic instructions low latency
- Memory reads and writes more complex 
    - (use comparison of real time adding from ComputerFile: 
       https://www.youtube.com/watch?v=PpaQrzoDW2I)

TODO: How to get software info
- gcc -v

TODO: Provide scripts on how to get this information

## Chapter 1: Scoping
# What do we want to know?

What do we want to measure?
Why do we want to measure it?
Do we need to measure it?
Main takeaway: do not benchmark everything!
(talk about tools like valgrind etc)

TODO: Make Flowchart ending in benchmark or don't benchmark.


## Chapter 2: Theoretical speed
# What do we expect??

TODO: Intro
- Get insights on how an algorithm performs relative to theory

TODO: Introduce Complexity
- Big O theoretical concept
    - Time complexity
    - Space complexity
- Big O practical concept
    - A for loop where we do one multiplication and one addition:
{% highlight c %}
for (int r1 = 0; r1 < LEN_R1; r1++) {               /* n^1*add + n^1*lt  */
    for (int c2 = 0; c2 < LEN_C2; c2++) {           /* n^2*add + n^2*lt  */
        res[r1][c2] = 0;
        for (int c1 = 0; c1 < LEN_C1; c1++) {       /* n^3*add + n^3*lt  */ 
            res[r1][c2] += m1[r1][c1] * m2[c1][c2]; /* n^3*add + n^3*mul */
        }
    }
}
{% endhighlight %}
NOTE: assume the compiler does not optimize anything.
{% highlight markdown%}
Time: O(add x (2n^3+n^2+n^1) + lt x (n^3+n^2+n^1)+ mul x n^3)
{% endhighlight %}

TODO: Calculate theoretical speed
TODO: Simple case study 
- Why is this off? 
    - optimizations of the compiler
    - memory reads and writes

## Chapter 3: Validity
# What are we measuring?

TODO: Testing with pre and post conditions 
- Have these be the same when comparing versions or programs.
This is to ensure we dont compare apples with oranges.

TODO: Use Scoping
- Find a subsection of code that answers the question that has been Scoped





## SOURCES

[algorithmica: Algorithms for Modern Hardware](
https://en.algorithmica.org/hpc/)

[Ulrich Drepper: What Every Programmer Should Know About Memory](
https://people.freebsd.org/~lstewart/articles/cpumemory.pdf)

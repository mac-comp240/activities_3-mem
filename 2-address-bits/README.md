# Cache organization

There is no code for this question. It is simply an investigation into how the bits for an address get set up to access a byte in cache. Work out the numbers needed for ea
ch cache and enter them below.

Suggestion: be sure to double-check your work, since it is easy to make small mistakes that can propagate.

Work with a neighbor to compare your work on the following questions.

--------------

All caches follow this general structure as shown in your book in Figure 6.25


![Overall cache structure](.guides/img/6.25cacheorg.png)

--------------


And a full address to memory actually must have these elements to it


![Cache address elements](.guides/img/6.25physaddr.png)


Suppose that we want to determine what the address is for the following real processor, which happens to power your VM on codio. A specification can be found here:

[Intel® Xeon® Processor E5-2697 v4 Specifications](http://www.cpu-world.com/CPUs/Xeon/Intel-Xeon%20E5-2697%20v4.html)


## Main memory chip design

{Check It!|assessment}(fill-in-the-blanks-3967907410)
Determine maximum M
It is interesting to note how current processors have been designed for main memory values that are absurdly unattainable today. For this processor, the above specifications tell us:

The maximum value of M, size of main memory, is


## Some enterprise servers do have a lot of memory

Companies like Hewlitt Packard can configure servers with very large amounts of memory, such as 1024 Gigabytes (GB). To address each byte of that memory using cache-based
addresses, we need to determine what the structure of a cache address would be. For each of the questions below, begin by stating what the cache size C is, and what the nu
mber of lines per set E is. Then use those to determine S, t, s, and b.

1. For one of the the level 1 caches, per processor, what would the values for the t bits, the s bits, and the b bits be if 1024 GB of memory was installed on the machine?

{Check It!|assessment}(fill-in-the-blanks-4203207770)

Level 1 Cache address specs

For one of the the level 1 caches, per processor, what would the values for the
t bits, the s bits, and the b bits be if 1024 GB of memory was installed on a
large server-class machine?

The cache size C for a level 1 cache is KB.
The number of lines E is .
The block size B is 64 bytes.
The value for the number of sets, S, can be derived to be .
The value for t can be derived to be .
The value for s can be derived to be .
The value for b can be derived to be .


2. For the level 2 cache, what would the values for the t bits, the s bits, and the b bits be if 1024 GB of memory was installed on the machine?

Level 2 cache address specs

For the level 2 cache, determine the following, assuming the memory size is 1024
GB:

The cache size C for a level 2 cache is KB.
The number of lines E is .
The block size B is 64 bytes.
The value for the number of sets, S, can be derived to be .
The value for t can be derived to be .
The value for s can be derived to be .
The value for b can be derived to be .


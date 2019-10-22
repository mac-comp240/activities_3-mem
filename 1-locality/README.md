# Spatial and Temporal Locality

## Timing Code

You can observe the impact of poor localty by timing how long your code takes to
execute. This is a skill you should use as you work on larger projects.

You will be observing the performance of examples from your textbook,
which you will see in section 6.5:


| File          | What it does           |
| ------------- |-------------|
| sumvec.c      | 1-d array manipulation with varying degrees of good and poor locality |
| sumarrayrows.c     | 2-d matrix manipulation with good locality      |
| sumarraycols.c | 2-d matrix manipulation with poor locality        |
| sumarray3d.c | 3-d matrix manipulation with varying degrees of good and poor locality       |

We are including a helper file called `timing.h` in these C files.


### Terminology: .h files

>Files ending in .h are designed to be included in .c code files. So far, you
>have included library .h files, such as stdio.h, that are built into the
>language. In this case, we are using one as if it was written by you as a
>programmer. On many C software development teams, there are a certain core set
>of these .h files that are shared within the team for different reasons. One
>reason is that the file contains utility functions that are used routinely in a
>project. This `timing.h` file falls into this category.

We often wish to determine how long certain portions of our code take to run, so
that we can determine how efficient it is and whether certain updates we make
will improve the running time. In the file called `timing.h`, we have placed 2
functions and a typedef that can make timing of our code a bit simpler, hiding
some of the details of how to place start and stop time mechanisms around a code
segment.

In the four different examples we will explore during this activity (mentioned
above), each will include this file in this way:

    #include "timing.h"

Notice how a file we have written that is not a library .h file is included
using the double quotes instead of < and >.

The use of the timing functions is also illustrated in these four examples. The
basic concept behind using these functions is this set of steps:

1. Mark a start time just before a section of code that you want to time.
2. Execute code to be timed.
3. Retrieve the amount of time that has passed since the mark at step 1.

Observe this in the code examples described in the next 3 sections.

# One-dimensional array performance

Open the file called `sumvec.c`. This code was written to create an array of a
particular size, given as the first parameter of the program called *sumvec* on
the command line. The second parameter is the **stride** value for accessing
this array. 

Start by making and the executing *sumvec* with no command line arguments, so
that it uses the default values for array size and a stride of 1, like this:

    ./sumvec

Try running it several times. The times for each function vary because you are
sharing resources with others that are using Amazon cloud resources.

Note that the code for 2 different functions is being timed: 

1. *sumvec*, a stride-1 loop of the array. We set the default size of the array
about as large as it can be on your codio VM so that the time for *sumvec* is
near a millisecond.

2. *sumvec_stride*, which accesses the array in a different pattern from
sequential access, as long as the value of the argument called **stride** is
greater than 1. The default is for it to be 1, to establish a baseline of how
much time it takes.

## Your first task: determine the access pattern of sumvec_stride

Look carefully at the code for the function sumvec_stride. Work with your
neighbors to describe and visualize how the elements in the array are being
accessed when the stride is greater than 1.


{Submit Answer!|assessment}(free-text-2366518607)


Now change the stride by running the code like this:

    ./sumvec 1048576 4
    
Try running it several times. Observe whether the code with this stride takes
longer to run or not. Try it with larger strides, such as 8, 16, 32, and 64.


{Submit Answer!|assessment}(free-text-1555962937)


## Experiment with the timing

You can try to add code to check how long it takes to initialize the 1-d array
(in the middle of main where the loop is). This is also a stride-1 reference
pattern.


# Two-dimensional array performance

Now let's observe access patterns of 2-D arrays. We have 2 programs, each of
which statically creates a 2-dimensional array, or matrix, of M rows and N
columns. We start with M and N being equal, so that the matrix is square. The
code files are called:

    sumarrayrows.c
    sumarraycols.c
    
Each of these was made when you were working with the *sumvec* program above.

The size of the array a is set to be near the maximum size for our small codio
VM, whose memory size is 512 MB (megabytes).

Look at the .c files for each to determine the difference in the access pattern
of the matrix when determining the overall sum of the values in the array. Of
course the names of these files and the functions give you a big clue!


{Submit Answer!|assessment}(free-text-406511733)

{Submit Answer!|assessment}(free-text-931505100)


## Observe timings

Now execute *sumarrayrows* several times to determine an approximate average
time to execute the sumarrayrows function. 

execute *sumarraycols* several times to determine an approximate average time to
execute the sumarraycols function. 


{Submit Answer!|assessment}(free-text-1598901841)


## Optional: Experiment with the timing

You can try to add code to check how long it takes to initialize the 2-d array
(at the beginning of main where the nested loop is). This is row-major order
reference pattern in each case.

# Three-dimensional array performance

Now let's turn to the file called `sumarray3d.c`. I created a program called
*sumarray3d*.

The function called sumarray3d in the summarray3d.c code file should run about
as fast as possible when accessing all the lements in the 3-d array. You can try
running it a few times to see what time it takes in microseconds to access the
3-d array using the access pattern in the sumarray3d function.

## Your task: make it slower!

Now you try to complete the function sumarray3d_slower by changing the access
pattern of the array in a way that makes the locality poorer. There are a few
ways to do this- experiment with different possibilities. Add timing of your
potentially slower function to the main(). Then make and run the code a few
times to observe whether you created a slower access pattern.

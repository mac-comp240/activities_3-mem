# Similar code, Different task

This activity contains code that is similar to the code that you observed in memory activity 1. There are the following C code files:

| File          | What it does           |
| ------------- |-------------|
| sumvec.c      | 1-d array manipulation with varying degrees of good and poor locality |
| sumarrayrows.c     | 2-d matrix manipulation with good locality      |
| sumarraycols.c | 2-d matrix manipulation with poor locality        |
| sumarray3d.c | 3-d matrix manipulation with varying degrees of good and poor locality       |

Build them with make.

This time, you will be examining precisely how many cache misses are encountered when running each of these examples, with varying sizes of data arrays and stride values for accessing them.

## 1-D array

The code for sumvec.c has been updated slightly. The function called *sumvec_stride* has been improved to ensure that it has exactly the same number of data accesses and nearly equal number of instructions. In addition, in main() we have added a slightly more sophisticated way of handling the command line arguments. The possible arguments that you can include are:

    -n followed by a number for the size of the array
    -s followed by a number for the size of the stride

This enables you to execute the program like these examples:

    ./sumvec -n 1048576 -s 1
    ./sumvec -n 1048576 -s 4
    ./sumvec -n 1048576 -s 8
    ./sumvec -n 1048576 -s 16
    ./sumvec -n 1048576 -s 32

You can likely try bigger numbers for the size of the array, like this:

    ./sumvec -n 2048576 -s 4
    
### Determine actual cache misses

Now let's use a new command-line tool that has been installed in your VM in codio. It is called **valgrind**. Along with a special tool that comes with it called cachegrind, we will be able to see exactly how many cache misses our code has when it runs under different conditions.

You run valgrind with its cachegrind tool like this:

    valgrind --tool=cachegrind ./sumvec -n 1048576 -s 1

In this case, you will see what the number of cache misses is in the *D* caches, which hold the data array used in this code, for the best-case, stride-1.  What is the miss rate reported for the D1 cache?

You can also observe how many misses there are from the instructions- this is the I1 cache.

Now try running it again with various values of stride greater than 1, like this, for stride of 8:

    valgrind --tool=cachegrind ./sumvec -n 1048576 -s 8

Verify that for stride 1 and any other stride, the number of data references,D, are close to the same, but not identical (this is because the stride-1 function is still slightly different that the code for the stride function).

What do you observe about the cache miss rate as the stride increases?

### cachegrind output files

**NOTE:** each time you run valgrind with the cachegrind tool, a new file gets written out in your workspace. You will see them in the tree on the left and if you do `ls` at the terminal. These files contain more detail than we need to get into for this course (there is quite a bit of information you can find out about exactly which cache lines were used when). These files are mainly designed to be read by other programs. One of these is called **cg_annnotate**. OPTIONAL: If you want to try it you can send one of the output files as a command line argument to **cg_annotate** in the terminal.

You can remove the cachegrind output files as they pile up by using a nice feature of the command line. This will show them all to you:

    ls cache*
    
And this will remove them all:

    rm cache*


## 2-D matrix

Use valgrind with the cachegrind tool on the programs called **sumarrayrows** and **sumarraycols**.

Is the difference in data miss rate what you would have expected?

## 3-D matrix

The 3-D matrix program, called sumarray3d, has been updated from memory activity 1 to take one optional command line argument, -s. If you run it with -s like this:

    ./sumarray3d -s

You will see that it runs the slower version of the code, which has poor spatial locality. You run the faster version with good spatial locality by not including the -s flag, like this:

    ./sumarray3d
    
Once you verify that the timing is slower for the version using the -s flag, then use valgrind with the cachegrind tool (still on the command line) to run each version.

Do the reported number of cache misses indicate what you might expect, given the spatial locality of the data references?




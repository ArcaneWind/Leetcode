# 9021 Quiz 6 DFS 

## Link

## Problem Description

You are provided with a stub in which you need to insert your code where indicated without doing any changes to the existing code to complete the task. Given the value of seed and density, the provided code randomly fills an array (or grid) of size 10 x 10 with 0s and 1s. Your task is to determine the maximum number of "spikes" in a shape. A shape is made up of 1s connected horizontally or vertically (it can contain holes). A "spike" in a shape is a 1 that is part of this shape and "sticks out" (has exactly one neighbour in the shape). Neighbours are only considered vertically or horizontally (not diagonally). Note that a shape with a single 1 is also a spike. 

![image-20240410222131662](C:\Users\13399\AppData\Roaming\Typora\typora-user-images\image-20240410222131662.png)

![image-20240410222146610](C:\Users\13399\AppData\Roaming\Typora\typora-user-images\image-20240410222146610.png)

## Solution

Color different shapes with dfs.

## key Points

* dfs

## Code

``` py
# Randomly generates a grid of 0s and 1s and determines
# the maximum number of "spikes" in a shape.
# A shape is made up of 1s connected horizontally or vertically (it can contain holes).
# A "spike" in a shape is a 1 that is part of this shape and "sticks out"
# (has exactly one neighbour in the shape).
# Neighbours are only considered vertically or horizontally (not diagonally).
# Note that a shape with a single 1 is also a spike.

from random import seed, randrange
import sys


dim = 10


def display_grid():
    for row in grid:
        print('   ', *row) 


# Returns the number of shapes we have discovered and "coloured".
# We "colour" the first shape we find by replacing all the 1s
# that make it with 2. We "colour" the second shape we find by
# replacing all the 1s that make it with 3.
def colour_shapes():
    c=2
    for i in range(dim):
        for j in range(dim):
            if grid[i][j]==1:
                colour(i,j,c)
                c+=1
    return c-2
    



def max_number_of_spikes(nb_of_shapes):
    mspikes=0
    for c in range(2,nb_of_shapes+2):
        spikes=0
        for i in range(dim):
            for j in range(dim):
                if grid[i][j]==c:
                    if isSpike(i,j,c):
                        spikes+=1
        mspikes=max(mspikes,spikes)
    return mspikes


# Possibly define other functions here 
def isSpike(m,n,c):
    neighbours=0
    for x,y in [(-1,0),(1,0),(0,-1),(0,1)]:
        if 0<=m+x<dim and 0<=n+y<dim:
            if grid[m+x][n+y]==c:
                neighbours+=1
    return neighbours==1

def colour(m,n,c):
    if m<0 or m>=dim or n<0 or n>=dim:
        return
    if grid[m][n]!=1:
        return
    grid[m][n]=c
    for x,y in [(-1,0),(1,0),(0,-1),(0,1)]:
        colour(m+x,n+y,c)

try: 
    for_seed, density = (int(x) for x in input('Enter two integers, the second '
                                               'one being strictly positive: '
                                              ).split()
                    )
    if density <= 0:
        raise ValueError
except ValueError:
    print('Incorrect input, giving up.')
    sys.exit()

seed(for_seed)
grid = [[int(randrange(density) != 0) for _ in range(dim)]
            for _ in range(dim)
       ]
print('Here is the grid that has been generated:')
display_grid()
nb_of_shapes = colour_shapes()
print('The maximum number of spikes of some shape is:',
      max_number_of_spikes(nb_of_shapes)
     )
```


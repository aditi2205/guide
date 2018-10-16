---
title: Backtracking Algorithms
---

# Backtracking Algorithms

Backtracking is a general algorithm for finding all (or some) solutions to some computational problems, notably constraint satisfaction problems, that incrementally builds candidates to the solutions, and abandons each partial candidate *("backtracks")* as soon as it determines that the candidate cannot possibly be completed to a valid solution.

### Example Problem (The Knight’s tour problem)

   *The knight is placed on the first block of an empty board and, moving according to the rules of chess, must visit each square exactly once.*



 ### Path followed by Knight to cover all the cells
  Following is chessboard with 8 x 8 cells. Numbers in cells indicate move number of Knight.
  [![The knight's tour solution - by Euler](https://upload.wikimedia.org/wikipedia/commons/d/df/Knights_tour_%28Euler%29.png)](https://commons.wikimedia.org/wiki/File:Knights_tour_(Euler).png)

### Naive Algorithm for Knight’s tour
The Naive Algorithm is to generate all tours one by one and check if the generated tour satisfies the constraints.
```
while there are untried tours
{ 
   generate the next tour 
   if this tour covers all squares 
   { 
      print this path;
   }
}
```
### Backtracking Algorithm for Knight’s tour
Following is the Backtracking algorithm for Knight’s tour problem.
```
If all squares are visited 
    print the solution
Else
   a) Add one of the next moves to solution vector and recursively 
   check if this move leads to a solution. (A Knight can make maximum 
   eight moves. We choose one of the 8 moves in this step).
   b) If the move chosen in the above step doesn't lead to a solution
   then remove this move from the solution vector and try other 
   alternative moves.
   c) If none of the alternatives work then return false (Returning false 
   will remove the previously added item in recursion and if false is 
   returned by the initial call of recursion then "no solution exists" )
```
### Example Problem (The N Queen problem)
The N Queen is the problem of placing N chess queens on an N×N chessboard so that no two queens attack each other. For example, following is a solution for 4 Queen problem.
https://cdncontribute.geeksforgeeks.org/wp-content/uploads/N_Queen_Problem.jpg


The expected output is a binary matrix which has 1s for the blocks where queens are placed. For example, following is the output matrix for above 4 queen solution.

              { 0,  1,  0,  0}
              { 0,  0,  0,  1}
              { 1,  0,  0,  0}
              { 0,  0,  1,  0}


Naive Algorithm
Generate all possible configurations of queens on board and print a configuration that satisfies the given constraints.

while there are untried configurations
{
   generate the next configuration
   if queens don't attack in this configuration then
   {
      print this configuration;
   }
}
Backtracking Algorithm
The idea is to place queens one by one in different columns, starting from the leftmost column. When we place a queen in a column, we check for clashes with already placed queens. In the current column, if we find a row for which there is no clash, we mark this row and column as part of the solution. If we do not find such a row due to clashes then we backtrack and return false.

1) Start in the leftmost column
2) If all queens are placed
    return true
3) Try all rows in the current column.  Do following for every tried row.
    a) If the queen can be placed safely in this row then mark this [row, 
        column] as part of the solution and recursively check if placing queen here leads to a solution.
    b) If placing the queen in [row, column] leads to a solution then return 
        true.
    c) If placing queen doesn't lead to a solution then umark this [row, 
        column] (Backtrack) and go to step (a) to try other rows.
3) If all rows have been tried and nothing worked, return false to trigger 
    backtracking.



### More Information

[Wikipedia](https://en.wikipedia.org/wiki/Backtracking)

[Geeks 4 Geeks](http://www.geeksforgeeks.org/backtracking-set-1-the-knights-tour-problem/)

[A very interesting introduction to backtracking](https://www.hackerearth.com/practice/basic-programming/recursion/recursion-and-backtracking/tutorial/)

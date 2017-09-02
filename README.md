# Sudoku Solver

The aim of this project is to learn the basic techniques in Artificial Intelligence like Search and Constraint Propagation by creating a program to solve a Sudoku problem. The basic version uses a simple search model to remove duplicated entries. A better version (the one here) uses the concepts of constraint propagation to generate better heuristics to solve a wider variety of problems.

### Use constraint propagation to solve the naked twins problem
The "naked twins" contraint says that if two cells in one unit both contain the same two values
then those two values cannot be in any other cell in that unit. 
By searching each unit for naked-twins and then removing those digits from all the peers in the
unit we can further reduce the search space get to the solution faster.
The constraint is that if a unit contains a pair of boxes with two identical numbers 
then no other box in that unit can contain either of those two numbers. We thus try to find
all boxes with two numbers, then for each of them, search within it's peers to find another
box with matching values. If one is found then a naked twin pair has been located. 
We now have a collection of common set of peers for the twins. 
For each of these, remove any of the two digits that are in the naked twins.

[Reference](http://www.sudokudragon.com/sudokustrategy.htm#XL2104)

### Use constraint propagation to solve the diagonal sudoku problem 
The only difference from the usual sudoku problem is that the constraint is propagated to diagonals of the
puzzle as well while it was only propagated to horizontal, vertical and 3x3 boxes eariler. 
To implement this constraint extension, we add the two diagonals in the units list
so that all the constrain propagation functions we already implemented also apply to those diagonal units.
Once the digonals are added to the units and peers collections, the regular algorithms eliminate,
one_choice and naked_twins will work as usual.

### Install

This project requires **Python 3**.

Recommended to install [Anaconda](https://www.continuum.io/downloads), a pre-packaged Python distribution that contains all of the necessary libraries and software for this project. 

##### Optional: Pygame

Optionally, you can also install pygame if you want to see your visualization. If you've setup up your conda environment, you should be all set.

If not, please see how to download pygame [here](http://www.pygame.org/download.shtml).

### Visualizing

To visualize your solution, please only assign values to the values_dict using the `assign_value` function provided in solution.py

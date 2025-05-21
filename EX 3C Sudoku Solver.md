# EX 3C Sudoku Solver
## DATE:
## AIM:
To Write a python program to implement sudoku solver using backtracking to find the the safe position in the grid.

## Algorithm
1. Find the next unassigned cell (a 0).
2. Try placing numbers 1-9 in that cell.
3. Check if safe to place the number (row, column, and 3x3 box).
4. Recursively solve the rest of the puzzle from the new state, backtracking if a path fails.
5. Print the solved Sudoku or "No solution".
  
## Program:
### Developed by: NARASIMHAN S 
### Register Number: 212223230133 

```
SIZE = 9
matrix = [
    [6,5,0,8,7,3,0,9,0],
    [0,0,3,2,5,0,0,0,8],
    [9,8,0,1,0,4,3,5,7],
    [1,0,5,0,0,0,0,0,0],
    [4,0,0,0,0,0,0,0,2],
    [0,0,0,0,0,0,5,0,3],
    [5,7,8,3,0,1,0,2,6],
    [2,0,0,0,4,8,9,0,0],
    [0,9,0,6,2,5,0,8,1]]
def print_sudoku():
    for i in matrix:
        print (i)
def number_unassigned(row, col):
    num_unassign = 0
    for i in range(0,SIZE):
        for j in range (0,SIZE):
            if matrix[i][j] == 0:
                row = i
                col = j
                num_unassign = 1
                a = [row, col, num_unassign]
                return a
    a = [-1, -1, num_unassign]
    return a
def is_safe(n, r, c):
    
    for i in range(0, SIZE):
        if matrix[r][i] == n:
            return False
    for i in range(0, SIZE):
        if matrix[i][c] == n:
            return False
    row_start, col_start = r - r % 3, c - c % 3
    for i in range(0, 3):
        for j in range(0, 3):
            if matrix[row_start + i][col_start + j] == n:
                return False
    return True
def solve_sudoku():
    row = 0
    col = 0
    a = number_unassigned(row, col)
    if a[2] == 0:
        return True
    row = a[0]
    col = a[1]
    for i in range(1,10):
        if is_safe(i, row, col):
            matrix[row][col] = i
            if solve_sudoku():
                return True
            matrix[row][col]=0
    return False

if solve_sudoku():
    print_sudoku()
else:
    print("No solution")
```

## Output:

![image](https://github.com/user-attachments/assets/3f48503a-c27e-465b-b53d-265d15b92095)

## Result:
The Sudoku solver program executed successfully and found the solution for the given puzzle.

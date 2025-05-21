# EX 3A Knight Tour & Count Path
## DATE:
## AIM:
To write a python program to implement knight tour problem using backtracking.

## Algorithm
1. Initialize the board and knight's possible moves.
2. Recursively explore possible knight moves, marking visited squares.
3. Check safety of each move (within board, not visited).
4. Backtrack if a path doesn't lead to a solution.
5. Print the final tour or indicate no solution.

## Program:
### Developed by: NARASIMHAN S
### Register Number: 212223230133 

```
BOARD_SIZE = int(input())
board = [[0 for i in range(BOARD_SIZE)] for j in range(BOARD_SIZE)]    
STEPS = [[-1, 2], [1, 2], [-2, 1], [2, 1], [1, -2], [-1, -2], [2, -1], [-2, -1]]
 
def solve_knights_tour(x, y, step_count):
    if step_count == BOARD_SIZE ** 2 + 1:
        return True
    
    for step in STEPS:
        next_x = x + step[0]
        next_y = y + step[1]
        if is_safe(next_x, next_y):
            board[next_x][next_y] = step_count
            if solve_knights_tour(next_x, next_y, step_count + 1):
                return True
            board[next_x][next_y] = 0  
    return False
def is_safe(x, y):
    return 0 <= x < BOARD_SIZE and 0 <= y < BOARD_SIZE and board[x][y] == 0
 
def print_solution():
    for row in board:
        for col in row:
            print("0" + str(col) if col < 10 else col, end=" ")
        print()
 
board[0][0] = 1     
 
if solve_knights_tour(0, 0, 2):
    print("Found a solution")
    print_solution()
else:
    print("Could not find a solution")
```
## Output:

![image](https://github.com/user-attachments/assets/6ceacba3-68f4-46a7-9961-8cd486552076)

## Result:
The program executed successfully, and implement knight tour problem using backtracking was calculated.

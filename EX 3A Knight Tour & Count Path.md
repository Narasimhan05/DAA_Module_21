# EX 3A Knight Tour & Count Path
## DATE:
## AIM:
To Write a python program to implement knight tour problem using backtracking

## Algorithm
1. Initialize the Board: Sets up an empty chessboard of a user-defined size and defines the possible knight moves.
2. Start the Tour (Backtracking): Places the knight at (0,0) and attempts to find a path to visit every square exactly once using a recursive backtracking approach.
3. Check for Valid Moves: For each potential knight move, it verifies if the new position is within the board boundaries and hasn't been visited yet.
4. Mark and Recurse: If a move is valid, the square is marked with the current step number, and the function recursively calls itself for the next move.
5. Print Solution or Failure: If a complete tour is found (all squares visited), it prints the numbered board; otherwise, it indicates that no solution exists.  

## Program:
Developed by: NARASIMHAN S
Register Number: 212223230133 
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

![image](https://github.com/user-attachments/assets/ea57c317-11c8-4f1b-82bb-a214f3536b41)

## Result:
The program executed successfully, and the minimum number of steps for the knight to reach the target was calculated.

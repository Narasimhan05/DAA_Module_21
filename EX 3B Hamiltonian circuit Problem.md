# EX 3B Hamiltonian Circuit Problem
## DATE:
## AIM:
To Create a python program to implement Hamiltonian circuit problem using Backtracking.

## Algorithm
1. Initialize a graph and a path array for tracking visited vertices.
2. Recursively try to extend the current path to form a cycle.
3. Check if safe to add a vertex: connected to the previous, and not already in path.
4. Backtrack if a path doesn't lead to a complete Hamiltonian Cycle.
5. Print the found Hamiltonian Cycle or state that none exists.  

## Program:
### Developed by: NARASIMHAN S
### Register Number: 2122223230133 

```
class Graph():
    def __init__(self, vertices):
        self.graph = [[0 for column in range(vertices)]
                            for row in range(vertices)]
        self.V = vertices

    def isSafe(self, v, pos, path):
        if self.graph[ path[pos-1] ][v] == 0:
            return False
        for vertex in path:
            if vertex == v:
                return False
        return True

    def hamCycleUtil(self, path, pos):
        if pos == self.V:
            if self.graph[path[pos - 1]][path[0]] == 1:
                return True
            else:
                return False
        for v in range(1, self.V):
            if self.isSafe(v, pos, path):
                path[pos] = v
                if self.hamCycleUtil(path, pos + 1):
                    return True
                path[pos] = -1
 
    def hamCycle(self):
        path = [-1] * self.V
        path[0] = 0
        if self.hamCycleUtil(path,1) == False:
            print ("Solution does not exist\n")
            return False
        self.printSolution(path)
        return True
 
    def printSolution(self, path):
        print ("Solution Exists: Following",
                 "is one Hamiltonian Cycle")
        for vertex in path:
            print (vertex, end = " ")
        print (path[0], "\n")
g1 = Graph(5)
g1.graph = [ [0, 1, 0, 1, 0], [1, 0, 1, 1, 1],
            [0, 1, 0, 0, 1,],[1, 1, 0, 0, 1],
            [0, 1, 1, 1, 0], ]
g1.hamCycle();
```
## Output:

![image](https://github.com/user-attachments/assets/dc942ea5-8069-4301-9f2c-5ffeb2278c09)

## Result:
The Hamiltonian path program executed successfully, and it determined whether aHamiltonian circuit problem using Backtracking.

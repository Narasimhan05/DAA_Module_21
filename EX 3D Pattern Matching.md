# EX 3D Pattern Matching
## DATE:
## AIM:
To Write a Python program for Bad Character Heuristic of Boyer Moore String Matching Algorithm.

## Algorithm
1. Preprocess the pattern to create a "bad character" shift table.
2. Align the pattern with the beginning of the text.
3. Compare the pattern with the text from right to left.
4. Shift the pattern based on the bad character rule or full match.
5. Repeat until the pattern is found or the end of the text is reached.  

## Program:
### Developed by: NARASIMHAN S 
### Register Number: 212223230133 
```
NO_OF_CHARS = 256
def badCharHeuristic(string, size):
    badChar = [-1] * NO_OF_CHARS
    for i in range(size):
        badChar[ord(string[i])] = i
    return badChar
def search(txt, pat):
    m = len(pat)
    n = len(txt)
    badChar = badCharHeuristic(pat, m)
    s = 0
    while(s <= n-m):
        j = m-1
        while j>=0 and pat[j] == txt[s+j]:
            j -= 1
        if j<0:
            print("Pattern occur at shift = {}".format(s))
            s += (m-badChar[ord(txt[s+m])] if s+m<n else 1)
        else:
            s += max(1, j-badChar[ord(txt[s+j])])
def main():
    txt = input()                     
    pat = input()                      
    search(txt, pat)
 
if __name__ == '__main__':
    main()
```
## Output:

![image](https://github.com/user-attachments/assets/0246cdb6-b54c-41f2-bbf6-db0cb1b724a9)

## Result:
The Bad Character Heuristic of Boyer Moore String Matching Algorithm executed successfully and returned the starting index of the match or 0 if no match was found.

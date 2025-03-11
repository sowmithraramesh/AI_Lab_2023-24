# Ex.No: 4   Implementation of Alpha Beta Pruning 
### DATE:                                                                            
### REGISTER NUMBER : 
### AIM: 
Write a Alpha beta pruning algorithm to find the optimal value of MAX Player from the given graph.
### Steps:
1. Start the program
2. Initially  assign MAX and MIN value as 1000 and -1000.
3.  Define the minimax function  using alpha beta pruning
4.  If maximum depth is reached then return the score value of leaf node. [depth taken as 3]
5.  In Max player turn, assign the alpha value by finding the maximum value by calling the minmax function recursively.
6.  In Min player turn, assign beta value by finding the minimum value by calling the minmax function recursively.
7.  Specify the score value of leaf nodes and Call the minimax function.
8.  Print the best value of Max player.
9.  Stop the program. 

### Program:
```
def minimax(depth, index, is_max, values, alpha, beta):
    if depth == 3:
        return values[index]

    func = max if is_max else min
    best = float('-inf') if is_max else float('inf')

    for i in range(2):
        val = minimax(depth + 1, index * 2 + i, not is_max, values, alpha, beta)
        best = func(best, val)

        if is_max:
            alpha = max(alpha, best)
        else:
            beta = min(beta, best)

        if beta <= alpha:  # Alpha-Beta Pruning Condition
            break

    return best

# Test case
values = [3, 5, 6, 9, 1, 2, 0, -1]
print("The optimal value is:", minimax(0, 0, True, values, float('-inf'), float('inf')))
```

### Output:
![image](https://github.com/user-attachments/assets/f6a0bcb6-f68a-4cb9-8483-19c4f39dae98)



### Result:
Thus the best score of max player was found using Alpha Beta Pruning.

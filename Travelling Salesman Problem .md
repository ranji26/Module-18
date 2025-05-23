# Ex. No: 18D - Travelling Salesman Problem (TSP)

## AIM:
To write a Python program to find the shortest possible route that visits every city exactly once and returns to the starting point using the **Travelling Salesman Problem (TSP)** approach.

## ALGORITHM:

**Step 1**: Start the program.

**Step 2**: Input the number of cities and the distance matrix.

**Step 3**: Set the starting city (e.g., city `0`).

**Step 4**: Generate all possible permutations of the remaining cities.

**Step 5**: For each permutation:
- Calculate the total cost of traveling through the permutation starting and ending at city `0`.
- Keep track of the **minimum cost** and the corresponding route.

**Step 6**: Return the **route** and the **minimum cost**.

**Step 7**: End the program.

## PYTHON PROGRAM

```
from itertools import permutations

def tsp_brute_force(distance_matrix):
    num_cities = len(distance_matrix)
    cities = list(range(num_cities))
    start = 0
    min_cost = float('inf')
    best_route = []

    for perm in permutations(cities):
        if perm[0] != start:
            continue

        current_cost = 0
        for i in range(num_cities - 1):
            current_cost += distance_matrix[perm[i]][perm[i + 1]]
        current_cost += distance_matrix[perm[-1]][perm[0]]

        if current_cost < min_cost:
            min_cost = current_cost
            best_route = perm

    return best_route + (best_route[0],), min_cost

distance_matrix = [
    [0, 10, 15, 20],
    [10, 0, 35, 25],
    [15, 35, 0, 30],
    [20, 25, 30, 0]
]

route, cost = tsp_brute_force(distance_matrix)
print("Optimal Route:", route)
print("Minimum Cost:", cost)
```

## OUTPUT
![image](https://github.com/user-attachments/assets/5faf94e5-f03e-4619-a9f8-39df8b4b3df6)


##RESULT
Thus, the Python program to solve the Travelling Salesman Problem using brute-force method was successfully executed and the shortest route was determined.

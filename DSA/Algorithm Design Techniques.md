# Algorithm Design Techniques

## Brute Force Algorithms

Brute force algorithms consider all possible solutions, one by one, and select the optimal solution. Also known as exhaustive search method.

For example, the time complexity for the Traveling Salesman Problem using brute force is O(n!), and for the Knapsack Problem, it’s O(2^n).

### Pros:
- straightforward, usually follows the problem definition
- might be suitable only for smaller inputs
- The brute force approach is a guaranteed way to find the correct solution by listing all the possible candidate solutions for the problem.
- It is a generic method and not limited to any specific domain of problems.
- The brute force method is ideal for solving small and simpler problems.
- It is known for its simplicity and can serve as a comparison benchmark.

### Cons:
- rarely the efficient approach
- The brute force approach is inefficient. For real-time problems, algorithm analysis often goes above the O(N!) order of growth.
- This method relies more on compromising the power of a computer system for solving a problem than on a good algorithm design.
- Brute force algorithms are slow.
- Brute force algorithms are not constructive or creative compared to algorithms that are constructed using some other design paradigms.

## Dynamic Programming

Dynamic Programming is a method used in mathematics and computer science to solve complex problems by breaking them down into simpler subproblems. By solving each subproblem only once and storing the results, it avoids redundant computations, leading to more efficient solutions for a wide range of problems.

### How Does Dynamic Programming (DP) Work?

If the subproblems share resources and are not independent, then dynamic programming may not provide the correct solution.

Dynamic programming can be achieved using two approaches:

### 1. Top-Down Approach (Memorization):

In the top-down approach, also known as memorization, we start with the final solution and recursively break it down into smaller subproblems. To avoid redundant calculations, we store the results of solved subproblems in a memoization table.

#### Let’s breakdown Top down approach:
1. Identify Subproblems: Divide the main problem into smaller, independent subproblems.
2. Store Solutions: Solve each subproblem and store the solution in a table or array.
3. Build Up Solutions: Use the stored solutions to build up the solution to the main problem.
4. Avoid Redundancy: By storing solutions, DP ensures that each subproblem is solved only once, reducing computation time.

Starts with the final solution and recursively breaks it down into smaller subproblems.

Memorization is typically implemented using recursion and is well-suited for problems that have a relatively small set of inputs.

### 2. Bottom-Up Approach (Tabulation):

In the bottom-up approach, also known as tabulation, we start with the smallest subproblems and gradually build up to the final solution. We store the results of solved subproblems in a table to avoid redundant calculations.

#### Let’s breakdown Bottom-up approach:
- Tabulation is typically implemented using iteration and is well-suited for problems that have a large set of inputs.
- Stores the solutions to subproblems in a table to avoid redundant calculations.
- Suitable when the number of subproblems is large and many of them are reused.
- Starts with the smallest subproblems and gradually builds up to the final solution.
- Fills a table with solutions to subproblems in a bottom-up manner.
- Suitable when the number of subproblems is small and the optimal solution can be directly computed from the solutions to smaller subproblems.

### Comparison of Memorization and Tabulation

| Feature             | Memorization                                                 | Tabulation                                                   |
| ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Approach            | Top-down                                                     | Bottom-up                                                    |
| Implementation      | Recursive                                                    | Iterative                                                    |
| Storage             | Caches the results of function calls                         | Stores the results of subproblems in a table                 |
| Problem Suitability | Well-suited for problems with a relatively small set of inputs | Well-suited for problems with a large set of inputs          |
| Usage               | Used when the subproblems have overlapping subproblems       | Used when the subproblems do not overlap                     |
| Overhead            | Can have additional overhead due to the cost of recursion, such as the cost of function call stack maintenance. | Overhead does not exist in this method which uses iteration. |
| Time complexity     | Same because they solve the same number of subproblems.      | Same because they solve the same number of subproblems.      |
| State               | State transition relation is easy to think                   | State transition relation is difficult to think              |
| Code                | Code is easy and less complicated                            | Code gets complicated when a lot of conditions are required  |
| Speed               | Slow due to a lot of recursive calls and return statements   | Fast, as we directly access previous states from the table   |
| Subproblem solving  | If some subproblems in the subproblem space need not be solved at all, the memoized solution has the advantage of solving only those subproblems that are definitely required | If all subproblems must be solved at least once, a bottom-up dynamic-programming algorithm usually outperforms a top-down memoized algorithm by a constant factor |
| Table Entries       | In Memorized version, all entries of the lookup table are not necessarily filled. The table is filled on demand. | In Tabulated version, starting from the first entry, all entries are filled one by one |

### Memorization implementation of Fib(n):

```cpp
#include <iostream>
#include <unordered_map>

int fibonacci(int n, std::unordered_map<int, int>& cache) {
    if (cache.find(n) != cache.end()) {
        return cache[n];
    }
    int result;
    if (n == 0) {
        result = 0;
    } else if (n == 1) {
        result = 1;
    } else {
        result = fibonacci(n-1, cache) + fibonacci(n-2, cache);
    }
    cache[n] = result;
    return result;
}
```

### Tabulation implementation of Fib(n):

```cpp
#include <iostream>
#include <vector>

int fibonacci(int n) {
    if (n == 0) {
        return 0;
    } else if (n == 1) {
        return 1;
    } else {
        std::vector<int> table(n + 1, 0);
        table[0] = 0;
        table[1] = 1;
        for (int i = 2; i <= n; i++) {
            table[i] = table[i - 1] + table[i - 2];
        }
        return table[n];
    }
}
```

## Greedy Algorithms

A greedy algorithm is a type of optimization algorithm that makes locally optimal choices at each step with the goal of finding a globally optimal solution. It operates on the principle of “taking the best option now” without considering the long-term consequences.

### Steps for Creating a Greedy Algorithm:
1. Define the problem: Clearly state the problem to be solved and the objective to be optimized.
2. Identify the greedy choice: Determine the locally optimal choice at each step based on the current state.
3. Make the greedy choice: Select the greedy choice and update the current state.
4. Repeat: Continue making greedy choices until a solution is reached.

### Standard Greedy Algorithms:
- Prim’s Algorithm
- Kruskal’s Algorithm
- Dijkstra’s Algorithm

### Properties of problems that can be solved using Greedy Approach:
- Optimal substructure property.
- Minimization or Maximization of quantity is required.
- Ordered data is available such as data on increasing profit, decreasing cost, etc.
- Non-overlapping subproblems.

### Applications of Greedy Approach:
Greedy algorithms are used to find an optimal or near optimal solution to many real-life problems. Few of them are listed below:
1. Make a change problem
2. Knapsack problem/Knapsack with fractions
3. Minimum spanning tree
4. Single source shortest path
5. Activity selection problem 
6. Job sequencing problem
7. Huffman code generation.
8. Job scheduling
9. Interval scheduling
10. Greedy set cover

### Comparison of Greedy Algorithms and Dynamic Programming

| Feature         | Greedy Algorithm                                             | Dynamic Programming                                          |
| --------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Approach        | Makes the locally optimal choice at each stage with the hope of finding a global optimum. | Breaks down the problem into smaller subproblems and solves each subproblem once, storing the solutions in a table to avoid redundant computations. |
| Optimality      | May not always guarantee an optimal solution, as it makes decisions based on local optimality. | Guarantees an optimal solution by considering all possible cases. |
| Recursion       | Follows a problem-solving heuristic of making the locally optimal choice at each stage. | Usually based on a recurrent formula that uses previously calculated states. |
| Memorization    | More efficient in terms of memory as it doesn't need to store previous choices. | Requires a dynamic programming table for memoization, which increases the memory complexity. |
| Time Complexity | Generally faster, e.g., Dijkstra's algorithm has a time complexity of O(E log V + V log V). | Generally slower, e.g., Bellman-Ford algorithm has a time complexity of O(VE). |
| Computation     | Computes its solution by making its choices in a serial forward fashion, never looking back or revising previous choices. | Computes its solution bottom-up or top-down by synthesizing them from smaller optimal sub-solutions. |
| Examples        | Fractional knapsack problem.                                 | 0/1 knapsack problem.                                        |

### 0/1 Knapsack problem using different approaches

#### 1. Brute Force Algorithm:

```cpp


#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int knapSackBruteForce(int W, vector<int>& wt, vector<int>& val, int n) {
    if (n == 0 || W == 0)
        return 0;
    if (wt[n-1] > W)
        return knapSackBruteForce(W, wt, val, n-1);
    else
        return max(val[n-1] + knapSackBruteForce(W-wt[n-1], wt, val, n-1), knapSackBruteForce(W, wt, val, n-1));
}
```

#### 2. Dynamic Programming:

```cpp
#include <iostream>
#include <vector>

using namespace std;

int knapSackDP(int W, vector<int>& wt, vector<int>& val, int n) {
    vector<vector<int>> dp(n+1, vector<int>(W+1, 0));

    for (int i = 0; i <= n; i++) {
        for (int w = 0; w <= W; w++) {
            if (i == 0 || w == 0)
                dp[i][w] = 0;
            else if (wt[i-1] <= w)
                dp[i][w] = max(val[i-1] + dp[i-1][w-wt[i-1]], dp[i-1][w]);
            else
                dp[i][w] = dp[i-1][w];
        }
    }

    return dp[n][W];
}
```

#### 3. Greedy Algorithm:

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

struct Item {
    int value, weight;
    Item(int v, int w) : value(v), weight(w) {}
};

bool compare(Item a, Item b) {
    double r1 = (double)a.value / a.weight;
    double r2 = (double)b.value / b.weight;
    return r1 > r2;
}

int knapSackGreedy(int W, vector<Item>& items) {
    sort(items.begin(), items.end(), compare);
    int curWeight = 0;
    double finalValue = 0.0;

    for (int i = 0; i < items.size(); i++) {
        if (curWeight + items[i].weight <= W) {
            curWeight += items[i].weight;
            finalValue += items[i].value;
        } else {
            int remain = W - curWeight;
            finalValue += items[i].value * ((double)remain / items[i].weight);
            break;
        }
    }

    return finalValue;
}
```

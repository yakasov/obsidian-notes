##### Examples of problems
- Array sum problem - given an array of $n$ integers, return their sum
- Searching for a key - given an ordered list $L$ of $n$ integers, find a given key in it
- Sorting problem - given an array $L$ of integers, arrange $L$ in ascending order, ie for any $1 \leq i \lt j \leq n, L[i] \leq L[j]$ 
- Travelling salesperson problem - find the shortest path for a salesman to visit all cities on a given route

Developing a good solution requires designing an algorithm, and then analysing the correctness and efficiency of the algorithm.

Absolute execution time of an algorithm depends on many factors:
- the algorithm used to solve a problem
- the programming language (interpreted languages are typically slower than compiled languages)
- the quality of the actual implementation
- the machine on which the code is run
- the size of the input

### Time complexity function
When analysing the efficiency of an algorithm, we focus on the *"speed"* of the algorithm (the complexity of the algorithm) as a function of the size of the input on which it is run, where "speed" is the number of basic steps/operations in the program.

> [!faq] Example
> - summing the numbers in the array with 2 elements clearly requires fewer operations than summing 2 million elements
> - searching in a list of 2 elements requires fewer operations than searching in a list of 2 million elements

> [!info] Definition
> The *time complexity function $T(n)$* expresses the number of primitive operations (usually the addition of two numbers or their comparison is a primitive operation) which the algorithm needs to execute on an input of size $n$.

#### Worst-case time complexity
> [!info] Definition
> The algorithm has to finish in time $T(n)$ for all instances of input of size $n$ (but can finish quicker)

> [!info] Array sum algorithm example
> **Problem:** add all the $n$ integers given in the array $S$
> **Inputs:** positive integer $n$, array of numbers $S$ indexed from $1$ to $n$
> **Outputs:** sum, the sum of the integers in $S$
> 
> An example of code would be a function that uses a *for* loop to sum up to a certain index -
> $$\begin{aligned}\text{sum} := 0;  &-  \text{(initialise $t_1$)} \\ \text{for} i := 1 \text{to} n  &-  \text{(set up loop $t_2$)} \\ \text{sum} := \text{sum} + S[i]  &-  \text{(each iteration $t_3$)} \\ \text{print sum;}  &-  \text{(finalisation $t_4$)}\end{aligned}$$
> 
> **Basic operation:** the addition of an item in the array to *sum*. This is the most expensive (in time) of the operations in the routine.
> **Input size:** the size of the input is proportional to $n$, the number of items in the array.
> **Time complexity function:** the time required is dominated by the addition, which is called $n$ times. Thus, $$T(n) \approx t_1 + t_2 + t_3 \times n + t_4$$
> $T(n) = A \times n$, corresponds to $t_1 + t_2 + t_3 \times n + t_4$
> where $A$ is a suitable constant (eg how many primitive operations correspond to our operation with the array)


**Sequential search:** go through the array element by element
**Binary search:** split the array in half and see if we need to go to the higher half or lower half, repeat

### Summary
- time complexity, which describes how long an algorithm takes to solve a problem of a given input size
- how to compare different algorithms that solve the same problems
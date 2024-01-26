# 1. Computability and equivalent models
a. $Z := \max\{Y - X, 0\}$ 
Z := 0
while X > 0 do
	Y := pred(Y)
	X := pred(X)
od

if Y > 0 do
	Z := Y
od

b.
F(2)  = add(2, F(1))
	= add(2, add(2, 0))
	= add(2, 2)
	= succ(add(2, 1))
	= succ(succ(add(2, 0)))
	= succ(succ(2))
	= succ(3)
	= 4

c.
i.
baaabaaabaaa
$\rightarrow$ aaaaaa
$\rightarrow$ a$^{\{i + j + k - 3\}}$

ii.
any string with an equal number of a's as b's will return $\lambda$ 

d.
YES - there exists a function that can be computed by a Turing machine but is not primitive recursive. The Ackermann function, for example, is computable but not primitive recursive as it displays extremely fast growth, faster than any primitive recursive function, but can still be computed by a Turing machine as a Turing machine can simulate the nested recursion that the function requires.

e.
three computational models that are equivalent to Turing machines may include:
- $\lambda$-calculus
- Markov algorithms
- Post algorithms
They are all equal in terms of computational power. In classical computer science, there does not exist a model more powerful than a Turing machine.

# 2. Decidable and undecidable problems
a. 
the Halting problem is undecidable - there does not exist an algorithm for determining whether the answer will be YES or NO. Without a given number of steps to wait and see if the program halts, there is no way to know for certain if a given program will eventually halt, or continue forever.

b.
the problem cannot be solved by increasing the maximum amount of resources for computation - the amount of resources has no effect on the outcome of an undecidable problem.

c.
i.
the set of all strings over the alphabet $\{a, b, c\}$ of length 10 is countable - the set size is $3^{10}$.

ii.
the set $S$ of all languages over the alphabet $\{a, b, c\}$ with the following property: each language from $S$ contains only strings of length ten is countable - only a finite amount of languages can be formed from the alphabet, and each set of all strings in that language has a finite size.

d. $\{(11, 1), (0111, 10), (10, 0), (1, 111)\}$
The pairs (11,1), (10, 0), (1, 111) can potentially be combined - the top and bottom halves have the same amount of 1s and 0s.

Indeed, we can arrange them as such - (1, 111), (11, 1), (10, 0), which gives us 1 - 11 - 10 on the top, and 111 - 1 - 0 on the bottom, both equalling 11110.

e. $A = \{a, b, c, d\}$, each string is length $n, n \geq 5$  
i. for $m = 4$,
every string in $A$ is of length 5 or above, so any string of length 4 will not be in the list.

ii. for $m = n$,
we can use diagonalisation to create a new string from a subset of strings from $A$ provided they are all of the same length. If this subset is ordered, then we can diagonally create a new string. This guarantees a new string not already in the list.

iii. for $m = 2n$,
since the length of each string is $n$, no string will be of length $2n$ - thus we can easily generate a string of $m$ length without it already being in the list

# 4. Computational complexity
a.
i. constant time complexity
NO - as $n$ increases, the solve time will also increase for any sorting algorithm

ii. linear time complexity $O(n)$ 
NO - there is no polynomial sorting algorithm, the fastest being $n\log{n}$ 

iii. time complexity $O(n^2)$ 
YES - for example bubble sort is $O(n^2)$ 

b. sorted list $A$ of 100 different integers
binary search
128 - 64 - 32 - 16 - 8 - 4 - 2 
1 - 2 - 3 - 4 - 5 - 6 - 7
Or $O(\log{n}): \log(100) = 6.64$ 
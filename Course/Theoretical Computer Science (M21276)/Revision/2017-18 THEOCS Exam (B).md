# 1. Computability and equivalent models
a.
i. $X := X + Y$ 
while Y > 0 do
	X := succ(X)
	Y := pred(Y)
od

ii. $Z := X * Y$
while Y > 0 do
	temp := X
	while temp > 0 do
		Z := succ(Z)
		temp := pred(temp)
	od
	Y := pred(Y)
od

b.
i. $a^iba^jba^k$ 
if i = j = k, then output is $\lambda$ 
if i - j > k, then output is $a^{i - j- k}$
else, output is $a^{k - (i - j)}$

ii. if rules two and three are swapped
then the output is different ()

c.
i.
$\text{zero}: \mathbb{N} \rightarrow \mathbb{N}, \text{zero}(x) = 0$
$\text{succ}(x) = x + 1$
$\text{project}_i: \mathbb{N}^k \rightarrow \mathbb{N}$

ii.
a Turing machine can compute any primitive recursive function - these functions can only do finite loops and therefore always terminate

d. $XaY \rightarrow XccY$
i.
for any symbol $a$ in the input string, if the symbol is surrounded by two different symbols, it is changed to $cc$
therefore $abccaab \rightarrow abccccab \rightarrow abccccccb$ 

ii. 
the output will be different as the instruction will only be ran once, so the output will be $abccccab$ 


# 2. Decidable and undecidable problems 
a.
list $D$ contains $k$
$k$ is the amount of finite strings in $D$ 
the length of each string is at most $k, k \geq 1$ 

if we assume that the list $D$ contains all possible strings of length $k$, we can arrange them alphabetically. We can then construct a new string looking at character $i$ from string of index $i$ - if the character is $a$, we change it to a $b$, and if it is not an $a$, then we change it to an $a$. The resulting string is of length $k$, and as a result of its construction method, it differs from every string in $D$ by at least one position, so it cannot be in $D$. This also shows that the set of all strings of length $k$ over this alphabet is uncountable.

b.
since $L$ is over a finite alphabet, there will always exist a Turing machine that can recognise $L$ due to the amount of combinations that can be understood

c.
i.
the Post Correspondence Problem is an undecidable problem.
Given a finite set of dominos, where each domino has a top string $s$ and a bottom string $t$ (both over an alphabet), can we determine if there exists a sequence of these dominos such that the concatenation of the top strings is equal to the concatenation of the bottom strings?

It is possible to design an algorithm that returns YES for all instances for which a solution exists - if the solution exists, we can enumerate all possible sequences until we find one that works. 

It is not possible to design an algorithm that returns YES for all instances in a finite amount of time, as the problem is undecidable.

ii. {(aabb, bcaa), (aabbbb, aab), (acba, abab), (adba, aab), (bb, b)}
The first domino starts with 'aa' on $s$ and 'bc' on $t$ - no other domino ends with 'bc' on top, so the first domino cannot be the first in any sequence.
The second domino starts with 'aa' on $s$ and 'aa' on $t$ - no other domino ends with 'bb' on top, so the second domino cannot be first in any sequence.
The third domino starts with 'ac' on $s$ and 'ab' on $t$ - no other domino ends with 'ab' on top, so the third domino cannot be first in any sequence.
The fourth domino starts with 'ad' on $s$ and 'aa' on $t$ - no other domino ends with 'ab' on top, so the fourth domino cannot be first in any sequence.
The fifth domino starts with 'bb' on $s$, and 'b' on $t$ - no other domino ends with 'b' on top, so the fifth domino cannot be first in any sequence.

Since no domino can be first in the sequence, there does not exist a solution for this instance of PCP.

d.
i.
A set is countable if it is finite or countably infinite, meaning we can construct a numbered list of all its elements.

Two disjoint countable sets may be the set of all odd numbers, and the set of all even numbers. They can both be counted as each number in the set can be corresponded to the set of natural numbers:
- all odds numbers <-> all natural numbers = 2n + 1
- all even numbers <-> all natural numbers = 2n

ii.
Three disjoint uncountable sets may be:
- the set of all real numbers between 1 and 2;
- the set of all real numbers between 3 and 4;
- the set of all real numbers between 5 and 6;

# 3. Time complexity
a. $T(n) = An^4 + Bn^2\log_2n$ 

$O(...)$ is the asymptotic upper bound
$\Omega(...)$ is the asymptotic lower bound
$\Theta(...)$ is the asymptotic tight bound

i. $T(n) = \Theta(n^4)$ is TRUE - time complexity is both upper and lower bounded by $n^4$ 
ii. $T(n) = \Omega(2^n)$ is FALSE - $\Omega$ describes a lower bound, and $2^n$ grows much faster than either $n^4$ or $n^2\log_2n$ 
iii. $T(n) = O(n^4)$ is TRUE - O describes an upper bound, and time complexity is upper bounded by $n^4$ 
iv. $T(n) = \Theta(n^2\log_2n)$ is FALSE - $\Theta$ describes an upper *and* lower, and $n^2\log_2n$ is not the most dominant term as $n$ increases
v. $T(n) = O(n^3)$ is FALSE - O describes an upper bound, and $n^4 \gt n^3$ 

b.
$T(n) = A \times 2^n$, $n = 10 \rightarrow T(n) = 1\times{}10^{-2}$ 
$1 \times 10^{-2} = A \times 1 \times 10^3$ 
$\frac{1 \times 10^{-2}}{1 \times 10^3} = A = 1 \times 10^{-5}$ 

i. 
$T(n) = (1 \times 10^{-5}) \times 2^{20}$ 
$2^{10} \approx 10^3 \implies 2^{20} \approx 10^6 (2^{10^2} \approx 10^{3^2})$ 
$T(n) = (1 \times 10^{-5}) \times 10^6 = 10^1 = 10$ 
10 seconds

ii.
$10^7 = 10^{-5} \times 2^n$ 
$\frac{10^7}{10^{-5}} = 10^{12} = 2^n$ 
$2^{10} \approx 10^3 \implies 2^{40} \approx 10^{12} (2^{10^4} \approx 10^{3^4})$ 
$n = 40$ 

iii.
Intractable - the lower bound is $2^n$, making it exponential

c.
i.
12 times - first loop then 3 increments after (3x3)
$T(n) = n^2$ 

ii.
$\Theta(n)$ is not the asymptotically tight bound for $T(n)$ as the algorithm given is $\Theta(n^2)$.

iii.
The algorithm is now $n(3n + 1)$ which simplifies to $n^2$, so the tight bound $\Theta$ is the same as before ($\Theta({n^2})$)

d.
i.
There is no function that fits between these bounds - an example might be $n^5$ 

ii.
The fastest growth rate is $\frac{n!}{20^{10}}$ 

# 4. Computational complexity
a.
i. searching for a minimum in an unordered array of integers
this problem is tractable and can be solved in polynomial time - $n$ time is required for $n$ integers in the array

ii. the Halting problem
this problem is undecidable, as no algorithm exists to provide a YES/NO answer

iii. the decision version of the Travelling Salesman Problem
this problem is NP-complete - given a number of cities and distances, we can plan a shortest route between them, but this problem cannot be solved in polynomial time

b.
P problems can be solved in polynomial time by a Turing machine. NP-complete problems can be verified that a solution exists, but finding a solution cannot be solved in polynomial time. Most NP-complete problems are decidable, but there exist some that are not, such as the Halting problem.

c.
the lower bound is the minimum amount of resources that an algorithm requires to solve a problem, ie the best case scenario. The upper bound is the maximum amount of resources that an algorithm requires to solve a problem, ie the worst case scenario. The complexity of the problem required can be polynomial or exponential depending on the algorithm used to find a solution.

d.
if one NP-complete problem can be solved in polynomial time, then all of them can be, which would mean P = NP. This is a 10 in significance, as it would allow many problems to be solved easier, but also have implications on the world of cyber security where security relies on problems to be solved in exponential time to guarantee safety.

e.
if $\mathcal{Q}$ is NP-hard, then we can try approximating the best solution, which will allow us to find a solution that is within a known factor of the optimal solution. We can also use algorithms known not to give the best result combined with intuition to reach a solution that may be good enough.

f.
an algorithm with $T(n) = O(n^2)$ is the most appropriate - many algorithms, such as bubble sort or selection sort, are of this time complexity as they use a swapping method which involves multiple iterations through the list.
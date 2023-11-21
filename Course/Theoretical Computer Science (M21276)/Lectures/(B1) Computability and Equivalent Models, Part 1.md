### Outline
- some other models with the same power as TMs
- showing some problems cannot be solved by any computers
- figuring out how long it will take to solve problems that can be solved
- comparing two algorithms
- looking at similarities between problems; finding classes of problems that are similar to one another
- possible approaches for solving "hard" problems

Russel's set paradox comes from Georg Cantor's set theory:
	*"Let $S$ be the set of all sets that are not members of themselves. But how about the set $S$?"*
	$S = \{x \: | \: x \notin x\},$ then $S \in S \Leftrightarrow S \notin S$ 

From Russel's set paradox comes Hilbert's program:
- a formalisation of all mathematics: all mathematical statement should be written in a precise formal language and manipulated according to well defined rules
	- we start with a set of axioms and precisely define rules for logical inference and deduction
	- a proposition is considered proven true if we can derive it from the axioms in a finite sequence of logical steps
- completeness: any proposition expressible in the system can be proved to be true or false 
- decidability: there should be “an algorithm” (mechanically verifiable proofs) for deciding the truth or falsity of any mathematical statement

#### Computability
A thing is computable:
- if there is some computation that computes it
- if it can be described by an algorithm

So, a computation is an execution of an algorithm. "Computable" has something to do with a formal process (execution) and a formal description (algorithm).

> [!faq] Examples
> Some examples of formal processes and formal descriptions connected with our intuitive notion of computable:
> - the derivation process associated with grammars
> - the evaluation process associated with functions
> - the state transition process associated with machines
> - the execution process associated with programs and programming languages
> 
> A model is a formalisation of an idea. So, we have several ways to model the idea of computability.

##### Computation Models
> [!info] Church-Turing Thesis
> Anything that is intuitively computable can be computed by a Turing machine.

On one hand, we have only informal ideas of what being computable means. On the other hand, the idea of a Turing machine is formal and precise.

Because of this, there is no possibility of ever proving that everyone's idea of computability is equivalent to the formal idea of a Turing machine.

Several attempts were made in the first half of the 20th century to formalise the notion of computability:
- **Alonzo Church:** created a method for defining functions called the $\lambda$-calculus
- **Alan Turing:** created a theoretical model for a machine that could carry out calculations from inputs
- **Church + Stephen Kleene + J.B. Rosser:** created a formal definition of a class of functions whose values could be calculated by recursion (partial recursive functions)
These computation models may process different kinds of data but they can still be compared with respect to how they process natural numbers.

#### Model 1: $\lambda$-calculus

blah blah fill in

#### Model 2: Simple programming language

The simple language is a little imperative language introduced by **Stepherdson** and **Sturgis** in 1963.

This language has the same power as a Turing machine, meaning:
- any problem that can be solved by a TM can be solved with a simple program
- any problem that can be solved by a simple program can be solved by a TM

An informal description:
1. there are variables that take values in the set $\mathbb{N}$ in the set of natural numbers
2. there is a while statement of the form
	   while $X \neq 0$ do statement od.
3. there is an assignment statement taking one of the three forms:
	   $X := 0$, $X: = \text{succ}(Y)$, $X := \text{pred}(Y)$ 
4. a statement is either:
   - a while statement
   - an assignment statement
   - a sequence of two or more statement separated by semicolons
5. a simple program is a statement

To keep all values in $\mathbb{N}$, $\text{pred}(0) = 0$.

> [!faq] Examples
> A simple code for the macro statement $X := Y$
> $X := \text{succ}(Y); X := \text{pred}(X)$
> 
> A simple code for the macro statement $X := 3$
> $X := 0, X:= \text{succ}(X); X:= \text{succ}(X); X:= \text{succ}(X)$

#### Model 3: Markov algorithms
These are equivalent in power to Turing machines.

A Markov algorithm over an alphabet $\Sigma$ is a finite ordered sequence of productions $x \rightarrow y$, where $x, y \in \Sigma^{\ast}$.
- some productions may be labeled with the word "halt" (although not required)
- if there is a production $x \rightarrow y$ such that $x$ occurs as a substring of $w,$ then the leftmost occurrence of $x$ in $w$ is replaced by $y$.
- a Markov algorithm transforms an input string into an output string $\Rightarrow$ **it computes a function from $\Sigma^{\ast}$ to $\Sigma^{\ast}$.**

Given an input string:
1. check the productions in order from top to bottom to see whether any of the patterns can be found in the input string
2. if none are found, the algorithm stops
3. if one (or more) is found, use the first of them to replace the leftmost matching text in the input string
4. if the applied production was a terminating one, the algorithm stops
5. return to step 1 and continue
Assumption: $w = {\lambda}w$. So a production of the form $\lambda \rightarrow y$ would transform $w$ to $yw$.

> [!faq] Example
> Suppose $M$ is the Markov algorithm over $\{a, b\}$ consisting of the following sequence of three productions:
> 1. $aba \rightarrow b$
> 2. $ba \rightarrow b$
> 3. $b \rightarrow \lambda$
> 
> We can trace the execution of $M$ for the string $w = aabaaa$:
> 	$w = aabaaa$ 
> 	$\rightarrow abaa$
> 	$\rightarrow ba$
> 	$\rightarrow b$
> 	$\rightarrow \lambda$
> 
> The algorithm returns:
> - $\lambda$ for all strings of the form $a^iba^j$ where $i \leq j$
> - $a^{i-j}$ for all strings of the form $a^iba^j$ where $i \gt j$

> [!faq] Example
> Write the Markov algorithm which will delete all $a$-s from any string over the alphabet $\{a, b, c\}$
> 
> $$a \rightarrow \lambda$$


#### Model 4: Post algorithms
A Post algorithm is a string processing model, which is equivalent to the power of a TM.

A Post algorithm over an alphabet $\Sigma$ is the set of productions that are used to transform strings:
- the productions have the form $s \rightarrow t$, where $s$ and $t$ are strings made up of symbols from $\Sigma$ and possible some variables
- if a variable $X$ occurs in $t$ then $X$ occurs in $s$
- some productions may be labeled with the word "halt" (although not required)

Given an input string $w \in \Sigma^{\ast}$:
1. find a production $x \rightarrow y$ such that $w$ matches $x$
2. if so, use the match and $y$ to construct a new string. Otherwise, halt
3. if the $x \rightarrow y$ is labeled with (halt), then halt
4. return to step 1 and continue
Variables may also match $\lambda$. A Post algorithm can be either deterministic or nondeterministic.

> [!faq] Example
> Consider the following single production over the alphabet $\{a, b\}:$
> 	$aXb \rightarrow X$
> 
> Start with the string $aab$:
> - execution starts by matching $aab$ with $aXb$, where $X = a$
> - thus $aab$ is transformed into the string $a$
> - since $a$ doesn't match the left hand side of the production, the computation halts
> 
> $X$ can match the empty string too and in that way $ab$ can be transformed into $\lambda$.

The Post algorithm does many things, for example it transforms any string of the form $a^ib$ to $a^{i - 1}$ for $i \gt 0$.


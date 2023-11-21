#### Preliminaries
The initial proofs of undecidability use a technique called *self-reference*, or *diagonalisation*.

Any system that is powerful enough to allow self-reference is going to present problems - this can be illustrated with the Barber paradox.

> [!faq] Barber Paradox
> Suppose there is a town
> - with just one male barber, and that
> - every man in the town keeps himself clean-shaven: some by shaving themselves, some by attending the barber;
> - the barber obeys the following rule: He shaves all and only those men in town who do not shave themselves
> 
> Under this scenario, we can ask the following question: Does the barber shave himself?
> - if he does not shave himself, he must abide by the rule and shave himself
> - if he does shave himself, he does not need to shave himself
> 
> Since there is no solution, it is a paradox.

#### Diagonalisation
What makes two sets the same size? How can we easily say that two sets have the same size without counting the elements?
- if they are finite, we can pair the sets off (*1-1 correspondence*)
- if a set is infinite, does the set have the same size as the set $\mathbb{N}$ of all positive integers $\{1, 2, ...\}$? Or is it larger?

> [!faq] Example
> The even numbers are the same size as $\mathbb{N}$, we can pair them:
> 
> 1 - 2
> 2 - 4
> 3 - 6
> etc...

A set is defined as *countably infinite* if it is the same size as $\mathbb{N}$.
A set is *countable* if it is finite or countably infinite - this means we can construct a numbered list of all its elements.

For example, the set of integers, the set of odd numbers, and the set of rational numbers are all countable.

> [!faq] Question
> What about the size of the set $\mathcal{P}(\mathbb{N})$ of all subsets of $\mathbb{N}$? Is it countable?
> 
> $$\mathcal{P}(\mathbb{N}) = \{\emptyset, \{0\}, \{1\}, \{2\}, \{3\}, \{1, 2\}, ...\}$$
> 
> The answer is NO, and the proof is based on a method called *diagonalisation*.
> 
> ($\mathcal{P}$ is the power subset.)

##### Diagonalisation Proof
When we have a list of words of the same length, how can we construct a word that is not on the list?
$$\begin{bmatrix} Q & U & I & E & T \\ S & T & O & N & E \\ O & F & F & E & R \\ C & L & E & A & R \\ P & H & L & O & X \end{bmatrix}$$
The idea is to start with the diagonal as a word and replace each letter by the next letter in the alphabet.

For example, the diagonal string from $\text{Q}$ to $\text{X}$ is originally $\text{QTFAX} \rightarrow \text{RUGBY}$.

This new word cannot be in the list, as
- it is different from the first word in the first letter,
- different from the second word in the second letter,
- etc

#### Uncountable sets
> [!info] Theorem (Cantor Theorem)
> The set $\mathcal{P}(\mathbb{N})$ is not countable.

Suppose it is countable - then we can write down a list of all the subsets of $\mathbb{N}$. It could look like
$$1 \rightarrow \{2,3\}, 2 \rightarrow \{4,7\}, 3 \rightarrow \{2, 4, 6, 8\}, ... $$
So we have a function $\text{f} : \mathbb{N} \rightarrow \mathcal{P}(\mathbb{N})$ that maps numbers to sets such that every set appears in the list.

Now define a set $\text{T}$ as follows: add $i$ to the set $\text{T}$ exactly when $i \notin \text{f}(i)$, e.g
$1 \in \text{T}$ because $1 \notin \text{f}(1)$, $3 \in \text{T}$ because $3 \notin \text{f}(2)$, ...

But the set $\text{T}$ is not on the list - $\text{T}$ is different from the first set, the second set, ... $\implies \text{T}$ is not on the list, which contains all subsets of $\mathbb{N}$.

This is a contradiction - such a list does not exist, and $\mathcal{P}(\mathbb{N})$ is not countable.

Another example of an uncountable set is the set of real numbers.

#### Decision Problems
> [!info] Definition
> A decision problem is a problem that asks a question with a yes or no answer.
> 
> > [!faq] Example 1
> > Decide whether in a given finite array of integers the maximum is larger than 10.
> 
> ${}$
> > [!faq] Example 2
> > For a given language $\text{L}$, decide whether a string $s$ is from $\text{L}$ or not.
>
> ${}$
> > [!faq] Example 3
> > Decide whether the following polynomial has a solution in $\mathbb{N}$:
> > $$\text{f}(x) = 2x^{10} - 3x^8 + 4x^6 + 32x + 10$$

A decision problem can be viewed as a formal language:
- where the members of the language are instances whose answer is yes, and
- the non-members are those instances whose output is no.

> [!info] Definition
> A decision problem is decidable if there is an algorithm that for every input instance of the problem halts with a correct answer, YES or NO.
> 
> If no such algorithm exists, then the problem is undecidable.

> [!faq] Example (decidable)
> To decide whether a particular string $w$ is in a given regular language is a decidable problem.
> 
> Decidable problems correspond to the cursive languages. They can be recognised by Turing machines that halt for every input.

##### Partial decision problems
> [!info] Definition
> An undecidable decision problem is partially decidable if there is an algorithm that
> - halts with the answer yes for those instances of the problem that have yes answers, but
> - may run forever for those instances of the problem whose answers are no
> 
> (the opposite is also true with 'yes' and 'no' swapped)

> [!faq] Example (partially decidable)
> Deciding whether a particular string $w$ is in a language generated by an unrestricted grammar is a partially decidable problem.

##### Existence of an undecidable problem
The set of TMs is countable, meaning
- the set of languages that are accepted / recognised by TMs is countable,
- the set of languages that are described by a grammar,
- $\implies$ the set of decidable problems is countable

The set of all languages (the set of all decision problems) is uncountable.

Therefore, there exists a language which can't be recognised by any TM (or described by any grammar). There exists an undecidable problem!

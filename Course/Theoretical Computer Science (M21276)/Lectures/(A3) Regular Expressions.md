**Ways to describe a regular language:**
- Languages that are inductively formed from combining very simply languages
- Those described by a regular expression
- Languages produced by a grammar with a special, very restricted form
- Languages that are accepted by some finite automaton

**Option 1: Building a regular language**
We start with the very basis of languages and build more complex ones by combining them.

Basic grammar:
	$\emptyset, \{\lambda\} \: \text{and} \: \{a\}$ are regular languages for all $a \in \Sigma$.
Induction:
	If $L$ and $M$ are regular languages, then the following languages are also regular:
		$L \cup M, \: L \cdot M, \: \text{and} \: L^\ast$.

All languages that you build this way are regular languages.

Example: over the alphabet $\Sigma = \{a, b\}$ we can get:
	$\emptyset, \{\lambda\}, \{a\}, \{b\}$ 
All regular languages over $\Sigma$ can be built from combining these four in various ways by recursively using the union, product and closure operation.

1. Is the language $\{\lambda, b\}$ regular?
	Yes, as it is the union of $\{\lambda\} \: \text{and} \: \{b\}$.

2. Is the language $\{a, ab\}$ regular?
   Yes, as it is the product of $\{a\} \: \text{and} \: \{\lambda, b\}$, which in turn is the union of $\{\lambda\} \: \text{and} \: \{b\}$.

However, many infinite languages are also regular.

3. Is the language $\{\lambda, b, bb, ..., b^n, ...\}$ regular?
   Yes, as it is the closure of $\{b\}$.

4. Is the language $\{a, ab, abb, ... ab^n, ...\}$ regular?
   Yes, as it is the product of $\{a\}$ and $\{b\}^\ast$.

5. Is the language $\{\lambda, a, b, aa, bb, ..., a^n, b^n, ...\}$ regular?
   Yes, as it is the union of $\{a\}^\ast \: \text{and} \: \{b\}^\ast$.

6. Is the language $\{b, aba, aabaa, ..., a^nba^n, ...\}$ regular?
   No, as we cannot build it using the union, product and closure operations.
   However, the similar language $\{b, ab, ba, aba, aab, baa, ..., a^nba^m, ...\}$ can be regular, as $n$ and $m$ can be different values.


**Option 2: Regular expressions**
A regular expression is essentially a shorthand way of showing how a regular language is built from the base set of regular languages. The symbols are nearly identical to those used to construct the languages, and any given expression has a language closely associated with it.

For each regular expression $E$ there is a regular language $L(E)$, but the symbols are distinct ie
- Expression $\emptyset$ correlates to $L(\emptyset) = \emptyset$.
- Expression $\lambda$ correlates to $L(\lambda) = \{\lambda\}$.
- Expression $a$ correlates to $L(a) = \{a\}$.

Like the languages they represent, regular expressions can be manipulated inductively to form new regular expressions.

Basic grammar:
	$\lambda, \emptyset$ and $a$ are regular expressions for all $a \in \Sigma$.
Induction:
	If $R$ and $E$ are regular expressions, then the following expressions are also regular:
		$(R), R + E, R \cdot E,$ and $R^\ast$.

The order of operations still applies - $x^n$ first, $\times$ second, and $+$ last.

The operators $+, \cdot$ and $\ast$ are closely associated with the union, product and closure operations on the corresponding languages.

Distinct regular expressions do not always represent distinct languages!

Example: the regular expressions $a + b$ and $b + a$ are different, but they both represent the same language:
	$L(a + b) = L(b + a) = \{a, b\}$

**Equivalence**
There are many general equalities for regular expressions. All the properties hold for any regular expressions and can be verified by using properties of languages and sets.

We can use these properties to simplify regular expressions and prove equivalences:

Example: Show $(\emptyset + a + b)^\ast = a^\ast(ba^\ast)^\ast$.
	$(\emptyset + a + b)^\ast = (a + b)^\ast$ ($+$ property)
					   $= a^\ast(ba^\ast)^\ast$ (closure property)

**Option 3: Regular grammars**
A regular grammar is one where each production takes one of the following restricted forms:
- $B \rightarrow \lambda$
- $B \rightarrow w$
- $B \rightarrow A$
- $B \rightarrow wA$
(where $A, B$ are non-terminals and $w$ is a non-empty string of terminals).
All other possible productions are forbidden in regular grammars.

Only one non-terminal can appear on the right hand side of a production. Non-terminals must appear on the right end of the right hand side.

Example: $A \rightarrow aBc$ and $S \rightarrow TU$ are not productions part of a regular grammar, but the production $A \rightarrow abcA$ is.

Additionally, productions like $A \rightarrow aB|cC$ is allowed because they are actually two separate productions.

For any regular language, we can find a regular grammar which will product it. However, there may be other non-regular grammars which also produce it.

Example: The regular language $a^{\ast}b^\ast \rightarrow$ 
	Irregular grammar:
		$S \rightarrow AB$
		$A \rightarrow \lambda|aA$
		$B \rightarrow \lambda|Bb$
	Regular grammar:
		$S \rightarrow \lambda | aS | A$
		$A \rightarrow \lambda | bA$

**Some simple examples**

| Regular Expression | Regular Grammar |
|---|---|
|$a^\ast$|$S \rightarrow \lambda \vert bS$|
|$(a + b)^\ast$|$S \rightarrow \lambda \vert aS \vert bS$|
|$a^\ast + b^\ast$|$S \rightarrow \lambda \vert A \vert B$ <br> $A \rightarrow a \vert aA$ <br> $B \rightarrow b \vert bB$|
|$a^{\ast}b$|$S \rightarrow b \vert aS$|
|$ba^\ast$|$S \rightarrow bA$ <br> $A \rightarrow \lambda \vert aA$ 
|$(ab)^\ast$|$S \rightarrow \lambda \vert abS$| 

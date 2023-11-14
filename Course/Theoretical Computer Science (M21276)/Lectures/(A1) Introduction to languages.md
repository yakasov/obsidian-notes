**Alphabet:** 
a finite, nonempty set of symbols
e.g. $\Sigma$ = *{a, b, c}*

**String:** 
a finite sequence of symbols from the alphabet, placed together in juxtaposition
e.g. *abc, aaa, bc* are examples of strings in $\Sigma$ 
a string with no symbols is called an empty string and is denoted $\lambda$

**Language:** 
if $\Sigma$ is a language, then a language over $\Sigma$ is a set of strings (including empty string $\lambda$) whose symbols come from $\Sigma$.
e.g. if $\Sigma$ = *{a, b}* then 
	$L$ = *{ab, aaaab, abbb, a}*
is an example of a language over $\Sigma$.

if $\Sigma$ is an alphabet, then $\Sigma^\ast$ denotes the infinite set of all strings made up from $\Sigma$ (including an empty string $\lambda$).
e.g. if $\Sigma$ = *{a, b}* then 
	$\Sigma^\ast$ = *{$\lambda$, a, b, ab, aab, aaab, bba, ... }*.
Looking at $\Sigma^\ast$, a language over $\Sigma$ is any subset of $\Sigma^\ast$.

**Product of two languages:**
if $L$ and $M$ are languages, then the new language (called the product of $L$ and $M$) is defined as $L$ $\cdot$ $M$ (or only $LM$).
	$L$ $\cdot$ $M$ = *{cat($s,\: t$) : $s \in L$ and $t \in M$}*

The operation of concatenation is not commutative. In other words, the order matters. Given two languages L and M, it's usually true that:
	$L \:\cdot M \neq M \:\cdot L$

The operation of concatenation is associative. In other words, if $L,\: M$ and $N$ are languages, then
	$L \cdot (M \cdot N)$ = $(L \cdot M) \cdot N$ 

**Powers of languages:**
If $L$ is a language, then the product $L \cdot L$ is denoted as $L^2$.
The language product L$^n$ for every $n \in$ *{0, 1, 2, ...}* is defined as follows:
	$L^0$ = {$\lambda$}
	$L^n = L \cdot L^{n-1}$ , if $n \gt 0$.

**Closure of a language:**
If $L$ is a language over $\Sigma$ (i.e $L\subset\Sigma^\ast$) then the closure of $L$ is the language denoted by $L^\ast$ and is defined as follows:
	$L^\ast = L^0 \,\cup\, L^1 \,\cup\, L^2 \,\cup\, L^3 \,\cup\,$...   

The positive closure of L is a language denoted by L$^+$ and defined as follows:
	$L^+ = L^1 \,\cup\, L^2 \,\cup\, L^3 \,\cup\, L^4 \,\cup\,$...    

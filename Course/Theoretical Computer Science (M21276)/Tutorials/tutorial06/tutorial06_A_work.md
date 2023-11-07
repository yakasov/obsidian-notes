1. 
   a. the difference between regular and context-free grammar:
	   all context-free grammars have productions with a single non-terminal on the left, which means any production $N \rightarrow \alpha$ can be used in derivation without regard to the context in which $N$ appears.<br>
	   this is different to regular grammars which are linear, and the production rule must be $N \rightarrow A$ or $N \rightarrow Ax$.
  b. an example of a context-free language that is not regular is
	  $S \rightarrow aSb$ 
  c. proof by contradiction using pumping lemma
  d. an infinite regular language accepted by $m$ states means any string $w$ in $L$ with at least $m$ symbols can be decomposed as $w = xyz$ with $|xy| \leq m$ and $|y| \geq 1$.
  e. if we have $n$ pigeons and $m$ pigeonholes, where $n \gt m$, at least one pigeonhole must have more than one pigeon

2. $A, B$ non-terminals, $S$ initial non-terminal, and $0, 1$ terminals
	   $S \rightarrow 0 \:|\: 0A$
	   $A \rightarrow 1B$
	   $B \rightarrow 0 \:|\: 0A$
  a. regular grammar (the smallest Chomsky class possible) <span class="tick">✓</span>
  b. 0, 010, 01010 - 0 followed by any amount of (10)s 
	  $L = \{0(10^n \:|\: n \geq 0\}$ <span class="tick">✓</span>
  c. $(01)^{\ast}0$ <span class="tick">✓</span>

3. $A, B$ non-terminals, $S$ initial non-terminal, and $0, 1$ terminals
	   $S \rightarrow 0A \:|\: 1A$
	   $A \rightarrow 1BB$
	   $B \rightarrow 11 \:|\: 01$
  a. this grammar is context-free and is finite, belonging to the regular Chomsky class. <span class="tick">✓</span>
  b. 011111, 111111, 010111 - always the length six, always second character 1 <span class="tick">✓</span>
  c. (0 + 1)1(11 + 01)(11 + 01) <span class="tick">✓</span>

4. for each of the following languages over the alphabet $\{a, b\}$, state whether it is regular or not
  a. $\{(ab)^n \:|\: n \gt 100\}$ 
	$\underbrace{ab...ab}_{101}(ab)^\ast$, regular <span class="tick">✓</span>
  b. $\{(ab)^n \:|\: n \lt 100\}$ 
	Finite $\implies$ regular <span class="tick">✓</span>
  c. $\{a^nb^n \:|\: n \lt 100\}$ 
    Finite $\implies$ regular <span class="tick">✓</span>
  d. $\{a^nb^nc^n \:|\: n \gt 1\}$ 
    not regular - not possible with finite automata due to finite memory, can be proved using pumping lemma <span class="tick">✓</span>

5. find a context-free grammar for the following languages over $\Sigma = \{a, b\}$
  a. $L = \{ab(bbaa)^nbba(ba)^n \:|\: n \geq 0\}$
	  $S \rightarrow abA$  
	  $A \rightarrow bbaaAba \:|\: bba$
	  this is not a regular language because $A \rightarrow bbaaAba$ does not end in a terminal
  b. $L = \{a^nb^m \:|\: 0 \leq n \leq m + 3\}$
	  $S \rightarrow AbbbB$
	  $A \rightarrow aA \:|\: \Lambda$
	  $B \rightarrow bB \:|\: \Lambda$ 
  c. $L = \{a^nb^m \:|\: 0 \leq 2n \leq m \leq 3n\}$
	  $S \rightarrow \:?$ 

6. $A, B, C$ non-terminals, $S$ initial non-terminal, which generates the language $L$ over the alphabet $\{a, b, c\}$ with the following grammar:
	$S \rightarrow SABC \:|\: ABC$ 
	$AB \leftrightarrow BA$
	$BC \leftrightarrow CB$
	$AC \leftrightarrow CA$
	$A \rightarrow a$
	$B \rightarrow b$
	$C \rightarrow c$
  i. three strings from $L$ include: $abc, abcabc, bac$
  ii. $abac$ is not in the language, as all strings must be a multiple of 3 characters long
  iii. no, because it's not a regular language (why?)
  iv. ?
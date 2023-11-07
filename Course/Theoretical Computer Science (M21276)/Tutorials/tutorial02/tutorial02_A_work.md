**Question 1**
Given the set of terminals $\{0, 1, 2, 3, 4, 5, 6, 7, 8, 9\}$, the start symbol $S$, another non-terminal symbol $D$ and the set of productions:
- $S \rightarrow D\:|\:DS$
- $D \rightarrow 0\:|\:1\:|\:2\:|\:3\:|\:4\:|\:5\:|\:6\:|\:7\:|\:8\:|\:9$

- $S \implies DS \implies 7S \implies 7DS \implies 7DDS \implies 78DS \implies 780S \implies 780D \implies 7801$ 
  1. $S \rightarrow DS = DS$ <span class="tick">✓</span>
  2. $D \rightarrow 7 = 7S$ <span class="tick">✓</span>
  3. $S \rightarrow DS = 7DS$ <span class="tick">✓</span>
  4. $S \rightarrow DS = 7DDS$ <span class="tick">✓</span>
  5. $D \rightarrow 8 = 78DS$ <span class="tick">✓</span>
  6. $D \rightarrow 0 = 780S$ <span class="tick">✓</span>
  7. $S \rightarrow D = 780D$ <span class="tick">✓</span>
  8. $D \rightarrow 1 = 7801$ <span class="tick">✓</span>
- 2468, 123412341234, 9999, 1 <span class="tick">✓</span>
- $S \implies DS \implies 7S \implies 7DS \implies 78S \implies 78DS \implies 780S \implies 780D \implies 7801$ <span class="tick">✓</span>
- $S \implies DS \implies DDS \implies DDDS \implies DDD1 \implies DD01 \implies D801 \implies 7801$ <span class="tick">✓</span>

**Question 2**
Given the set of terminals $\{a, b\}$ and the non-terminal start symbol $S$:
- $S \rightarrow a \:|\: aS$
  $= \{a, aa, aaa, aaaa,...\}$ <span class="tick">✓</span>
  
- $S \rightarrow \Lambda \:|\: aSb$
  $= \{\Lambda, ab, aabb, aaabbb, aaaabbbb, ...\}$ <span class="tick">✓</span>
  
- $S \rightarrow aS \:|\: bS$
  $= \emptyset$ (no finite string can be constructed, which it must be if over the language $\{a,b\}$) <span class="tick">✓</span>

**Question 3**
All with the non-terminal start symbol $S$:
- $\{bb, bbbb, bbbbbb, ...\}$
  Terminals: $\{b\}$ <span class="tick">✓</span>
  Rules: $S \rightarrow bb \:|\: bbS$ <span class="tick">✓</span>
  
- $\{a, ba, bba, bbba, ...\}$
  Terminals: $\{a, b\}$ <span class="tick">✓</span>
  Rules: $S \rightarrow a \:|\: bS$ <span class="tick">✓</span>
  
- $\{\Lambda, ab, abab, ababab, ...\}$
  Terminals: $\{\Lambda, ab\}$ <span class="cross">{a, b}</span>
  Rules: $S \rightarrow \Lambda \:|\: abS$ <span class="tick">✓</span>
  
- $\{bb, bab, baab, baaab, ...\}$
  Terminals: $\{a, b\}$
  Rules: $S \rightarrow bb \:|\: bAb$ <span class="cross">S -> bAb only</span>
	     $A \rightarrow aA \:|\: a$ <span class="cross">A -> Lambda | aA</span>

**Question 4**
If $w$ is a string, let $w^R$ denote the reverse of $w$.
To describe the language $\{ww^R \:|\: w \in \Sigma^\ast\}$ for $\Sigma = \{a, b, c\}$, a possible grammar is:
- Terminals: $\{\Lambda, a, b, c\}$ <span class="cross">{a, b, c} only</span>
  Rules: $S \rightarrow aSa \:|\: bSb \:|\: cSc \:|\: \Lambda$ <span class="tick">✓</span>

**Question 5**
The set of binary numerals that represent odd natural numbers.
- Non-terminals: $\{0\}$ <span class="cross">{S, A}</span>
  Terminals: $\{\Lambda, 1\}$ <span class="tick">✓</span>
  Rules:  $S \rightarrow 1 \:|\: 1A1$ <span class="tick">✓</span>
	      $A \rightarrow 0A \:|\: 1A \:|\: \Lambda$ <span class="tick">✓</span>

The set of decimal numerals that represent odd natural numbers.
- Non-terminals: $\{0, 2, 4, 6, 8\}$ <span class="cross">{S}</span> 
  Terminals: $\{1, 3, 5, 7, 9\}$ <span class="tick">✓</span>
  Rules: $S \rightarrow \{0, 1, 2, 3, 4, 5, 6, 7, 8, 9\}S \:|\: \{1, 3, 5, 7, 9\}$ <span class="tick">✓</span>

**Question 6**
A grammar for each of the following languages over the alphabet $\{a, b, c\}$:
- $\{a^nb \:|\: n \geq 0\}$
  Terminals: $\{a, b\}$ <span class="tick">✓</span>
  Rules: $S \rightarrow aS \:|\: ab$ <span class="cross">S -> b | aS</span>
  <span class="cross">. Non-terminals: {S}</span>
  
- $\{a^nb^m \:|\: n \geq 1 \;\text{and}\; m \geq 1 \}$
  Terminals: $\{a, b\}$ <span class="tick">✓</span>
  Rules: $S \rightarrow aAb$ <span class="tick">✓</span>
	     $A \rightarrow aA \:|\: bA \:|\: a \:|\: b$ <span class="tick">✓</span>
<span class="cross">. Non-terminals: {S, A}</span>
  
- $\{a^nbc^n \:|\: n \geq 0\} \cup \{b^na^m \:|\: n \geq 0 \; \text{and} \; m \geq 0\}$ 
  Terminals: $\{a, b, c\}$ 
  Rules: $U \rightarrow S \:|\: X$ <span class="tick">✓</span>
	      $S \rightarrow aSc \:|\: b$ <span class="tick">✓</span>
	      $X \rightarrow bX \:|\: Y$ <span class="tick">✓</span>
	      $Y \rightarrow aY \:|\: \Lambda$<span class="tick">✓</span>
<span class="cross">. Non-terminals: {U, S, X, Y}</span>
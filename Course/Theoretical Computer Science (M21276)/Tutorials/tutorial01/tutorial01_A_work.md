**Question 1**
- $\Sigma$ of size 3 = $\{a, b, c\}$ <span class="tick">✓</span>
- $\{aaa, bbb, ccc, abc, aab, ...\}$ <span class="tick">✓</span>
- $L = \{aaa, bbb, cccccc, abcabc, aab, ...\}$ <span class="tick">✓</span>
- $\Sigma^\ast$ denotes the infinite set of all strings made from $\Sigma$, so $L$ is a subset of $\Sigma^\ast$. <span class="tick">✓</span>

**Question 2**
$\Sigma = \{a, b\}$, $L = \{\Lambda, a, ab, bb\}$ and $M = \{a, b, ab, ba\}$
- $L \cup M = \{\Lambda, a, b, ab, ba, bb\}$ <span class="tick">✓</span>
  $L \cap M = \{a, ab\}$ <span class="tick">✓</span>
  $L \cup \Sigma^\ast = \{\Sigma^\ast\}$  <span class="tick">✓</span>
  $L \cap \Sigma^\ast = \{L\}$ <span class="tick">✓</span>
  $L^0 = \{\Lambda\}$  <span class="tick">✓</span> 
  $L^2 = \{aa, ab, bb\}$ 
  $L^\ast = \{L^0 \cup L^1 \cup L^2 \:\cup \: ...\}$ <span class="tick">✓</span>
- $\{bbb, abbb, babb, bbab, bbba\}$ <span class="tick">✓</span>
- $L^\ast \:\backslash\: L^2 = \{a\}$ <span class="tick">✓</span>

**Question 3**
$L = \{\Lambda, abb, b\}$ and $M = \{bba, ab, a\}$
- $L \cdot M = \{bba, ab, a, abbbba, abbab, abba, bbba, bab, ba\}$ <span class="tick">✓</span>
- $M \cdot L = \{bba, bbaaab, bbab, abaab, abb, a, aabb, ab\}$ <span class="tick">✓</span>
- $L^2 = \{\Lambda, abb, b, abbabb, abbb, babb, bb\}$ <span class="tick">✓</span>

**Question 4**
- $\{\Lambda, a, ab\} \cdot L = \{b, ab, ba, aba, abb, abba\}$
  Set $A$ has 3 elements, Set $B$ has 6 elements, so Set $L$ must have 2 elements.
  $L = \{b, ba\}$ <span class="tick">✓</span>
  
- $L \cdot \{a, b\} = \{a, baa, b, bab\}$
  Set $A$ has 2 elements, Set $B$ has 2 elements, so Set $L$ must have 2 elements.
  $L = \{\Lambda, ba\}$ <span class="tick">✓</span>
  
- $\{a, aa, ab\} \cdot L = \{ab, aab, abb, aa, aaa, aba\}$
  Set $A$ has 3 elements, Set $B$ has 6 elements, so Set $L$ must have 2 elements.
  $L = \{b, a\}$ <span class="tick">✓</span>
  
- $L \cdot \{\Lambda, a\} = \{\Lambda, a, b, ab, ba, aba\}$
  Set $A$ has 2 elements, Set $B$ has 6 elements, so Set $L$ must have 3 elements.
  $L = \{\Lambda, b, ba\}$ <span class="tick">✓</span>

**Question 5**
- $\{\Lambda\}^\ast = \emptyset^\ast = \{\Lambda\}$
  $\{\Lambda\}^\ast$ is the infinite set of $\Lambda$, which is in turn equal to $\{\Lambda\}$. The only possible concatenations from the empty set $\emptyset^\ast$ is $\{\Lambda\}$, $\therefore$ proof
  
- $L^\ast = L^\ast \cdot L^\ast = (L^\ast)^\ast$ 
  $L^\ast$ represents the infinite set of concatenations of $L$, and so $L^\ast \cdot L^\ast$ is the infinite set of concatenations multiplied by the infinite set of concatenations, which is equal to $L^\ast$, $\therefore$ we can use the same reasoning to say that $L^\ast$ must be equal to $(L^\ast)^\ast$.

- $\Lambda \in L$ if and only if $L^+ = L^\ast$.
  If $L^+ = L^\ast$ then $L^1 \cup L^1 \cup L^2 \cup \:$ ... $= L^0 \cup L^1 \cup L^2 \cup L^3 \cup \:$...
  For $L^+$ to contain an element equal to $L^0$, $L$ must contain the element $\Lambda$.
  
- $L \cdot (M \cdot L)^\ast = (L \cdot M)^\ast \cdot L$
  The operation of concatenation is associative. 
  ?
  
- $(L^\ast \cdot M^\ast)^\ast = (L^\ast \cup M^\ast)^\ast = (L \cup M)^\ast$
  ? 
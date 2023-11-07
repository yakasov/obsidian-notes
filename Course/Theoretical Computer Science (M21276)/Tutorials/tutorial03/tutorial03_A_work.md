**Question 1**
Find the language corresponding to each of the following regular expressions over the alphabet $\{a, b, c\}$.
i. $a + b$
  $= a \cup b$
  $= \{a, b\}$ <span class="tick">✓</span>
ii. $a + bc$
  $= a \cup bc$
  $=\{a, bc\}$ <span class="tick">✓</span>
iii. $ab + ba$
  $= ab \cup ba$
  $= \{ab, ba\}$ <span class="tick">✓</span>
iv. $ab^\ast$
  $= a \cdot b^\ast$
  $= \{a, ab, abb, abbb, abbbb, ...\}$ <span class="tick">✓</span>
v. $a + b^\ast$
  $= a \cup b*$
  $= \{a, \Lambda, b, bb, bbb, bbbb, ...\}$ <span class="tick">✓</span>
vi. $ab^\ast + c$
  $= (a \cdot b^\ast) \cup c$
  $= \{c, a, ab, abb, abbb, abbbb, ...\}$ <span class="tick">✓</span>
vii. $ab^\ast + bc^\ast$
  $= (a \cdot b^\ast) \cup (b \cdot c^\ast)$
  $= \{a, ab, abb, abbb, ..., b, bc, bcc, bccc, ...\}$ <span class="tick">✓</span>
viii. $a^{\ast}bc^\ast + ac$
  $= (a^\ast \cdot b \cdot c^\ast) \cup (a \cdot c)$
  $= \{b, ac, a^{\ast}bc^\ast\}$ <span class="tick">✓</span>

**Question 2**
Find all strings in $L((a + b)^{\ast}b(a +ab)^\ast)$ of length less than four.
  $= \{a, b\}^\ast \cdot \{b\} \cdot \{a, ab\}^\ast$ 
  $= \{b, ab, ba, bb, aab, aba, baa, bbb, bab, bba\}$ <span class="tick">✓</span>

**Question 3**
Find a regular expression to describe each of the following languages over the alphabet $\{a, b, c\}$.
i. $\{a, b, c\}$
  $= a + b + c$ <span class="tick">✓</span>
ii. $\{aa, ab, ac\}$
  $= a(a + b + c)$ <span class="tick">✓</span>
iii. $\{\Lambda, bb, bbbb, bbbbbb, ...\}$
  $= (bb)^\ast$ <span class="tick">✓</span>
iv. $\{a, b, ab, ba, abb, baa, ..., ab^n, ba^n, ...\}$
  $= ab^\ast + ba^\ast$ <span class="tick">✓</span>
v. $\{a, aaa, aaaaa, ..., a^{2n+1}, ...\}$
  $= a(aa)^\ast$ <span class="tick">✓</span>
vi. $\{\Lambda, a, abb, abbbb, ..., ab^{2n}, ...\}$
  $= \emptyset + a(bb)^\ast$ <span class="tick">✓</span>
vii. $\{\Lambda, a, b, c, aa, bb, cc, ..., a^n, b^n, c^n, ...\}$
  $= a^\ast + b^\ast + c^\ast$ <span class="tick">✓</span>
viii. $\{\Lambda, a, b, ca, bc, cca, bcc, ..., c^{n}a, bc^n, ...\}$
  $= \emptyset + c^{\ast}a + bc^\ast$ <span class="tick">✓</span>
ix. $\{a^nb^m, n \geq 4, m \leq 3\}$
  $= aaaa(a)^\ast(\Lambda + b + bb + bbb)$ <span class="tick">✓</span>
x. $\{a^nb^m, n \geq 3, m \:\text{is even}\}$
  $= aaaa^{\ast}(bb)^\ast$ <span class="tick">✓</span>
xi. $\{a^nb^m, (n + m) \:\text{is even}\}$
  $= (aa)^\ast(bb)^{\ast} + (aa)^\ast(bb)^\ast(ab+ba)(aa)^\ast(bb)$ <span class="cross">+ a(aa)*b(bb)*</span> 

**Question 4**
Find a regular expression for each of the following languages over the alphabet $\{a, b\}$.
i. All strings with even length
  $= ((a + b)(a + b))^\ast$ <span class="tick">✓</span>
ii. All strings whose length is a multiple of 3
  $= ((a + b)(a + b)(a + b))^\ast$ <span class="tick">✓</span>
iii. All strings containing the substring $aba$
  $= (a + b)^{\ast}aba(a + b)^\ast$ <span class="tick">✓</span>
iv. All strings with an odd number of $a$'s.
  $= b^{\ast}ab^{\ast}(ab^{\ast}ab^{\ast})^\ast$ <span class="tick">✓</span>
v. All strings except those with the substring $aa$.
  $= b^{\ast}a(b + b^{\ast}a)^\ast$ ? <span class="cross">(b + ab)*(Lambda + a)</span>
vi. All strings except those with the substring $aaa$.
  $=$ <span class="cross">(b + ab +aab)*(Lambda + a + aa)</span>
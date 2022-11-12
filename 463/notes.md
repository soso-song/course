### Question:

- relation between reduction vs reduction technique vs mapping reduction vs A$\leq_{m}$B
  - ch5.1 reduction from A~TM~, to prove HALT~TM~ is undecidable (p219)
    - (reduction then conclude -> contradiction) check below
    - reduction from A to B
      - Assume B has decider
      - Build A's decider that sloves A 
  - ch5.3 example 5.24 made a TM F that compute the mapping function (p219)
  - textbook
    - example 5.26 saying reduction from E~TM~ which is same as reduction from A~TM~ are mapping reduction
  - I can see there are big differece between Example 5.24 (p236) and (p219)

## Computability

#### A$\leq_{m}$B $\iff$ $\overline{\text{B}}\leq_m\overline{\text{A}}$ 

When A is reducible to B, solving A cannot be harder than solving B because a solution to B gives a solution to A. 

#### Rice’s theorem (lec4)

> states that determining any property of the languages recognized by Turing machines is undecidable

Suppose P is a language of TM description such that

- P is nontrivial: 
  - $\exists\ TM\in P, \exists\ TM\notin P$
  - it contains some but not all TM description
- P is a property of the TM's languages:
  - $L(M_1) = L(M_2) \rightarrow \langle M_1\rangle\in P \text{ iff } \langle M_2\rangle\in P$
- then P is an undecidable language

Note: language P has to be defined in terms of the semantics of the TM, not by its structure.

Examples (they all undecidable):

- EMPTY~TM~ = {\<M>: L(M) = $\empty$}
- FINITE~TM~ = {\<M>: L(M) = is finite}
- DECIDABLE = {\<M>: L(M) is decidable}

Note: doesn't apply to {\<M>: M is a decider}

Prove (LEC):

- Assume \<T~0~> $\notin$ P | T~0~ rejects everything
- Assume \<T~1~> $\in$ P because P is non trivial, so T~1~ existst
- Reduce A~TM~ $\leq_m$ P
  - \<M,w> land on T~0~ and T~1~

#### Computation histories (p220)

finite sequences of configurations thats end in accepting/rejecting status

#### Reduction from A~TM~ Ch5.1(p219)

Prove a language is undecidable by successfully using it's "decider" to decide an undecidable language

- Assume HALT~TM~ is decide by R and use this to construct S that decides A~TM~, but we know A~TM~ is undecidable -> $\nexists$ R that decides HALT~TM~
- It's different reduction techniques from A~TM~$\leq_{m}$HALT

#### Mapping Reducibility Ch5.3(p234).         (*many-one reducibility*)

Prove a language are **not Turing-recognizable** and applizations in **complexity theory**.

Reduce problem A to B by using MR means $\exists$ **computable function** that converts instances of A to B

>A is **mapping reducible** to B (A$\leq_{m}$B):
>
>- $\exists$ **computable function** f | w$\in$A $\leftrightarrow$ f(w)$\in$B
>- f is called **reduction** from A to B
>- Computable function: 
>  - $\exists$ TM M, on every input w, halts with f(w) on its tape
>  - "The following machine F computes a reduction f"



Theorem 5.22, 5.23, 5.28 and Corollary 5.29: 

- A$\leq_{m}$B and B is decidable   		$\rightarrow$ A is decidable (run D~B~ on f(w))
- A$\leq_{m}$B and A is undecidable   	$\rightarrow$ B is undecidable (contradiction ch5.1)
- A$\leq_{m}$B and B is recognizable  	$\rightarrow$ A is recognizable (run R~B~ on f(w))
- A$\leq_{m}$B and A is not recognizable$\rightarrow$ B is not recognizable (A~TM~$\leq_{m}$ not B)

- A$\leq_{m}$B $\iff$ $\overline{\text{A}}\leq_m\overline{\text{B}}$  (Corollary 5.29)

We can get

- A~TM~$\leq_{m} \overline{\text{B}} \rightarrow$ B is not recognizable (proof of Theorem 5.30)
- A~TM~$\leq_{m}$ B$\rightarrow$ $\overline{\text{B}}$ is not recognizable (proof of Theorem 5.30)

- A$\leq_{m}$B and A is neither  $\rightarrow$ B is neither



Transitive: A~TM~ $\leq$~m~ MPCP $\leq$~m~ PCP $\rightarrow$ A~TM~ $\leq$~m~ PCP

$A \leq_{m} B$ $\leftrightarrow$ $\overline{A} \leq_{m}\overline{B}$ 



Classic mapping reduction format: Example 5.24 (p236)

#### Descriptive/Kolmogorov Complexity: (section 6.4 lecture 5)

> A definition of information

Encoding of <M,w>

- by adding subtle poin/delimiter: |<M,w>| = 2|M| + |w| + 1 which could be smaller

Definition 6.23

- let x be binary string, the minimal description of x, written d(x), is the shortest string <M,w> where TM M on input w halts with x on its tape. If sevral suh string exist, select the lexicographically first among them.
- Kolmogorov complexity of x is K(x) = |d(x)|
  - Lec 5 hint: this is undecidable
  - K(x) is the amount of information in string x
  - d(x) is a description of x

Theorem 6.24, 6.25, 6.26, 6.27

- $\exists c \forall x \ [K(x) \leq |x| + c]$
  - M what halt on line1: K(x) <= |<M,x>| = 2|M| + |x| + 1 = |x| + c  (Let 5)
- $\exists c \forall x \ [K(xx) \leq K(x) + c]$
  - Lec Corollary: k((01)^n^)
- $\exists c \forall x,y \ [K(xy) \leq 2K(x) + K(y) + c]$
- $\forall x \ [K(x) \leq K_p(x) + c]$



x is c-compressible (definition 6.28)

- $K(x) \leq |x| - c$

- if x is not c-compressible -> x is incompressible by c
- if x is incompressible by 1 -> x is incompressible

Theorem 6.29 Corollary 6.30 Theorem 6.31, 6.32

- incompressible strings of every length exist
- at least 2^n^ - 2^n-c+1^ + 1strings of length n are incompressible by c
- let f be a computable ...
- for some constant b ...9

## Languages

### Decidable Languages 4.1

A~DFA~ = {<B,w> | B is a DFA that accepts input string w}

A~NDA~  = {<B,w> | B is an NFA that accepts input string w}

A~REX~ = {<R,w> | R is a regular expression that generates string w}

E~DFA~ = {\<A>   | A is a DFA and L(A) = ∅}

EQ~DFA~= {<A,B> | A and B are DFAs and L(A) = L(B)}

A~CFG~ = {<G,w> | G is a CFG that generates string w}

E~CFG~ = {\<G>   | G is a CFG and L(G) = ∅}

Every CFL (context-free language) is decidable

- Every CFL can be decided by an LBA.

A~LBA~ = {\<M,w> | M is an LBA that accepts string w}

- Similar to A~TM~, but LBA can have only a limited number of configurations respect to length of the input n
- LBA with q states and g symbols in tape alphabet, there are exactly qng^n^ distinct configurations of M for a tape of length n (LEMMA 5.8)

### Undecidable &rarr; Turing-recognizable

#### Reduction from A~TM~ (A~TM~$\leq_{m}$B $\rightarrow$ B is undecidable)

HALT~TM~

- Prove by reduction from A~TM~ Ch5.1(p219)



A~TM~ = {<M,w> | M is a TM and M accepts w}

- *Diagonalization* method
  - Set A and B are the **same size** if $\exist\ f:A→B\ |\ f$ is **one-to-one** and **onto**, $f$ is called a **correspondence**.

PCP = {\<P> | P is an instance of the Post Correspondence Problem with a match}
- A~TM~ $\leq$~m~ MPCP $\leq$~m~ PCP 			chapter 5.2
  - Textbook provides a idea of converting A~TM~ yes-instance into a PCP yes-instance instead of a formal mapping function
  - The book doesn't deliver a TM M that compute the mapping function f, but it's still contains the characteristics of mapping reduction
- MPCP create limited domino with valid configuration substring around q
- PCP force first domino to contains the inital configuration




### Undecidable &rarr; co-Turing-recognizable

Set of all L is uncountable, set of all TM is countable &rarr; $\exist$ L are not recongnized by any TM



DIAG = {\<M> | M is a TM, \<M> $\notin$ L(M)}
- Suppost $\exists $ M | L(M) = DIAG

### Undecidable (Neither)

EQ~TM~ = {\<M1, M2>| M1 and M2 are TMs and L(M1) = L(M2)}

- same prove as HALT~TM~, but building E~TM~
- Example 5.26 saying it's mapping reduction: E~TM~ $\leq_{m}$ EQ~TM~
- Theorem 5.30: neither
  - A~TM~ $\leq_{m}$ EQ~TM~
  - A~TM~ $\leq_{m}$ not EQ~TM~
- Lecture & TUT

### Undecidable (Not sure)

#### Reduction from A~TM~ (A~TM~$\leq_{m}$B $\rightarrow$ B is undecidable)

E~LBA~ = {\<M> | M is an LBA where L(M) = $\empty$}

- contruct a LBA B that determines if M,w have accepting computation history
- run decider of E~LBA~, R on \<B>, if rejects accept

ALL~CFG~ = {\<G>|G is a CFG and L(G) = Σ^∗^}

- same prove as E~LBA~

REGULAR~TM~ = {\<M> | M is a TM and L(M) is a regular language}

- this problem is the same as determining whether the TM recognizes a regular language
- same prove as HALT~TM~, with modifications on input M

E~TM~ = {\<M>|M is a TM and L(M) = $\empty$}

- same prove as HALT~TM~, with modifications on input M
- Google: not Turing recognizable
- Google: E~TM~ is co-Turing recognizable

#### Mapping Reduction



#### Other

EQ~CFG~= {<G,H> | G and H are CFGs and L(G) = L(P from Rice Theorem

- Example:
  - EMPTY~TM~ = {\<M>}
  - FINITE~TM~
  - DECIDABLE~TM~

## Machines

##### Some machine

H(<M,w>) 
- H = M~A~ depends on A~TM~

D(\<M>)
- NOT operator

QUINE

- program that prints its own source code (using recursion)
- Q(w):
  1. B <- code for step 2
  2. A <- code that prints var B
  3. C <- code that executes A then B
  4. print C

Fixed Points:

- F: $\Sigma^* → \Sigma^*$ 

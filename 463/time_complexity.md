## Time Complexity

#### Background:

| Computability                 | Complexity                             |
| ----------------------------- | -------------------------------------- |
| The decidable languages       | The class P                            |
| The recognizable languages    | The class NP                           |
| The co-recognizable languages | The class co-NP                        |
| Mapping reductions            | Polynomial Time Reduction              |
| The language HALT             | 3SAT $\leftrightarrow$ TQBF for Space? |

Millennium Problems recognized by the Clay Mathmatics Institute:

- Is P = NP $\cap$ co-NP? (no strong consensus)
- Is NP = co-NP? (strongly believed to be no)
- Is P = NP? (strongly believed to be no)



#### Polynomial Time Reducibility (p300) (polynomial time many–one reducibility)

> The efficient analog to mapping reducibility.  Other forms of efficient reducibility are available, but polynomial-time reducibility is enough to...

Prove a language are in **NP-Complete**?

When problem A is *efficiently* reducible to problem B means

- $\exists$ **polynomial time computable function** that converts instances of A to B
- an efficiently solution to B can be used to solve A efficiently

> A is **polynomial time reducible** to B (A$\leq_P$B):
>
> - $\exists$ **polynomial time computable function** f |  w$\in$A $\leftrightarrow$ f(w)$\in$B
> - f is called **polynomial time reduction** of A to B
>
> **Polynomial time computable function**: 
>
> - $\exists$ TM M, on every input w, halts with f(w) on its tape
> - "The following machine F computes a reduction f"



Theorem 7.31: 

- A$\leq_{P}$B and B $\in$ P  $\rightarrow$ A $\in$ P (Build polynomial time algo N deciding A)

Corollary

- A$\leq_{P}$B and B $\in$ NP  $\rightarrow$ A $\in$ NP
- A$\leq_{P}$B and A $\notin$ P  $\rightarrow$ B $\notin$ P 
- A$\leq_{P}$B and A $\notin$ NP  $\rightarrow$ B $\notin$ NP



#### Big-O Notation (Definition 7.2)

Let $f,g: \N \rightarrow \R^+$ be functions

- $f(n)=O(g(n))$: 

- $\exist c \in \R^+, \exist n_0 \in N, n \geq n_0 \rightarrow f(n) \leq cg(n)$

- $g(n)$ is an ***asymptotic upper bound*** for $f(n)$

#### Small-o Notation (Definition 7.5)

Let $f,g: \N \rightarrow \R^+$ be functions

- $f(n)=o(g(n))$: 

- $\forall c \in \R^+, \exist n_0 \in N, n \geq n_0 \rightarrow f(n) \leq cg(n)$
- same as $\lim_{n \to \infty} \frac{f(n)}{g(n)} = 0$

Example: $\sqrt n = o(n)$;	$nlogn = o(n^2)$;	$n^2 = o(n^3)$



#### TIME: Time Complexity Class (Def 7.7)

Let $t : \N \rightarrow \R^+$ be a function

- $TIME(t(n))$ = { L | L is a language decided by some TM that has worst-case time of $O(t(n))$ }

Example: $TIME(n^2)$ contains all languages that can be decided in $O(n^2)$ time

#### NTIME: Nondeterministic Time Complexity Class (Def 7.21)

Let $t : \N \rightarrow \R^+$ be a function

- $NTIME(t(n))$ = { L | L is a language decided by an $O(t(n))$ time nondeterministic TM }



#### P: Polynomial Time (Definition 7.12)

> **P** is the class of language that are decidable in polynomial time on a ***deterministic single-tape Turing machine***
>
> - $P = \bigcup_{k\in\N} TIME(n^k)$
> - Or multitape since they are polytime equivalent

Show L $\in$ P:

1. Provide polytime algorithm

Languages:

- PATH = { <G, s, t> | G is a directed graph that has a directed path from s to t}.

- RELPRIME = { <x, y> | x and y are relatively prime}.
  - relatively prime: if 1 is the largest integer that evenly divides them both.
- Every context-free language is a member of P
- COMPOSITES = { x | x = pq, for integers p, q > 1} = not Prime



#### NP: Nondeterministic Polynomial Time (Definition 7.19)

> **NP** is the class of language that are decidable in polynomial time on a ***NTM*** (Corollary 7.22)
>
> - $NP = \bigcup_{k\in\N} NTIME(n^k)$
>
> L $\in$ **NP** $\leftrightarrow \exist$ ***nondeterministic polynomial time TM*** decides L (Theorem 7.20)
>
> - Prove: polytime verifier $\xleftrightarrow{convert}$ polynominal time NTM

> **NP** is the class of languages that have ***polynomial time (P) verifiers*** (Definition 7.19)
>
> **Verifier** for a language A is an algorithm V, where
>
> - A = { w | V accepts <w,c> for some string c}
>
> - **Polynomial time verifier** runs in *polynomial time* (P) in the length of w.
> - A language A is **polynomially verifiable** if it has a polynomial time verifier.

Show L $\in$ NP:

1. Show that L is a decision problem (1 line sentence)
2. Give a certificate for L ($C_x$)
3. Show that certificate is polynomial in the input size
4. Give a verifier for the certificate (deterministic TM in P)
5. Show the verifier is polytime in the input size

**Languages** (No P slover yet / not known to be in P):

- HAMPATH = { <G, s, t> | G is a directed graph with a Hamiltonian path from s to t}



#### NP-COMPLETE (7.4)

B $\in$ **NP-complete** : (Definition 7.34)

1. B $\in$ NP
2. $\forall$ A $\in$ NP, A $\leq_P$ B  Note: A is harder than B ?
   - Prove B is NP-hard by showing 3SAT $\leq_P$ B
   - *NP-hard*: B could $\notin$ NP

Hardest problems in NP:

- They have **same hardness**: If a polynomial time algorithm exists for any of these problems, all problems in NP would be polynomial time solvable.

- B $\in$ NP-complete and B $\in$ P:  (Theorem 7.35)
  - P = NP
  - Example: SAT $\in$ P $\leftrightarrow$ P = NP (Theorem 7.27)
- B $\in$ NP-complete and B $\leq_P$ C for C $\in$ NP (Theorem 7.36)
  - C $\in$ NP-complete

##### Languages:

- SAT = { <$\phi$> | $\phi$ is a satisfiable Boolean formula} = satisfiability problem

  - ***Cook-Levin Theorem***: 

    > SAT is NP-complete (Theorem 7.37), is a natural NP-complete problem

    1. Show that SAP is in NP
    2. Show $\forall$A$\in$NP, A $\leq_P$ SAT

- 3SAT =  { <$\phi$> | $\phi$ is a satisfiable 3cnf-formula} (Corollary 7.42)

  - SAT $\leq_P$ 3SAT
  - To prove A is NP-complete, we usually use 3SAT $\leq_P$ A
    - gadgets:  structures in A that can simulate the variables and clauses in Boolean formulas, usually mimic variables and clauses.
    - General setup for creating variable gadgets and clause gadgets:
      - define 3cnf-formula $\phi$ containing k **clauses** and $l$ **variables**
      - $\phi = (a_1 \or b_1 \or c_1) \and (a_2 \or b_2 \or c_2) \and ... \and(a_k \or b_k \or c_k)$
      - where each a,b, and c is a **literal** $x_i$ or $\overline{x_i}$
      - let $x_1,...,x_l$ be the $l$ variables of $\phi$
  - Example: 
    - $(x1 \or \overline{x2} \or \overline{x3}) \and (x3 \or \overline{x5} \or x6) \and (x3 \or \overline{x6} \or x4) \and (x4 \or x5 \or x6)$
    - If an assignment satisfies a *cnf-formula*, each *clause* must contain at least one *literal* that evaluates to 1

- CLIQUE = { <G, k> | G is an undirected graph with a k-clique}

  - Theorem 7.32 3SAT $\leq_p$ CLIQUE $\rightarrow$ Corollary 7.43: CLIQUE is NP-complete
  - clique in an undirected graph is a subgraph, wherein every two nodes are connected by an edge. 
  - k-clique is a clique that contains k nodes.
  - Has $\in NP$ proof on book: Validate certificate in P;    Slove in NP

- VERTEX-COVER =  {<G, k> | G is an undirected graph that has a k-node vertex cover}

  - a vertex cover of G is a subset of the nodes where every **edge** of G touches one of those nodes
  - 3SAT $\leq_p$ VERTEX-COVER
  - INDEPENDENT-SET (373W10):
    - Independent Set $\leq_p$ Vertex Cover
    - $\overline{\text{VERTEX-COVER}}$ = INDEPENDENT-SET
    - S is a vertex cover iff V\S is an independent set

  - SET-COVER (373W10):
    - Vertex Cover $\leq_p$ Set Cover
    - Input: <Universe of elements U, family of Subsets S, integer k>
    - Q: Do there exist k sets from S whose union is U?
    - U = {1,2,3,4,5,6,7}, S= {{1,3,7},{2,4,6},{4,5},{1},{1,2,6}}, k = 3 yes, k = 2 no

- HAMPATH = whether the input graph contains a path from s to t that goes through every node exactly once.

  - 3SAT $\leq_p$ HAMPATH
  - Complex, does this covered in lec?
  - UHAMPATH = undirected version of the Hamiltonian path problem
    - HAMPATH $\leq_p$ UHAMPATH

- SUBSET-SUM = { <S, t> | S = {$x_1,..., x_k$}, and for some {$y_1,..., y_l$} $\subseteq$ {$x_1,...,x_k$}, we have $\sum{y_i} = t$ }

  - 3SAT $\leq_p$ SUBSET-SUM (Theorem 7.56)
  - S and it's subset are multisets: allow repetition of elements
  - Complex, does this covered in lec?



#### co-NP: something (Page 297)

> $L \in$ co-NP $\iff$ $\overline{L} \in $ NP

**co-NP** contains the languages that are complements of languages in NP. 

- We don’t know whether coNP is different from NP.



#### Not in P and Not in NP

- $\overline{\text{HAMPATH}}$
  - No P slover yet -> not in P
  - No P verifier yet -> not in NP
- $\overline{\text{CLIQUE}}$
  - Verifying not present is more difficult than verifying that it is present
- $\overline{\text{SUBSET-SUM}}$
  - Verifying not present is more difficult than verifying that it is present



#### TMs Formalisms Matter

Let $t(n) \geq n$ be a function

##### Single-tape vs Multitape: Polynomial Difference

- $\forall$ $t(n)$ time *multitape TM* has an equivalent $O(t^2(n))$ time *single-tape TM*

##### Deterministic vs Nondeterministic: Exponential Difference

- $\forall$ $t(n)$ time *nondeterministic single-tape TM* has an equivalent $2^{O(t(n))}$ time *deterministic single-tape TM*

#### Unary Notation ( input n vs loop n ):

- The magnitude of a number represented in binary, or in any other base k notation for $k\geq2$, is exponential in the length of its representation. (Page 289)
  - input binary(100) v.s. loop 100 times are in EXP
  - input unary(100) v.s. loop 100 times are in P

- Unary notation for encoding numbers (as in the number 17 encoded by the unary string 11111111111111111) isn’t reasonable because it is exponentially larger than truly reasonable encodings, such as base k notation for any $k\geq2$. (Page 287)

#### Attributes

##### Class:

- P = the class of languages for which membership can be decided quickly.

- NP = the class of languages for which membership can be verified quickly.
- We loosely refer to polynomial time solvable as solvable “quickly.”
- Researchers also have tried proving that the classes P&NP are unequal, but that would entail showing that no fast algorithm exists to replace brute-force search.
- We can prove $NP \subseteq EXPTIME = \bigcup_k TIME(2^{n^k})$ (Page 298)

##### TM:

##### $nlog(n)$ is lower bound for single-tape deterministic TM (Problem 7.49)

- $\forall$ langueage can be decided in $o(n log (n))$ time on a single-tape TM is regular (Page 281)
  - Prove L is not regular and provide a $nlog(n)$ decider, then we can conclude it's best running time 

- $\forall$ *non-regular language* will need at least $\Omega(nlog(n))$ time on a *single-tape deterministic TM* 
- Usage: `The solution to Problem 7.49 implies that no single-tape TM can do it more quickly`

##### $n$ is lower bound for multi-tape deterministic TM

- need at least $\Omega(nlog(n))$ time to read the input

##### Graph:

In reasonable graph representations, the size of the representation is a polynomial in the number of nodes.

- $m < n^2 \rightarrow O(mn) = O(n^3)$





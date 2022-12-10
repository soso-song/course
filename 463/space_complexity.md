## Space Complexity

L $\subseteq$ NL=coNL $\subseteq$ P $\subseteq$ NP $\subseteq$ PSPACE=NPSPACE $\subseteq$ EXP



Proved:

- NL $\neq$ PSPACE Corollary 9.6
  - coNL $\neq$ P
  - P  $\neq$  PSPACE
- L$\neq$ PSPACE
- P $\neq$ EXP

Havent Prove:

- 3SAT $\notin$ NL



#### SPACE: (Deterministic) Space Complexity Class (Def 8.2)

> M is deterministic TM that halts on all inputs. The space complexity of M is the function f : N−>N, where f(n) is the maximum number of tape cells that M scans on any input of length n. If the space complexity of M is f(n), we also say that M runs in space f(n)

Let $f : \N \rightarrow \R^+$ be a function

- $\text{SPACE}(f(n))$ = { L | L is a language decided by an $O(f(n))$ space deterministic TM }
- $\text{SPACE}$ closed under complement (Page 336): A in SPACE then not A also in SPACE

Example: $\text{SPACE}(n^2)$ contains all languages that can be decided in $O(n^2)$ space

#### NSPACE: Nondeterministic Space Complexity Class (Def 8.2)

> M is nondeterministic TM wherein all branches halt on all inputs, we define its space complexity f(n) to be the maximum number of tape cells that M scans on any branch of its computation for any input of length n.

Let $f : \N \rightarrow \R^+$ be a function

- $\text{NSPACE}(f(n))$ = { L | L is a language decided by an $O(f(n))$ space nondeterministic TM }



#### PSPACE: (Deterministic) Polynomial Space (Definition 8.6)

> **PSPACE** is the class of language that are decidable in polynomial space on a ***deterministic Turing machine***
>
> - $PSPACE = \bigcup_{k\in\N} SPCAE(n^k)$

Show L $\in$ PSPACE:

- Provide polynomial space slover/decider

Languages:

- SAT: 
  - SPACE(n): linear space
  - evaluate $\phi$ for each truth ass x1~xm (NP-complete) 
  - Store: only current truth assignment <= |m| = number of variables
  - O(m) = O(n) space
- $\overline{\text{ALL}_{NFA}}$
  - NSPACE(n): nondeterministic linear space
  - Run all string with length $2^q$ to conver every states in A
  - Store: location of markers <= one?, loop counter <= $2^q$
  - Time: O(n), not O(logn)?
  - Not known to be in NP or coNP
- $\text{ALL}_{NFA}$ = { ⟨A⟩| A is an NFA and L(A) = Σ∗}.
  - coNSPACE(n) $\rightarrow$ SPACE($n^2$) beacuase $\overline{\text{ALL}_{NFA}}$ in NPSPACE and 
  - Savitch's Theorem & the deterministic space complexity classes are closed under complement



#### NPSPACE: Nondeterministic Polynomial Space

> NPSPACE = PSPACE by virtue of Savitch’s theorem because the square of any polynomial is still a polynomial 



#### PSPACE-COMPLETE (8.3)

> B $\in$ **PSPACE-complete**:
>
> 1. B $\in$ PSPACE
> 2. $\forall$ A $\in$ NP, A $\leq_P$ B  Note: A is harder than B ?
>
> *PSPACE-hard*: If B merely satisfies condition 2

Show L $\in$ PSPACE-COMPLETE:

- Prove from lowest level: configuration
- Example: TQBF

**Languages:**

- TQBF ={ ⟨$\phi$⟩| $\phi$ is a true fully quantified Boolean formula
  - example: $\phi = \forall x \exists y [(x\or y)\and (\not x \or \not y)]$
  - $\in$ PSPACE: 2 recursion to remove $\exists$ and $\forall$
  - PSPACE-hard: 



## 8.3 PSPACE-completeness

##### SPACE

PSAPCE-complete: hardest questions in PSPACE

##### Fully quantified boolean formula (TQBF)

$\forall x [x]$ is not 

SAT is special case where all quantifiers are $\exists$

TAUT .... $\forall$

SAT <=p TQBF

TQBF is PSPACE-complete

Proof:

1. in PSPACE
   - reuse phi, T desides TQBF: space used = O(m)
2. PSPACE-hard
3. m1,c3,c4 -> n^k + n^k +.... = $n^{2k}$

##### NO GAME?



### Savitch's Theorem

$\forall f : \N \rightarrow \R^+$, where $f(n) \geq n$ 

$\text{NSPACE}(f(n)) \subseteq \text{SPACE}(f^2(n))$

Use CANREACH/CANYIELD

- Size of a node: O(f(n)) 
- Depth: log t = O(f(n))
  - $f(n)2^{dO(f(n))}$ max different configurations using f(n) tape
    - LEMMA5.8: M be an (linear bounded automata) LBA with q states and g symbols in the tape alphabet. There are exactly $qng^n$ distinct configurations of M for a tape of length n 
  - t = $2^{dO(f(n))}$ max time that nondeterministic machine may use on any branch using f(n) tape
  - d=3 expanding digite of each cell to 000,001, to repersent Tape Alphabet, 
- Simulate an f(n) space NTM deterministically: Deepest path = O($f^2(n)$)







##### 



## 8.4 The Classes L and NL

PATH in NL but not sure if its in L (since we dont know NL=L)

- start on s and nondeterminitly write next vertex and check if its connected, remove previous vertex, only store 2 vertex.
- PATH is NL-complete

NL-complete

- A in NL
- A is NL-hard **iff**
  - (for all B in NL, B $\leq_L$ NL) log space reduction
  - output of this mapping function will be poly length

NL is subset of P

- we can create all configuation of NL in poly time
- if more than polytime, means some configuration repeats -> loop

B in NL, B $\leq_L$ A in L

- then B in L

- not simple, compute individual symbols of f(w)...

PATH is in NL-complete

- construct graph, check if there path from cstart to caccept










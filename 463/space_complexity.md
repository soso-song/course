## Space Complexity

#### SPACE: Space Complexity Class (Def 8.2)

> M is deterministic TM that halts on all inputs. The space complexity of M is the function f : N−>N, where f(n) is the maximum number of tape cells that M scans on any input of length n. If the space complexity of M is f(n), we also say that M runs in space f(n)

Let $f : \N \rightarrow \R^+$ be a function

- $\text{SPACE}(f(n))$ = { L | L is a language decided by an $O(f(n))$ space deterministic TM }

Example: $\text{SPACE}(n^2)$ contains all languages that can be decided in $O(n^2)$ space

#### NSPACE: Nondeterministic Space Complexity Class (Def 8.2)

> M is nondeterministic TM wherein all branches halt on all inputs, we define its space complexity f(n) to be the maximum number of tape cells that M scans on any branch of its computation for any input of length n.

Let $f : \N \rightarrow \R^+$ be a function

- $\text{NSPACE}(f(n))$ = { L | L is a language decided by an $O(f(n))$ space nondeterministic TM }



### Savitch's Theorem

$\forall f : \N \rightarrow \R^+$, where $f(n) \geq n$ 

$\text{NSPACE}(f(n)) \subseteq \text{SPACE}(f^2(n))$

Proof:

- Branch uses $f(n)$ space may run for $2^{O(f(n))}$ space
-  





### Linear Space:

- SAT (NP-complete)
  - evaluate $\phi$ for each truth ass x1~xm
  - Store: only current truth assignment <= |m| = number of variables
  - O(m) = O(n) space

### Nondeterministic Linear Space:

- $\overline{\text{ALL}_{NFA}}$ = { ⟨A⟩| A is an NFA and L(A) = Σ∗}.
  - Run all string with length $2^q$ to conver every states in A
  - Store: location of markers <= one?, loop counter <= $2^q$
  - Time: O(n), not O(logn)?
  - Not known to be in NP or coNP





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

##### NO GAME



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










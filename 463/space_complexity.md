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

#### TIME vs SPACE:

- TIME(t(n)) $\subseteq$ SPACE(t(n))
- SPACE(t(n)) $\subseteq$ TIME($2^{O(t(n))}$) = $\bigcup_c$ TIME($c^{t(n)}$)

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

- $LADDER_{DFA}$ = { ⟨B,u,v⟩ | B is a DFA and L(B) contains a ladder $y_1,y_2,...,y_k$ where $y_1 = u$ and $y_k=v$  }

  - $\in$ NPSPACE, NSPACE(n) by simple Nondeterministically scan all possible y

    - Repete t = $|\Sigma|^{|u|}$ times

  - $\in$ SPACE(n^2) by similar proof of Savitch's Theorem, t/2 thing

  - ##### TAKE NOTE ABOUT BOTH ALGOS= {classic NPSPACE & classic PSPACE}



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

  > SAT is special case where all quantifiers are $\exists$

  - example: $\phi = \forall x \exists y [(x\or y)\and (\not x \or \not y)]$
  - $\in$ PSPACE: 2 recursion to remove $\exists$ and $\forall$
  - PSPACE-hard:

- NO GAME?

##### 

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





## The Classes L and NL

> Log space: can only write pointers?
>
> need introduce new model since input has n space

Model: 2-tape TM with read-only input tape for defining sublinear space computation

1. read-only input tape of size n
2. read/write work tape of size O(logn)



#### L: Logarithmic Space

> L is the class of languages that are decidable in logarithmic space on a deterministic TM
>
> L = SPACE(logn)

**Languages:**

- Palindrome = { ww^R | w $\in \Sigma^*$ }
  - Work tape store 2 pointers at both side
- A = { $0^k1^k$ | k $\geq$ 0 }

##### Relation:

L $\subseteq$ P

- M is decider of A in **space** O(logn)
- A configuration for M on w is ($q, p_1, p_2, t$) = (state, tape head positions, tape content)
- number of configurations is |Q| * n * O(logn) * $d^{O(log(n))}$ = O($n^k$) for some k
- Therefore M runs in polynomial **time**



#### NL: Nondeterministic Logarithmic Space

> NL is the class of languages that are decidable in logarithmic space on a deterministic NTM
>
> NL = NSPACE(logn)

**Languages:**

- 

##### Relation:

NL $\subseteq$ SPACE($log^2n$)

- Savitch's theorem works for log space

NL $\subseteq$ P

- NTM M is decider of A in **space** O(logn)
- Computation/configuration graph $G_{M,w}$ for M on w has
  - nodes: all config for M on w
  - edges: edge from $c_i \rightarrow c_j$ if $c_i$ can yield(reach) $c_j$ in 1 step
- Claim: M accepts w iff $G_{M,w}$ has a path from $c_{start}$ to $c_{accept}$
- $\exists$ Polynomial time algo T for A, "on input w
  1. Construct the $G_{M,w}$
  2. Accept if there is a path from  $c_{start}$ to $c_{accept}$, reject if not
- Therefore M runs in polynomial **time** and every problem in NL seems like PATH problem





#### Log-space reducibility ($\leq_L$)

> if we use $\leq_P$, all languages in P are reducible to each other
>
> Define a new notion of reducibility thats weaker than the class:

**log-space transducer** (deterministic) is a TM with three tapes that computes f:

1. read-only input tape of size n
2. read/write work tape of size O(logn)
3. write-only output tape stores f(n) (poly length)
   - f(n) is at most polynomial in n because transducer can only run polynomial number of steps without having loop

**log-space reducible** $\leq_L$:

- $A \leq_L B$ if $A \leq_m B$ by a reduction function that is computable in log-space

##### Theorem:

A $\leq_{L}$ B and A $\in$ NL  $\rightarrow$ B $\in$ L ??

- then B in L

- not simple, compute individual symbols of f(w)...

A $\leq_{L}$ B and B $\in$ L  $\rightarrow$ A $\in$ L

- Old prove not work now:
  - TM for A = "On input w, 
    1. compute f(w)
    2. run decider for B on f(w), output same"
  - Not working this time beacue f(w) from output tape could not able to store on log space memory.
- New prove:
  - Don't wait line1 finish
  - re-compute symbols of f(w) as needed by repeating running transducer so we only compute/store a digit from f(w) when we need



#### NL-complete

NL-complete

1. B in NL
2. for all A in NL, A $\leq_L$ NL

> A is NL-hard?

**Languages:**

- PATH  = { <G, s, t> | G is a directed graph that has a directed path from s to t}

  > PATH is like 3SAT for NP-complete

  1. $\in$ NL: Work tape store/tracks current node on the guessed path

  2. Let A in NL be decided by NTM M in space O(logn)

     > merge accept states by erase work tape, move heads to left end upon accepting
     >
     > so it's still PATH problem not exists path problem

     - Give log-space reduction f mapping A to PATH:
     - T = "on input w
       1. for all pairs ci, cj of config of M on w
       2. ​    Output paires which are legal moves for M
       3. Output $c_{start}$ and $c_{start}$"
     - Then T's output tape f(w) = <G,s,t> = <$G_{M,w}, c_{start},c_{accept}$>
     - And w in A iff G has path from s to t

- $\overline{2SAT}$
  1. show in NL
  2. show PATH $\leq_L \overline{2SAT}$
     - Give log-space reduction f from PATH to $\overline{2SAT}$, f(<G,s,t>) = <$\phi$>
     - for each node u in G put a variable $x_u$ in $\phi$
     - for each edge (u,v) in G, put a clause $(x_u \rightarrow x_v)$ in $\phi$ [equivalent to $(\bar x_u \or x_v)$]
     - in addition put the clauses $(x_s \or x_s)$ and $(x_t \or \bar x_s)$ in $\phi$
     - Show G has an path from s to t iff $\phi$ is unsatifiable
       - $\rightarrow$ follow implications to get contradiction
       - $\leftarrow$ if G has no path from s to t, assign all $x_u$ TRUE where u is reachable from s, and all other variable FALSE, that gives a satisfying assignment to $\phi$



#### NL = coNL

> Followed Lec: https://www.youtube.com/watch?v=vqFRAWeEcUs
>
> NTM can't flip answers
>
> PATH in NL-complete $\rightarrow$ $\overline{PATH}$ in coNL-complete

Show $\overline{PATH} \in NL$ $\rightarrow$ NL = coNL

> Definition: NTM M computes function f:$\Sigma^* \rightarrow \Sigma^*$ if for all w
>
> 1. all branches halt with f(w) on the tape or reject
> 2. some branch of M on w does not reject

##### Define:

Let f = haspath(G,s,t) = YES, if G has a path from s to t; NO otherwise

Let R = R(G,s) = { u| haspath(G,s,u) = YES } = set of reachable nodes from s

Let c = c(G,s) = |R| = number of reachable nodes from s

##### Theorem: if some NL-machine computes haspath(G,s,t), then some NL-machine computes c

Define C: "On input <G,s>

1. let k = 0
2. for each node u
3. ​    if HASPATH(G,s,u) = YES, then k+=1     [HASPATH is NL-machine computes haspath]
4. Output k"

##### Theorem: if some NL-machine computes c, then some NL-machine computes haspath

Define HASPATH: "On input <G,s,t>

1. compute c
2. k = 0
3. for each node u
4. ​    nondeterministically go to (p) or (n)    [guess one of it, p:hadpath, n:nopath]
5. ​        (p) Nondeterministically pick a path from s to u of length $\leq$ m = num of nodes [in some order]
6. ​            if fail, reject      [not reachable or there is path but wrong guess]
7. ​            if u = t, output YES, else set k = k + 1
8. ​        (n) Skip u and continue    [?]
9. if k $\neq$ c, reject   [pervent other branches output NO when t is reachable. since reach here means you found all the c numbers of reachable nodes, and we didnt output YES, means t is not in c numbers of reachable node]
10. Output NO." [found all c reachable nodes and none were t]

##### Theorem: if some NL-machine computes <font color="red">cd</font>, then some NL-machine computes <font color="red">haspathd</font>

Let haspathd(G,s,t) = YES, if G has a path from s to t of length $\leq$ d; NO otherwise

Let Rd = Rd(G,s) = { u| haspathd(G,s,u) = YES } = set of reachable nodes from s

Let cd = cd(G,s) = |R| = number of reachable nodes from s

Define HASPATH: "On input <G,s,t>

- compute <font color="red">cd</font>
- k = 0
- for each node u
- ​    nondeterministically go to (p) or (n)    [guess one of it, p:hadpath, n:nopath]
- ​        (p) Nondeterministically pick a path from s to u of length $\leq$ <font color="red">d</font> = num of nodes
- ​            if fail, reject      [not reachable or there is path but wrong guess]
- ​            if u = t, output YES, else set k = k + 1
- ​        (n) Skip u and continue
- if k $\neq$ <font color="red">cd</font>, reject
- Output NO." [found all <font color="red">cd</font> reachable nodes and none were t]

##### Theorem: if some NL-machine computes cd, then some NL-machine computes haspathd<font color="red">+1</font>

Let haspathd(G,s,t) = YES, if G has a path from s to t of length $\leq$ d; NO otherwise

Let Rd = Rd(G,s) = { u| haspathd(G,s,u) = YES } = set of reachable nodes from s

Let cd = cd(G,s) = |R| = number of reachable nodes from s

Define $HASPATH_{d+1}$: "On input <G,s,t>

- compute cd
- k = 0
- for each node u
- ​    nondeterministically go to (p) or (n)    [guess one of it, p:hadpath, n:nopath]
- ​        (p) Nondeterministically pick a path from s to u of length $\leq$ d = num of nodes
- ​            if fail, reject      [not reachable or there is path but wrong guess]
- ​            if u <font color="red">has an edge to</font> t, output YES, else set k = k + 1
- ​        (n) Skip u and continue
- if k $\neq$ cd, reject
- Output NO." [found all cd reachable nodes and none were t]

##### Corollary: Some NL-machine computes $c_{d+1}$ from $c_d$

Hence $\overline{PATH} \in NL$ 

"On input <G,s,t>

1. $c_0$ = 1
2. Compute each $c_{d+1}$ from c_d for d=1 to m
3. Accept if HASPATHm(G,s,t) = NO
4. Reject if HASPATHm(G,s,t) = YES"


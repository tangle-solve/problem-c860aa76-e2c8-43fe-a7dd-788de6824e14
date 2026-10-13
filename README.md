<!-- solve-problem:c860aa76-e2c8-43fe-a7dd-788de6824e14 -->
# Separating words problem

A [Tangle Solve problem](https://solve.tangle.tools/problems/c860aa76-e2c8-43fe-a7dd-788de6824e14).

## What is the problem?

Given two distinct strings $x, y \in \Sigma^n$ over a finite alphabet (classically $\{0,1\}$), how many states are sufficient — and necessary — in a deterministic finite automaton (DFA) that **separates** them, i.e., accepts one and rejects the other? Define $f(n)$ = the maximum, over all pairs of distinct length-$n$ strings, of the minimum number of states in a DFA separating them. Trivially $f(n) \le n+2$ (a DFA can simply remember the first position where $x$ and $y$ differ). The problem is to determine $f(n)$ asymptotically. It is widely conjectured that $f(n) = o(n)$ — indeed possibly $f(n) = (\log n)^{O(1)}$ or even $O(\log n)$ — but no superconstant lower bound beyond $f(n) = \Omega(\log n)$ (from counting: DFAs with $s$ states induce only $2^{\Theta(s \log s)}$ distinct behaviors on length-$n$ inputs) is known. The gap between $\Omega(\log n)$ and $O(n)$ is the open problem.

## Why does it matter?

Resolving it would resolve a long-standing question in formal language theory and automata minimization, connecting to circuit lower bounds and randomness extraction: separating automata are equivalent to certain small-depth randomized/deterministic decision procedures, and progress would illuminate the power of small automata, with implications for streaming algorithms and space complexity of one-pass string problems. The lower-bound side would be the first nontrivial automata lower bound technique beyond counting; the upper-bound side (a $O(\log n)$ construction) would likely involve elegant number-theoretic hashing of strings.

## What's already known?

- **Upper bound:** Robson (1996) proved $f(n) = O(n^{2/5} \log n)$ (verify the exact exponent/term), improving on earlier $O(n)$ trivial and $O(n/\log n)$-type bounds. His construction uses random DFAs based on arithmetic progressions of positions, analyzed via the probabilistic method.
- **Lower bound:** Only $f(n) = \Omega(\log n)$, by counting (a simple information-theoretic argument; folklore, also in Goralčík–Koubek).
- Goralčík and Koubek (1986) introduced the problem and proved $f(n) = O(n/\log n)$-type bounds (verify).
- The problem is hard because candidate separating DFAs must work for *worst-case pairs*, and known constructions (e.g., DFAs computing hash functions like $\sum i \cdot x_i \bmod p$) fail on adversarial pairs; proving any $f(n) = \omega(\log n)$ would require beating the counting bound with structural arguments, and no such technique exists.

## What would count as solving it?

Any of:
1. **Upper bound:** a proof that $f(n) = o(n^{2/5})$, ideally $f(n) = (\log n)^{O(1)}$; a referee would accept an explicit construction + proof that for every distinct pair $x,y$ some DFA from the family separates them.
2. **Lower bound:** a proof that $f(n) = \omega(\log n)$ — even $f(n) \ge \log^2 n$ for infinitely many $n$ — via an explicit pair of strings hard to separate.
3. **Resolution:** matching upper and lower bounds.

## How to start

1. Read the Wikipedia "Separating words" article and Robson (1996) for the best upper bound; understand why arithmetic-progression-based random DFAs give $n^{2/5}$-ish bounds.
2. Try small-$n$ computational experiments: for random and adversarial pairs of length-$n$ binary strings, compute the minimum separating DFA size (via SAT/ILP encodings); look for structure in hard pairs.
3. For lower bounds, attempt to construct hard pairs resistant to "linear-form modulo $p$" separators — this is where previous attempts stall, so characterizing which pairs these DFA families separate may reveal the frontier.
4. Main obstacle: no known technique converts structure of all small DFAs into a hard pair; counting is the only tool and it caps at $\log n$.

## Key references

- J. M. Robson, "Separating strings with small automata," *Information Processing Letters*, 1996. Proves the best known upper bound $f(n) = O(n^{2/5}\log n)$ using probabilistic constructions over arithmetic progressions. (verify exact statement)
- P. Goralčík, V. Koubek, "On discerning words by automata," *ICALP/Theoretical Computer Science*, 1986. Origin of the problem; gives early sublinear/related bounds. (verify)
- Wikipedia, "Separating words problem," https://en.wikipedia.org/wiki/Separating_words_problem — survey of the problem statement, bounds, and connection to randomness. (verify current bound values)

## Warnings

- The exact exponents in Robson's bound are frequently misquoted; verify against the paper before building on it.
- Easy trap: a separator only needs to differ on the two strings, not accept the language $\{x\} \setminus \{y\}$ — accepting "first differing bit" gives $n+2$, not $2n$.
- The counting lower bound $\Omega(\log n)$ is tight in the number of *behaviors*, not necessarily achievable; don't conflate the two.
- The problem is usually stated for binary alphabets; larger alphabets change constants only, but confirm the convention used in any cited bound.

---
*`ALGO-000226` · unverified*

## Acceptance guidance

Any of:
1. **Upper bound:** a proof that $f(n) = o(n^{2/5})$, ideally $f(n) = (\log n)^{O(1)}$; a referee would accept an explicit construction + proof that for every distinct pair $x,y$ some DFA from the family separates them.
2. **Lower bound:** a proof that $f(n) = \omega(\log n)$ — even $f(n) \ge \log^2 n$ for infinitely many $n$ — via an explicit pair of strings hard to separate.
3. **Resolution:** matching upper and lower bounds.

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/c860aa76-e2c8-43fe-a7dd-788de6824e14?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000226.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000226)

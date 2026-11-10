# Introduction to Algorithm Design — Outline Notes (IGNOU BCA)

Nov 6, 2026 · @x

## How these notes work: the outline method

The outline method writes notes as a ladder of ideas: the big topic sits at the left edge, and each smaller idea is pushed a step to the right underneath the idea it belongs to ([e-student guide](https://e-student.org/outline-note-taking-method/)). One glance at the indentation tells you what is a main idea and what is a detail.

- **A. What it is**
  - A hierarchy, from general to specific.
    - Level 1: main topic (left margin).
    - Level 2: sub-topic (one step in).
    - Level 3: supporting facts, examples, formulas (two steps in).
  - Each level is marked with letters, numbers or bullets so you never lose your place.
- **B. The six steps of the method**
  1. Gather your materials (notebook, pen, the syllabus).
  2. Write the few main topics at the left margin.
  3. Indent the sub-topics under each one.
  4. Add supporting facts and your own thoughts under each sub-topic.
  5. Add details and examples in short phrases, symbols and abbreviations.
  6. Review within 24 hours, then again before the exam.
- **C. Why it suits exam revision**
  - You see how small points connect to big ideas.
  - Every heading can be turned into a likely exam question.
  - Notes stay short, so revision is fast.
- **D. Its known weak spot, and how these notes handle it**
  - Outlines are weaker for maths-heavy subjects, where formulas and worked steps matter more than the hierarchy.
  - So here, every formula, trace table and worked example sits directly under the point it explains. You get the outline's structure plus the full working you need in the exam.
- **E. How to read each topic below**
  - The heading shows how many of the 8 past exams asked it, e.g. (8/8). Topics are in that order, most frequent first.
  - **Bold letters (A, B, C…)** are the main ideas of the topic.
  - Indented bullets are the supporting points; deeper bullets are details and examples.
  - **Exam tip** lines say what examiners usually want written.
  - Start with the "Before you begin" section if you have never studied computers. It explains every word the later topics use.

## Before you begin: words and maths you will need

Every later topic uses the ten ideas below, so learn these first; none needs any computer knowledge.

- **A. Computer and program**
  - A computer is a machine that follows instructions exactly, very fast, with no common sense.
  - A program is a set of instructions written for a computer.
- **B. Algorithm**
  - An algorithm is a step-by-step recipe for solving a problem.
    - Example: making tea. Boil water → add tea leaves → add milk and sugar → boil 2 minutes → strain.
  - A program is just an algorithm written in a language the computer understands.
- **C. Input, output and n**
  - Input = what you give the algorithm (e.g. a list of numbers).
  - Output = what it gives back (e.g. the same list, sorted).
  - **n** = the size of the input (e.g. how many numbers are in the list). Everything in this subject is measured against n.
- **D. Array (a list of boxes)**
  - An array is a row of numbered boxes, each holding one value.
    - A = \[7, 3, 9, 1\] means A\[1\] = 7, A\[2\] = 3, A\[3\] = 9, A\[4\] = 1.
  - The box number is called the **index**. (Some books count from 0 instead of 1; both are fine if you are consistent.)
- **E. Basic operation and "step"**
  - The single action an algorithm repeats most: a comparison (is 5 > 3?), an addition, a multiplication or a swap.
  - "Analysing" an algorithm mostly means counting how many times this action happens.
- **F. Pseudocode**
  - Pseudocode is algorithm-writing in plain, code-like English. No real programming language needed.
    - `x ← 5` means "store 5 in the box named x".
    - `for i ← 1 to n` means "repeat the next lines with i = 1, then 2, … up to n".
    - `while (condition)` means "keep repeating as long as the condition is true".
    - `if … then … else` means "choose what to do".
- **G. Recursion**
  - A recursive algorithm solves a problem by calling itself on a smaller version of the same problem.
    - Example: factorial. 5! = 5 × 4!, and 4! = 4 × 3!, … down to 1! = 1, where it stops.
  - The stopping point is called the **base case**. Without it, the recursion never ends.
- **H. Powers and logarithms**
  - Power: 2³ = 2 × 2 × 2 = 8.
  - Logarithm is the reverse question: "2 raised to what gives 8?" Answer 3, so log₂ 8 = 3.
  - Easy meaning: **log₂ n = how many times you can halve n before reaching 1.**
    - log₂ 16 = 4 (16 → 8 → 4 → 2 → 1).
    - log₂ 1,000,000 ≈ 20. A million halves to 1 in only about 20 steps. Remember this; it is why binary search is so fast.
  - In this subject, "log n" means log₂ n unless stated otherwise.
- **I. Other symbols**
  - n! (n factorial) = 1 × 2 × 3 × … × n. Example: 4! = 24.
  - ⌊x⌋ (floor) = round down. ⌊7.8⌋ = 7, ⌊9/2⌋ = 4.
  - m mod n = the remainder when m is divided by n. 17 mod 5 = 2.
  - ∞ = infinity, used to mean "not known yet / unreachable".
- **J. Two sums you will meet again and again**
  - 1 + 2 + 3 + … + n = n(n + 1)/2. Example: 1 + 2 + 3 + 4 = 10 = 4 × 5 / 2.
  - 1 + 2 + 4 + … + 2^(k−1) = 2^k − 1. Example: 1 + 2 + 4 + 8 = 15 = 16 − 1.

## 1. Asymptotic notations: O, Ω, Θ (8/8)

Asymptotic notation describes how fast an algorithm's work grows as the input size n gets very large, ignoring small details. Big-O is a ceiling, Big-Omega is a floor, and Theta is both at once.

- **A. Why we need it**
  - We count an algorithm's steps as a formula in n, called f(n). Example: f(n) = 3n² + 5n + 2.
  - Exact formulas are messy and depend on the computer. We only care about the part that matters when n is huge.
    - At n = 1000: 3n² = 3,000,000 but 5n + 2 = 5,002. The n² part swamps everything else.
  - So we drop constants and smaller terms and say "f(n) grows like n²".
- **B. Order of growth (memorise this ladder, slowest to fastest)**
  - 1 < log n < √n < n < n log n < n² < n³ < 2ⁿ < n! < nⁿ
    - 1 = constant (same work whatever n is).
    - log n = logarithmic (binary search).
    - n = linear (linear search).
    - n log n = "linearithmic" (merge sort, good quick sort).
    - n², n³ = quadratic, cubic (bubble sort, matrix multiplication).
    - 2ⁿ, n! = exponential, factorial (hopeless for large n).

How the ladder looks in real numbers:

| n | log₂ n | n log₂ n | n² | n³ | 2ⁿ |
| --- | --- | --- | --- | --- | --- |
| 10 | 3.3 | 33 | 100 | 1,000 | 1,024 |
| 100 | 6.6 | 664 | 10,000 | 1,000,000 | about 1.3 × 10³⁰ |
| 1,000 | 10 | 9,966 | 1,000,000 | 10⁹ | about 10³⁰¹ |

- **C. Big-O, O(g(n)): the upper bound ("at most")**
  - Plain meaning: f grows **no faster than** g. g is a ceiling for f.
  - Formal definition: f(n) = O(g(n)) if there exist positive constants c and n₀ such that **f(n) ≤ c · g(n) for all n ≥ n₀**.
    - c lets us ignore constant multipliers.
    - n₀ means "from some point onward"; small n do not matter.
  - Analogy: a speed limit. Your speed may be lower, never higher.
- **D. Big-Omega, Ω(g(n)): the lower bound ("at least")**
  - Plain meaning: f grows **at least as fast as** g. g is a floor.
  - Formal: f(n) = Ω(g(n)) if there exist positive c and n₀ such that **f(n) ≥ c · g(n) for all n ≥ n₀**.
- **E. Theta, Θ(g(n)): the tight bound ("exactly this rate")**
  - Plain meaning: f grows **at the same rate** as g. It is both O and Ω.
  - Formal: f(n) = Θ(g(n)) if there exist positive c₁, c₂ and n₀ such that **c₁ · g(n) ≤ f(n) ≤ c₂ · g(n) for all n ≥ n₀**.
  - Analogy: a sandwich. f is squeezed between two copies of g.
- **F. Little-o and little-omega (sometimes asked as one-liners)**
  - f = o(g): f grows **strictly slower** than g (f/g → 0). Example: n = o(n²).
  - f = ω(g): f grows **strictly faster** than g (f/g → ∞). Example: n² = ω(n).

```latex
f(n)=O(g(n)) \iff \exists\, c>0,\ n_0 \text{ such that } f(n)\le c\,g(n)\ \ \forall n\ge n_0
```

- **G. How to PROVE a bound (the recipe)**
  1. Write the inequality the definition needs.
  2. Make the left side bigger (for O) or smaller (for Ω) using simple tricks, like "n ≤ n² when n ≥ 1".
  3. Read off c and n₀. State them clearly. That is the proof.
  - **Worked example 1: prove 3n² + 5n + 2 = O(n²).**
    - For n ≥ 1: 5n ≤ 5n² and 2 ≤ 2n².
    - So 3n² + 5n + 2 ≤ 3n² + 5n² + 2n² = 10n².
    - Hence f(n) ≤ 10 · n² for all n ≥ 1. Take c = 10, n₀ = 1. Proved.
  - **Worked example 2: prove 3n² + 5n + 2 = Ω(n²).**
    - For n ≥ 1, 5n + 2 is positive, so 3n² + 5n + 2 ≥ 3n².
    - Take c = 3, n₀ = 1. Proved.
  - **Worked example 3: therefore 3n² + 5n + 2 = Θ(n²).**
    - 3n² ≤ f(n) ≤ 10n² for all n ≥ 1, so c₁ = 3, c₂ = 10, n₀ = 1.
  - **Worked example 4: prove 2n + 3 = O(n).**
    - For n ≥ 1: 3 ≤ 3n, so 2n + 3 ≤ 5n. c = 5, n₀ = 1.
  - **Worked example 5: prove 2ⁿ⁺¹ = O(2ⁿ).**
    - 2ⁿ⁺¹ = 2 · 2ⁿ, so c = 2, n₀ = 1 works.
- **H. How to DISPROVE a bound (proof by contradiction)**
  - Assume the bound is true, then show it forces something impossible.
  - **Worked example 6: show n² ≠ O(n).**
    - Suppose n² ≤ c · n for all n ≥ n₀.
    - Divide by n: n ≤ c for all n ≥ n₀.
    - Impossible: c is a fixed number but n keeps growing (take n = c + 1). Contradiction, so n² is not O(n).
  - **Worked example 7: show 2²ⁿ ≠ O(2ⁿ).**
    - Suppose 4ⁿ ≤ c · 2ⁿ. Divide by 2ⁿ: 2ⁿ ≤ c for all large n. Impossible. Contradiction.
  - **Worked example 8: show n ≠ Ω(n²).**
    - Suppose n ≥ c · n². Divide by n²: 1/n ≥ c. But 1/n shrinks to 0, so it cannot stay above a fixed c > 0. Contradiction.
- **I. Shortcuts for quick answers**
  - Drop constants and keep the highest-power term: 7n³ + 100n² + 9 = Θ(n³).
  - Any polynomial of degree k is Θ(n^k).
  - The base of a logarithm does not matter: log₂ n and log₁₀ n differ only by a constant.
  - Limit test: work out the limit of f(n)/g(n) as n → ∞.
    - 0 → f grows slower (f = O(g), in fact o(g)).
    - A positive constant → f = Θ(g).
    - ∞ → f grows faster (f = Ω(g), in fact ω(g)).
- **J. Upper and lower bounds of an algorithm**
  - Upper bound = a guarantee the algorithm never takes **more** than this. Usually stated with O, from the worst case.
  - Lower bound = the algorithm never takes **less** than this. Usually stated with Ω, from the best case.
    - Linear search: worst case n comparisons, best case 1. So its time is O(n) and Ω(1).
  - A lower bound can also belong to a whole **problem**: any sorting method that only compares items needs Ω(n log n) comparisons in the worst case.

**Exam tip:** for every "prove" question, always state the definition first, then show the inequality, then write "c = …, n₀ = …" in a final line. For "disprove", write "Assume, for contradiction, …" and end with "which is impossible".

## 2. Recurrence relations: substitution, recursion tree, Master theorem (8/8)

A recurrence relation describes the running time of a recursive algorithm in terms of its running time on smaller inputs; solving it means turning it into a plain formula like Θ(n log n). There are three methods, and the exam asks all three.

- **A. What a recurrence is**
  - T(n) = time to solve a problem of size n.
  - A recursive algorithm's time = time of its smaller calls + extra work done in this call.
    - Factorial: n! = n × (n−1)! → **T(n) = T(n−1) + 1**, T(1) = 1.
    - Binary search: look at the middle, then search one half → **T(n) = T(n/2) + 1**.
    - Merge sort: sort two halves, then merge in n steps → **T(n) = 2T(n/2) + n**.
  - Every recurrence needs a **base case** (like T(1) = 1) or it never ends.
- **B. Method 1: Substitution (two flavours)**
  - **B1. Back-substitution (also called iteration or "unrolling")**: keep replacing T(…) by its own formula until a pattern appears.
  - **Worked example 1: T(n) = T(n−1) + 1, T(1) = 1**
    - T(n) = T(n−1) + 1
    - = \[T(n−2) + 1\] + 1 = T(n−2) + 2
    - = T(n−3) + 3
    - Pattern after k steps: T(n−k) + k.
    - Stop when n − k = 1, i.e. k = n − 1: T(n) = T(1) + (n − 1) = n. So **T(n) = Θ(n)**.
  - **Worked example 2: T(n) = T(n/2) + 1, T(1) = 1** (binary search)
    - T(n) = T(n/2) + 1 = T(n/4) + 2 = T(n/8) + 3
    - Pattern: T(n/2^k) + k.
    - Stop when n/2^k = 1, i.e. k = log₂ n: T(n) = 1 + log₂ n. So **T(n) = Θ(log n)**.
  - **Worked example 3: T(n) = 2T(n/2) + n, T(1) = 1** (merge sort)
    - T(n) = 2T(n/2) + n
    - = 2\[2T(n/4) + n/2\] + n = 4T(n/4) + 2n
    - = 8T(n/8) + 3n
    - Pattern: 2^k · T(n/2^k) + k·n.
    - Put k = log₂ n: n · T(1) + n log₂ n = n + n log₂ n. So **T(n) = Θ(n log n)**.
  - **Worked example 4: T(n) = T(n−1) + n, T(1) = 1** (worst-case quick sort)
    - T(n) = n + (n−1) + (n−2) + … + 2 + 1 = n(n+1)/2. So **T(n) = Θ(n²)**.
  - **B2. Guess-and-prove**: guess the answer, then prove it by mathematical induction (see topic 14).
    - Guess T(n) ≤ c·n log n for T(n) = 2T(n/2) + n.
    - Assume it holds for n/2: T(n/2) ≤ c(n/2) log(n/2).
    - Then T(n) ≤ 2 · c(n/2) log(n/2) + n = c·n(log n − 1) + n = c·n log n − cn + n.
    - This is ≤ c·n log n whenever c ≥ 1. Guess confirmed: T(n) = O(n log n).
- **C. Method 2: Recursion tree (draw the calls as a tree)**
  - Steps:
    1. Draw the root with the extra work of the first call.
    2. Draw its children (the smaller calls), each with its own extra work.
    3. Add up the work on each level (row) of the tree.
    4. Count the levels.
    5. Total = sum of all levels.
  - **Worked example 5: T(n) = 2T(n/2) + n**

```
Level 0:                n                      →  n
Level 1:         n/2          n/2              →  n
Level 2:      n/4   n/4    n/4   n/4           →  n
  ...                 ...                         ...
Last level:   1  1  1  1  ...  1  (n leaves)   →  n
```

- **C (continued). Reading the tree**
  - Every level adds up to n.
  - The size halves each level, so there are log₂ n + 1 levels.
  - Total = n × (log₂ n + 1) → **Θ(n log n)**.
  - **Worked example 6: T(n) = 3T(n/4) + n²**
    - Level 0: n². Level 1: 3 nodes of (n/4)² = (3/16)n². Level 2: 9 nodes of (n/16)² = (3/16)²n².
    - Each level is 3/16 of the one above, a shrinking (geometric) series.
    - Total ≤ n² × (1 + 3/16 + (3/16)² + …) = n² × 16/13. So **Θ(n²)**: the root dominates.
  - **Worked example 7: T(n) = T(n/3) + T(2n/3) + n** (uneven split)
    - Every full level adds to n.
    - The longest path keeps 2/3 each time, so the height is log base 3/2 of n.
    - Total ≈ n × log n → **Θ(n log n)**.
- **D. Method 3: Master theorem (the fastest method)**
  - Works only for recurrences of the form **T(n) = a·T(n/b) + f(n)**, with a ≥ 1 and b > 1.
    - a = number of smaller calls; n/b = size of each; f(n) = extra work in this call.
  - Key quantity: n raised to (log base b of a). Call it the "watershed" W(n). Compare f(n) with W(n):

```latex
T(n)=aT(n/b)+f(n), \qquad W(n)=n^{\log_b a}
```

| Case | Condition (compare f with W) | Answer |
| --- | --- | --- |
| 1. Leaves win | f(n) grows polynomially slower than W(n) | T(n) = Θ(W(n)) |
| 2. Tie | f(n) = Θ(W(n)) | T(n) = Θ(W(n) · log n) |
| 3. Root wins | f(n) grows polynomially faster than W(n), and a·f(n/b) ≤ k·f(n) for some k < 1 | T(n) = Θ(f(n)) |

- **E. Easy version when f(n) = n^d (a plain power of n)**
  - Compare a with b^d:
    - a < b^d → Θ(n^d)
    - a = b^d → Θ(n^d log n)
    - a > b^d → Θ(n raised to log base b of a)
- **F. Master theorem worked examples (practise all of these)**

| Recurrence | a, b, f(n) | W(n) | Case | Answer |
| --- | --- | --- | --- | --- |
| T(n) = 9T(n/3) + n | 9, 3, n | n² | 1 | Θ(n²) |
| T(n) = 2T(n/2) + n | 2, 2, n | n | 2 | Θ(n log n) |
| T(n) = T(n/2) + 1 | 1, 2, 1 | n⁰ = 1 | 2 | Θ(log n) |
| T(n) = T(2n/3) + 1 | 1, 3/2, 1 | 1 | 2 | Θ(log n) |
| T(n) = 4T(n/2) + n² | 4, 2, n² | n² | 2 | Θ(n² log n) |
| T(n) = 8T(n/2) + n² | 8, 2, n² | n³ | 1 | Θ(n³) |
| T(n) = 7T(n/2) + n² | 7, 2, n² | n^2.81 | 1 | Θ(n^2.81) (Strassen) |
| T(n) = 3T(n/2) + n | 3, 2, n | n^1.585 | 1 | Θ(n^1.585) (Karatsuba) |
| T(n) = 2T(n/2) + n² | 2, 2, n² | n | 3 | Θ(n²) |
| T(n) = 3T(n/4) + n log n | 3, 4, n log n | n^0.793 | 3 | Θ(n log n) |

- **G. When the Master theorem does NOT apply**
  - Not of the form aT(n/b): e.g. T(n) = T(n−1) + n. Use substitution instead (answer Θ(n²)).
  - f(n) falls in a gap between cases: e.g. T(n) = 2T(n/2) + n log n. f is bigger than W(n) = n, but not by a power of n. (Its answer is Θ(n log² n), found with a recursion tree.)
  - a < 1 or a not constant: e.g. T(n) = 2ⁿ T(n/2) + n.

**Exam tip:** with the Master theorem, always write a, b, f(n), compute n^(log\_b a), name the case, then give the answer. For recursion trees, draw at least three levels and write the cost of each level beside it.

## 3. Minimum spanning tree: Kruskal's and Prim's algorithms (7/8)

A minimum spanning tree (MST) connects all the points of a weighted graph using the cheapest possible set of lines with no loops; Kruskal's and Prim's algorithms both find it greedily and always give the same total cost. (Read topic 8, graph terminology, first if "vertex" and "edge" are new.)

- **A. The problem in everyday words**
  - Five villages must be joined by electric cable. Each possible cable route has a cost.
  - Goal: every village connected, total cost as low as possible, no wasted loops.
- **B. Key definitions**
  - **Weighted graph**: each edge carries a number (its weight or cost).
  - **Spanning tree**: a set of edges that
    - touches every vertex,
    - keeps the graph connected,
    - has no cycle,
    - therefore has exactly **V − 1 edges** (V = number of vertices).
  - **Minimum spanning tree**: the spanning tree with the smallest total weight.
    - The graph must be connected and undirected.
    - If some weights are equal, there can be more than one MST, but all have the same total.
- **C. The example graph used below (5 vertices, 7 edges)**

```
      A
    2/ \3
    /   \
   B--1--C
   |   / |
  4|  5  |6
   | /   |
   D--7--E
```

- **C (continued).** Edges: A–B 2, A–C 3, B–C 1, B–D 4, C–D 5, C–E 6, D–E 7. V = 5, so the MST needs 4 edges.
- **D. Kruskal's algorithm (think "cheapest edge anywhere")**
  - Steps:
    1. Sort all edges from smallest to largest weight.
    2. Take the next smallest edge.
    3. If it joins two vertices that are **not yet connected**, accept it. If they are already connected, reject it (it would make a cycle).
    4. Stop when you have V − 1 edges.
  - How the computer checks "already connected": it keeps each vertex in a group (a "team"). An edge inside one team makes a cycle. Accepting an edge merges two teams. This is called the **union–find** (disjoint-set) structure.
  - Time: sorting takes O(E log E), so Kruskal is **O(E log E)**, the same as O(E log V).

Kruskal trace on the example:

| Step | Edge (weight) | Accept or reject? | Reason | Teams after this step |
| --- | --- | --- | --- | --- |
| 1 | B–C (1) | Accept | B, C in different teams | {B, C} {A} {D} {E} |
| 2 | A–B (2) | Accept | A not in B's team | {A, B, C} {D} {E} |
| 3 | A–C (3) | Reject | A and C already in one team (cycle A–B–C) | no change |
| 4 | B–D (4) | Accept | D in a different team | {A, B, C, D} {E} |
| 5 | C–D (5) | Reject | would make a cycle | no change |
| 6 | C–E (6) | Accept | E in a different team; 4 edges now, stop | {A, B, C, D, E} |

- **D (result).** MST edges: B–C, A–B, B–D, C–E. Total weight = 1 + 2 + 4 + 6 = **13**.
- **E. Prim's algorithm (think "grow one tree outward")**
  - Steps:
    1. Start from any vertex. It is the tree.
    2. Look at all edges that join a tree vertex to a non-tree vertex.
    3. Add the cheapest such edge (and its new vertex) to the tree.
    4. Repeat until all vertices are in the tree.
  - There is always exactly one tree, so a cycle can never form.
  - Time: **O(V²)** with an adjacency matrix; **O(E log V)** with a priority queue (min-heap).

Prim trace on the same graph, starting at A:

| Step | Tree so far | Edges leaving the tree (candidates) | Cheapest chosen |
| --- | --- | --- | --- |
| 1 | {A} | A–B 2, A–C 3 | A–B (2) |
| 2 | {A, B} | A–C 3, B–C 1, B–D 4 | B–C (1) |
| 3 | {A, B, C} | B–D 4, C–D 5, C–E 6 | B–D (4) |
| 4 | {A, B, C, D} | C–E 6, D–E 7 | C–E (6) |
| End | {A, B, C, D, E} | none | Total = 13 |

- **E (result).** Same total, 13, as Kruskal. This is always true: both find a minimum spanning tree.
- **F. Kruskal vs Prim: comparison**

| Point | Kruskal | Prim |
| --- | --- | --- |
| Basic idea | Picks the cheapest edge in the whole graph | Picks the cheapest edge touching the current tree |
| Starts from | The edge list (no start vertex) | Any one chosen vertex |
| Midway picture | A forest (several separate pieces) that later join | Always one connected tree |
| Cycle check needed? | Yes (union–find) | No, cycles cannot form |
| Main data structure | Sorted edge list + disjoint sets | Priority queue (min-heap) or array |
| Time | O(E log E) | O(V²) with matrix; O(E log V) with heap |
| Better for | Sparse graphs (few edges) | Dense graphs (many edges) |
| Strategy | Greedy | Greedy |
| Result | A minimum spanning tree | A minimum spanning tree (same total weight) |

**Exam tip:** always draw the graph, then a step table like the ones above. For Kruskal, write the rejected edges with "forms a cycle"; examiners give marks for that. End with the list of MST edges and the total weight.

## 4. Bubble sort: trace, comparisons and exchanges, best and worst case (6/8)

Bubble sort repeatedly compares neighbouring items and swaps them if they are in the wrong order, so the largest remaining item "bubbles" to the end on every pass; it always makes n(n−1)/2 comparisons in its basic form and is Θ(n²) in the worst case.

- **A. What "sorting" means**
  - Putting items in order, usually smallest to largest (ascending). \[5, 1, 4\] → \[1, 4, 5\].
- **B. The idea in plain words**
  - Walk along the list comparing each pair of neighbours: positions (1, 2), then (2, 3), then (3, 4) …
  - If the left one is bigger, swap them (an "exchange").
  - After one full walk (a **pass**), the biggest item has reached the last position, like a bubble rising to the top.
  - Each next pass can stop one position earlier, because the end is already sorted.
  - n items need at most n − 1 passes.
- **C. Pseudocode (with the "swapped" flag improvement)**

```
BubbleSort(A[1..n])
  for pass ← 1 to n − 1
      swapped ← false
      for j ← 1 to n − pass
          if A[j] > A[j + 1] then
              swap A[j] and A[j + 1]
              swapped ← true
      if swapped = false then stop     // no swaps: list is already sorted
```

- **D. Full trace: sort \[5, 1, 4, 2, 8\]** (n = 5)

| Pass | Pair compared | Swap? | List after this step |
| --- | --- | --- | --- |
| 1 | 5 and 1 | Yes | 1, 5, 4, 2, 8 |
| 1 | 5 and 4 | Yes | 1, 4, 5, 2, 8 |
| 1 | 5 and 2 | Yes | 1, 4, 2, 5, 8 |
| 1 | 5 and 8 | No | 1, 4, 2, 5, **8** |
| 2 | 1 and 4 | No | 1, 4, 2, 5, 8 |
| 2 | 4 and 2 | Yes | 1, 2, 4, 5, 8 |
| 2 | 4 and 5 | No | 1, 2, 4, **5, 8** |
| 3 | 1 and 2 | No | 1, 2, 4, 5, 8 |
| 3 | 2 and 4 | No | 1, 2, **4, 5, 8** (no swaps this pass) |
| 4 | 1 and 2 | No | **1, 2, 4, 5, 8** |

- **E. Counting for this example**
  - Comparisons per pass: 4, 3, 2, 1 → total **10** = 5 × 4 / 2.
  - Exchanges (swaps): 3 in pass 1, 1 in pass 2 → total **4**.
  - With the swapped flag, the algorithm stops after pass 3 (no swaps there) → 9 comparisons, 4 swaps.
  - Neat fact: number of swaps = number of **inversions** (pairs that are out of order). Here: (5,1), (5,4), (5,2), (4,2) = 4.
- **F. Counting in general (for a list of n items)**
  - Comparisons in the basic version: (n−1) + (n−2) + … + 2 + 1 = **n(n−1)/2**, whatever the input.
  - Exchanges depend on the input:
    - Already sorted → **0** swaps.
    - Reverse sorted → every comparison swaps → **n(n−1)/2** swaps.
    - Random order → about n(n−1)/4 swaps on average.
- **G. Best case and worst case**

| Case | Input example (n = 5) | Comparisons | Swaps | Time |
| --- | --- | --- | --- | --- |
| Best, with flag | 1, 2, 3, 4, 5 (sorted) | n − 1 = 4 (one pass) | 0 | Θ(n) |
| Best, without flag | 1, 2, 3, 4, 5 | n(n−1)/2 = 10 | 0 | Θ(n²) |
| Worst | 5, 4, 3, 2, 1 (reversed) | n(n−1)/2 = 10 | n(n−1)/2 = 10 | Θ(n²) |
| Average | random order | about n²/2 | about n²/4 | Θ(n²) |

- **H. Other properties (good for 1-mark answers)**
  - Space: O(1) extra. It sorts **in place** (only one spare box for swapping).
  - **Stable**: equal items keep their original order, because we swap only when strictly greater.
  - Simple to write, but slow for big lists.

**Exam tip:** show every pass as a separate line or table row, and write the comparisons and swaps per pass in the margin. If asked for best and worst cases, give an example input for each, not just the formula.

## 5. Linear search and binary search: trace, best and worst case (6/8)

Linear search checks items one by one and works on any list (worst case n comparisons); binary search repeatedly halves a **sorted** list and needs only about log₂ n comparisons, roughly 20 for a million items.

- **A. The search problem**
  - Input: a list A of n items and a value to find, called the **key**.
  - Output: the position of the key, or "not found".
- **B. Linear (sequential) search**
  - **B1. Idea**: start at the first box and check each one in turn until you find the key or run out of boxes. Like looking for a name in an unsorted attendance sheet.
  - **B2. Pseudocode**

```
LinearSearch(A[1..n], key)
  for i ← 1 to n
      if A[i] = key then return i     // found at position i
  return "not found"
```

- **B3. Trace: A = \[7, 3, 9, 1, 6\]**
  - Search key = 1: compare with 7 (no), 3 (no), 9 (no), 1 (yes) → found at position 4 after **4 comparisons**.
  - Search key = 5: compare with 7, 3, 9, 1, 6 → all no → "not found" after **5 comparisons**.
- **B4. Analysis**
  - Best case: key is in the first box → **1 comparison → Θ(1)**.
  - Worst case: key is in the last box, or absent → **n comparisons → Θ(n)**.
  - Average case (key present, any position equally likely): (1 + 2 + … + n)/n = **(n + 1)/2** comparisons → still Θ(n).
  - Works on unsorted lists. That is its big advantage.
- **C. Binary search**
  - **C1. Condition**: the list **must already be sorted**.
  - **C2. Idea**: like finding a word in a dictionary. Open the middle; if your word comes earlier, throw away the right half; if later, throw away the left half. Repeat.
  - **C3. Pseudocode**

```
BinarySearch(A[1..n], key)          // A is sorted
  low ← 1;  high ← n
  while low ≤ high
      mid ← ⌊(low + high) / 2⌋
      if key = A[mid] then return mid
      else if key < A[mid] then high ← mid − 1   // search left half
      else low ← mid + 1                          // search right half
  return "not found"
```

- **C4. Trace 1: A = \[2, 5, 8, 12, 16, 23, 38, 56, 72, 91\], key = 23** (n = 10)

| Step | low | high | mid | A\[mid\] | Decision |
| --- | --- | --- | --- | --- | --- |
| 1 | 1 | 10 | 5 | 16 | 23 > 16, go right: low = 6 |
| 2 | 6 | 10 | 8 | 56 | 23 < 56, go left: high = 7 |
| 3 | 6 | 7 | 6 | 23 | Equal: found at position 6 |

- **C4 (result).** Found in **3 comparisons** (linear search would need 6).
- **C5. Trace 2: same list, key = 10 (not present)**

| Step | low | high | mid | A\[mid\] | Decision |
| --- | --- | --- | --- | --- | --- |
| 1 | 1 | 10 | 5 | 16 | 10 < 16: high = 4 |
| 2 | 1 | 4 | 2 | 5 | 10 > 5: low = 3 |
| 3 | 3 | 4 | 3 | 8 | 10 > 8: low = 4 |
| 4 | 4 | 4 | 4 | 12 | 10 < 12: high = 3 |
| Stop | 4 | 3 | – | – | low > high: not found |

- **C6. Analysis**
  - Best case: key is at the first middle → **1 comparison → Θ(1)**.
  - Worst case: the list halves every step until one item is left → **⌊log₂ n⌋ + 1 comparisons → Θ(log n)**.
    - Recurrence: T(n) = T(n/2) + 1 → Θ(log n) (see topic 2).
  - Average case: also Θ(log n).
  - Space: O(1) for this loop version.
- **D. Side-by-side comparison**

| Point | Linear search | Binary search |
| --- | --- | --- |
| Needs sorted list? | No | Yes |
| Method | Check one by one | Halve the search range each step |
| Best case | 1 comparison, Θ(1) | 1 comparison, Θ(1) |
| Worst case | n comparisons, Θ(n) | ⌊log₂ n⌋ + 1 comparisons, Θ(log n) |
| Worst case for n = 1,000,000 | 1,000,000 comparisons | 20 comparisons |
| Design technique | Brute force | Divide and conquer (decrease by half) |

**Exam tip:** in a binary-search trace, always make the low / high / mid table and write the decision in words. Mention that the list must be sorted; examiners often give a mark just for that.

## 6. Euclid's GCD algorithm: trace and complexity (6/8)

Euclid's algorithm finds the greatest common divisor of two numbers by repeatedly replacing (m, n) with (n, m mod n) until n becomes 0; it takes O(log n) steps, far faster than checking every possible divisor.

- **A. What GCD means**
  - GCD(m, n) = the largest whole number that divides both m and n with no remainder. Also called HCF (highest common factor).
    - Divisors of 12: 1, 2, 3, 4, 6, 12. Divisors of 18: 1, 2, 3, 6, 9, 18. Common: 1, 2, 3, 6 → **GCD(12, 18) = 6**.
  - Listing divisors works for small numbers but is slow for big ones. Euclid's trick is much faster.
- **B. The one rule behind it**
  - **gcd(m, n) = gcd(n, m mod n)**, and **gcd(m, 0) = m**.
  - Recall: m mod n is the remainder of m ÷ n. Example: 60 mod 24 = 12, because 60 = 2 × 24 + 12.
  - Why the rule is true: any number dividing both m and n also divides m − q·n, which is the remainder. So the pair (n, remainder) has exactly the same common divisors as (m, n).
- **C. Algorithm (in steps, then pseudocode)**
  1. If n = 0, the answer is m. Stop.
  2. Divide m by n; let r be the remainder.
  3. Replace m by n, and n by r. Go back to step 1.

```
Euclid(m, n)          // m, n are non-negative, not both 0
  while n ≠ 0
      r ← m mod n
      m ← n
      n ← r
  return m
```

- **D. Trace 1: gcd(60, 24)**

| Step | m | n | r = m mod n |
| --- | --- | --- | --- |
| 1 | 60 | 24 | 12 |
| 2 | 24 | 12 | 0 |
| End | 12 | 0 | answer = **12** |

- **E. Trace 2: gcd(1071, 462)**

| Step | m | n | Division | r |
| --- | --- | --- | --- | --- |
| 1 | 1071 | 462 | 1071 = 2 × 462 + 147 | 147 |
| 2 | 462 | 147 | 462 = 3 × 147 + 21 | 21 |
| 3 | 147 | 21 | 147 = 7 × 21 + 0 | 0 |
| End | 21 | 0 | – | answer = **21** |

- **F. Trace 3 (a textbook favourite): gcd(31415, 14142)**

| Step | m | n | r |
| --- | --- | --- | --- |
| 1 | 31415 | 14142 | 3131 |
| 2 | 14142 | 3131 | 1618 |
| 3 | 3131 | 1618 | 1513 |
| 4 | 1618 | 1513 | 105 |
| 5 | 1513 | 105 | 43 |
| 6 | 105 | 43 | 19 |
| 7 | 43 | 19 | 5 |
| 8 | 19 | 5 | 4 |
| 9 | 5 | 4 | 1 |
| 10 | 4 | 1 | 0 |
| End | 1 | 0 | answer = **1** (10 divisions) |

- **G. What if m < n?** The first step simply swaps them: gcd(24, 60) → 24 mod 60 = 24 → (60, 24). One extra step, same answer.
- **H. Complexity**
  - Basic operation: the division (mod).
  - Key fact: **after every two steps, the bigger number at least halves**, because m mod n is always less than m/2.
  - So the number of steps is at most about 2 log₂ n → **O(log n)**, where n is the smaller number.
  - Best case: n divides m at once (e.g. gcd(60, 12)) → 1 division → Θ(1).
  - Worst case: two consecutive **Fibonacci numbers** (e.g. 13 and 8): the remainders fall as slowly as possible (Lamé's theorem). Still Θ(log n).
- **I. Compare with slower GCD methods**

| Method | How it works | Time |
| --- | --- | --- |
| Consecutive integer checking | Try t = min(m, n), then t − 1, t − 2 … until t divides both | O(min(m, n)), slow |
| Middle-school (prime factors) | Factorise both into primes, multiply the common primes | Slow for big numbers (factorising is hard) |
| Euclid's algorithm | Repeat gcd(n, m mod n) | O(log min(m, n)), fast |

**Exam tip:** always present the trace as an m / n / r table and box the final answer. For complexity, write the "halves every two steps" argument in one or two lines, then conclude O(log n).

## 7. Depth-first search (DFS), and DFS vs BFS (6/8)

DFS visits every vertex of a graph by going as deep as possible along one path before backing up, using a stack; BFS instead visits level by level using a queue. Both take Θ(V + E) time with adjacency lists.

- **A. What "traversal" means**
  - Visiting every vertex of a graph exactly once, in some systematic order.
  - We **mark** each vertex as "visited" so we never visit it twice (graphs can have loops).
- **B. DFS idea in everyday words**
  - Exploring a maze: keep walking forward through new corridors. At a dead end, walk back (**backtrack**) to the last junction that still has an unexplored corridor.
  - The "walk back" memory is a **stack** (last in, first out), like a pile of plates. Recursion gives this stack for free.
- **C. Pseudocode (recursive)**

```
DFS(G)
  mark every vertex as unvisited
  for each vertex v in G
      if v is unvisited then Explore(v)   // restarts handle disconnected graphs

Explore(v)
  mark v as visited; print v
  for each neighbour w of v
      if w is unvisited then Explore(w)
```

- **D. Example graph** (undirected; neighbours taken in alphabetical order)

```
        A
       / \
      B   C
     / \   \
    D   E---F
```

- **D (exact edges).** A–B, A–C, B–D, B–E, C–F, E–F. Adjacency lists:
  - A: B, C
  - B: A, D, E
  - C: A, F
  - D: B
  - E: B, F
  - F: C, E
- **E. DFS trace from A**

| Step | Action | Stack (bottom → top) | Visited so far |
| --- | --- | --- | --- |
| 1 | Start at A | A | A |
| 2 | A's first unvisited neighbour is B | A, B | A, B |
| 3 | B's first unvisited neighbour is D | A, B, D | A, B, D |
| 4 | D has no unvisited neighbour: backtrack | A, B | – |
| 5 | B's next unvisited neighbour is E | A, B, E | A, B, D, E |
| 6 | E's first unvisited neighbour is F | A, B, E, F | A, B, D, E, F |
| 7 | F's first unvisited neighbour is C | A, B, E, F, C | A, B, D, E, F, C |
| 8 | C, F, E, B, A have nothing new: pop all | empty | done |

- **E (result).** **DFS order: A, B, D, E, F, C.**
  - Tree edges (used to reach a new vertex): A–B, B–D, B–E, E–F, F–C. These form the **DFS tree**.
  - Back edge (leads to an already-visited ancestor): C–A. A back edge in an undirected graph means **there is a cycle** (A–B–E–F–C–A).
- **F. BFS on the same graph, for comparison**
  - Idea: visit the start, then all its neighbours, then all their neighbours… like ripples in a pond. Uses a **queue** (first in, first out), like a ticket line.

| Step | Remove from queue | Add its unvisited neighbours | Queue after |
| --- | --- | --- | --- |
| 1 | A | B, C | B, C |
| 2 | B | D, E | C, D, E |
| 3 | C | F | D, E, F |
| 4 | D | none | E, F |
| 5 | E | none (F already seen) | F |
| 6 | F | none | empty |

- **F (result).** **BFS order: A, B, C, D, E, F.** Notice BFS finishes all distance-1 vertices (B, C) before distance-2 ones.
- **G. Time complexity (both)**
  - Adjacency list: every vertex and every edge is handled once → **Θ(V + E)**.
  - Adjacency matrix: scanning each row costs V → **Θ(V²)**.
- **H. DFS vs BFS: comparison**

| Point | DFS | BFS |
| --- | --- | --- |
| Full name | Depth-first search | Breadth-first search |
| Data structure | Stack (or recursion) | Queue |
| Order of visiting | Deep along one path, then backtrack | Level by level, nearest first |
| Order in our example | A, B, D, E, F, C | A, B, C, D, E, F |
| Shortest path (fewest edges) in unweighted graph | Not guaranteed | Yes, guaranteed |
| Extra edges found | Back edges | Cross edges |
| Time with adjacency list | Θ(V + E) | Θ(V + E) |
| Time with adjacency matrix | Θ(V²) | Θ(V²) |
| Typical uses | Cycle detection, topological sort, connected components, mazes and puzzles | Shortest path by number of edges, "friends within 2 steps", level-order of a tree |

- **I. Uses of DFS worth remembering**
  - Is the graph connected? Run DFS once; if some vertex is unvisited, no. The number of restarts = number of **connected components**.
  - Does it have a cycle? Yes, if DFS ever finds a back edge.
  - Topological sorting of a directed acyclic graph (order tasks so prerequisites come first).

**Exam tip:** always state the starting vertex and the rule for choosing neighbours (e.g. "alphabetical order"); different rules give different but equally correct orders. Show the stack (DFS) or queue (BFS) at every step.

## 8. Graph terminology: path, cycle, connected and complete graph, tree, digraph (6/8)

A graph is a set of points (vertices) joined by lines (edges), written G = (V, E); almost every term below is a plain-English idea about how those points are joined.

- **A. Graph basics**
  - **Vertex** (node): a point. Example: a city.
  - **Edge**: a line joining two vertices. Example: a road between two cities.
  - **G = (V, E)**: V is the set of vertices, E the set of edges. |V| = number of vertices, |E| = number of edges.
    - Example: V = {A, B, C, D}, E = {A–B, B–C, C–D, D–A, A–C}. 4 vertices, 5 edges.

```
   A ----- B
   | \     |
   |   \   |
   D ----- C
```

- **B. Kinds of edges and graphs**
  - **Undirected graph**: edges have no direction. A–B is the same as B–A (a two-way road).
  - **Directed graph (digraph)**: every edge has an arrow, written as an ordered pair (u, v) meaning u → v (a one-way street; "A follows B" on social media).
  - **Weighted graph**: each edge has a number (cost, distance, time).
  - **Self-loop**: an edge from a vertex to itself. **Parallel (multiple) edges**: two edges joining the same pair.
  - **Simple graph**: no self-loops and no parallel edges. Exam graphs are simple unless stated.
- **C. Neighbours and degree**
  - **Adjacent** vertices: joined by an edge. In the example, A and C are adjacent; B and D are not.
  - **Degree** of a vertex: the number of edges touching it. In the example: deg(A) = 3, deg(B) = 2, deg(C) = 3, deg(D) = 2.
  - **Handshaking lemma**: the sum of all degrees = 2 × number of edges (each edge has two ends). Check: 3 + 2 + 3 + 2 = 10 = 2 × 5.
  - In a digraph: **in-degree** = arrows coming in; **out-degree** = arrows going out.
- **D. Path and cycle**
  - **Path**: a sequence of vertices where each one is joined to the next by an edge. Example: A → B → C → D.
    - **Length** of a path = number of edges in it (here 3).
    - **Simple path**: no vertex repeated.
  - **Cycle**: a path that starts and ends at the same vertex, with no other vertex repeated (needs at least 3 vertices in a simple undirected graph). Example: A → B → C → A.
  - **Acyclic graph**: a graph with no cycles.
  - **DAG**: directed acyclic graph (directed, no cycles). Used for task scheduling.
- **E. Connected graph**
  - **Connected**: there is a path between **every** pair of vertices. Our example is connected.
  - **Disconnected**: some pair has no path. The separate pieces are called **connected components**.
  - Digraph version: **strongly connected** = you can travel from every vertex to every other following the arrows.
- **F. Complete graph (Kₙ)**
  - Every pair of vertices is joined directly by an edge.
  - Number of edges in Kₙ = **n(n − 1)/2**. Example: K₄ has 4 × 3 / 2 = 6 edges.
  - This is also the **maximum** number of edges any simple undirected graph on n vertices can have. A simple digraph can have at most n(n − 1).
- **G. Tree**
  - **Tree**: a connected graph with **no cycles**.
  - Facts (all equivalent for a graph with n vertices):
    - connected and acyclic;
    - has exactly **n − 1 edges**;
    - there is **exactly one path** between any two vertices.
  - **Forest**: a collection of separate trees (acyclic but maybe disconnected).
  - **Rooted tree** words: root (top), parent, child, siblings, **leaf** (no children), height (longest root-to-leaf path).
  - **Spanning tree**: a tree using all vertices of a graph and some of its edges (topic 3).
- **H. Other useful words**
  - **Subgraph**: some of the vertices and edges of a graph.
  - **Dense graph**: many edges (close to n²). **Sparse graph**: few edges (close to n).
- **I. Quick summary table**

| Term | One-line meaning | Example |
| --- | --- | --- |
| Path | Vertices joined one after another by edges | A–B–C–D |
| Cycle | Path returning to its start, nothing else repeated | A–B–C–A |
| Connected graph | Path exists between every pair | Our 4-vertex example |
| Complete graph Kₙ | Every pair directly joined; n(n−1)/2 edges | K₄ has 6 edges |
| Tree | Connected, no cycle; n − 1 edges | A family tree |
| Digraph | Edges have direction (arrows) | One-way streets |
| Weighted graph | Edges carry numbers | Road map with distances |
| Degree | Number of edges at a vertex | deg(A) = 3 above |

**Exam tip:** for each definition, draw a tiny example graph beside it. Diagrams earn marks quickly in definition questions.

## 9. Greedy technique: fractional knapsack, minimum number of notes or coins (6/8)

A greedy algorithm builds an answer step by step, always taking the choice that looks best right now and never undoing it; it gives the best answer for fractional knapsack (sort by profit per kg) and for Indian rupee change-making, but not for every problem.

- **A. The greedy idea**
  - At each step, make the **locally best** choice. Hope it leads to the **globally best** answer.
  - Each choice must be:
    - **Feasible**: it obeys the rules (e.g. does not exceed capacity).
    - **Locally optimal**: the best option available at this step.
    - **Irrevocable**: once made, never changed.
  - Greedy algorithms you already know: Kruskal, Prim (topic 3), Dijkstra (topic 10).
- **B. Minimum number of notes and coins (change-making)**
  - **Problem**: pay an amount using the fewest notes and coins.
  - **Greedy rule**: always use the largest denomination that still fits; repeat with what is left.
  - Pseudocode:

```
MinNotes(amount, D[1..k])        // D sorted largest to smallest
  for i ← 1 to k
      count[i] ← amount div D[i]  // how many of this note fit
      amount ← amount mod D[i]    // what is left
  return count
```

- **B (worked example).** Pay ₹1,988 using denominations 500, 200, 100, 50, 20, 10, 5, 2, 1.

| Denomination (₹) | Amount left before | How many | Value used | Amount left after |
| --- | --- | --- | --- | --- |
| 500 | 1,988 | 3 | 1,500 | 488 |
| 200 | 488 | 2 | 400 | 88 |
| 100 | 88 | 0 | 0 | 88 |
| 50 | 88 | 1 | 50 | 38 |
| 20 | 38 | 1 | 20 | 18 |
| 10 | 18 | 1 | 10 | 8 |
| 5 | 8 | 1 | 5 | 3 |
| 2 | 3 | 1 | 2 | 1 |
| 1 | 1 | 1 | 1 | 0 |

- **B (result).** Total = 3 + 2 + 1 + 1 + 1 + 1 + 1 + 1 = **11 notes/coins**.
  - Time: one division per denomination → **O(k)** for k denominations.
  - **Greedy can fail** with odd coin systems. Coins {1, 3, 4}, amount 6:
    - Greedy: 4 + 1 + 1 = 3 coins.
    - Best: 3 + 3 = 2 coins.
    - It works for real currencies like the rupee because those systems are designed so greedy is always optimal.
- **C. Fractional knapsack**
  - **Problem**: a bag (knapsack) holds at most W kg. There are n items; item i has weight wᵢ and profit pᵢ. You may take **any fraction** of an item (like grains or liquids). Maximise total profit.
  - **Greedy rule**: compute **profit per unit weight, pᵢ / wᵢ**, for each item. Take items in decreasing order of this ratio. Take each item fully while it fits; take a fraction of the first item that does not fit; stop.
  - Pseudocode:

```
FractionalKnapsack(p[1..n], w[1..n], W)
  sort items by p[i]/w[i] in decreasing order
  remaining ← W;  profit ← 0
  for each item i in that order
      if w[i] ≤ remaining then
          x[i] ← 1;  remaining ← remaining − w[i];  profit ← profit + p[i]
      else
          x[i] ← remaining / w[i];  profit ← profit + p[i] × x[i]
          stop                                  // bag is full
  return profit
```

- **C (worked example 1).** n = 3, W = 20. Profits (25, 24, 15), weights (18, 15, 10).

| Item | Profit p | Weight w | Ratio p/w | Order |
| --- | --- | --- | --- | --- |
| 1 | 25 | 18 | 1.39 | 3rd |
| 2 | 24 | 15 | 1.60 | 1st |
| 3 | 15 | 10 | 1.50 | 2nd |

- **C (filling the bag).**
  1. Item 2: weight 15 fits in 20 → take all. Profit 24. Space left 5.
  2. Item 3: weight 10 > 5 → take 5/10 = 1/2. Profit 15 × 1/2 = 7.5. Space left 0. Stop.
  - Solution x = (x₁, x₂, x₃) = (0, 1, 1/2). **Maximum profit = 31.5.**
  - Why the ratio matters (other greedy rules are worse):
    - Largest profit first: item 1 (25), then 2/15 of item 2 (3.2) → 28.2.
    - Lightest first: item 3 (15), then 10/15 of item 2 (16) → 31.
    - Best ratio first → 31.5, the true maximum.
- **C (worked example 2, a common exam version).** n = 7, W = 15. Profits (10, 5, 15, 7, 6, 18, 3), weights (2, 3, 5, 7, 1, 4, 1).

| Order | Item | p/w | Take | Weight used (total) | Profit added | Total profit |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | 5 | 6.0 | all | 1 (1) | 6 | 6 |
| 2 | 1 | 5.0 | all | 2 (3) | 10 | 16 |
| 3 | 6 | 4.5 | all | 4 (7) | 18 | 34 |
| 4 | 3 | 3.0 | all | 5 (12) | 15 | 49 |
| 5 | 7 | 3.0 | all | 1 (13) | 3 | 52 |
| 6 | 2 | 1.67 | 2/3 | 2 (15) | 3.33 | 55.33 |
| – | 4 | 1.0 | none | bag full | 0 | 55.33 |

- **C (result 2).** x = (1, 2/3, 1, 0, 1, 1, 1). **Maximum profit ≈ 55.33.**
  - Time: sorting dominates → **O(n log n)**.
  - Contrast: in **0/1 knapsack** (take an item whole or not at all) this greedy rule can fail; that version needs dynamic programming or branch and bound (topic 15).

**Exam tip:** in knapsack answers always show the ratio column, the sorted order, the solution vector x and the final profit. In change-making, show the table and state the total count.

## 10. Dijkstra's single-source shortest path algorithm (5/8)

Dijkstra's algorithm finds the shortest distance from one starting vertex to every other vertex in a graph with non-negative edge weights, by repeatedly fixing the nearest unfixed vertex and updating its neighbours; it runs in O(V²) with a simple array.

- **A. The problem**
  - Input: a weighted graph (weights = distances, all **≥ 0**) and a **source** vertex s.
  - Output: the shortest distance from s to every vertex, and the route.
  - Everyday version: a map app finding the quickest road from your home to every place in town.
- **B. Two key words**
  - **dist\[v\]**: the best distance to v found so far. Starts at 0 for s and ∞ for everyone else.
  - **Relaxation** of an edge u–v with weight w: if dist\[u\] + w < dist\[v\], then a shorter road to v has been found, so set dist\[v\] ← dist\[u\] + w and remember that v's previous stop is u.
- **C. Steps**
  1. Set dist\[s\] = 0 and all other dist = ∞. All vertices are "unfinished".
  2. Pick the unfinished vertex u with the **smallest** dist. Mark it finished (its distance is now final).
  3. Relax every edge from u to an unfinished neighbour.
  4. Repeat steps 2–3 until all vertices are finished.
  - It is a **greedy** algorithm: it always finalises the closest vertex next.

```
Dijkstra(G, s)
  for each vertex v:  dist[v] ← ∞;  prev[v] ← none
  dist[s] ← 0
  while some vertex is unfinished
      u ← unfinished vertex with smallest dist[u]
      mark u finished
      for each neighbour v of u that is unfinished
          if dist[u] + weight(u, v) < dist[v] then
              dist[v] ← dist[u] + weight(u, v)
              prev[v] ← u
```

- **D. Example graph** (undirected). Edges: A–B 4, A–C 2, B–C 1, B–D 5, C–D 8, C–E 10, D–E 2. Source = A.

```
        4
   A ------- B
   |       / |
 2 |    1 /  | 5
   |     /   |
   C ------- D
    \   8   /
  10 \     / 2
      \   /
        E
```

- **E. Trace** (bold = finalised in that step; ∞ = not reached yet)

| Step | Vertex finalised | dist A | dist B | dist C | dist D | dist E | What changed |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Start | – | 0 | ∞ | ∞ | ∞ | ∞ | – |
| 1 | A (0) | **0** | 4 | 2 | ∞ | ∞ | B = 0+4, C = 0+2 |
| 2 | C (2) | 0 | 3 | **2** | 10 | 12 | B: 2+1 = 3 < 4; D = 2+8; E = 2+10 |
| 3 | B (3) | 0 | **3** | 2 | 8 | 12 | D: 3+5 = 8 < 10 |
| 4 | D (8) | 0 | 3 | 2 | **8** | 10 | E: 8+2 = 10 < 12 |
| 5 | E (10) | 0 | 3 | 2 | 8 | **10** | nothing left |

- **F. Answer (read the routes backwards using prev)**

| To | Shortest distance | Route |
| --- | --- | --- |
| B | 3 | A → C → B |
| C | 2 | A → C |
| D | 8 | A → C → B → D |
| E | 10 | A → C → B → D → E |

- **G. Complexity**
  - With an adjacency matrix and a plain array for dist: V rounds × V work to find the minimum → **O(V²)**.
  - With adjacency lists and a min-heap (priority queue): **O((V + E) log V)**.
- **H. The big limitation: no negative weights**
  - Directed example: A → B weight 2, A → C weight 3, C → B weight −2.
    - Dijkstra finalises B = 2 first.
    - But A → C → B = 3 + (−2) = 1 is shorter. The answer is wrong.
  - For negative weights use the **Bellman–Ford** algorithm instead.
- **I. Dijkstra vs Prim (they look alike)**
  - Both grow a set of finished vertices and pick the "cheapest" next vertex.
  - Prim's "cheapest" = the single edge joining it to the tree.
  - Dijkstra's "cheapest" = total distance from the source.
  - Prim builds a minimum spanning tree; Dijkstra builds a shortest-path tree. They can differ.

**Exam tip:** use the dist table exactly as above, with one row per step and the finalised vertex marked. Finish with a route table; many students lose marks by giving only distances without paths.

## 11. Graph representation: adjacency matrix and adjacency list (5/8)

A computer cannot "see" a drawing, so a graph is stored either as a V × V table of 0s and 1s (adjacency matrix, Θ(V²) space) or as a list of neighbours for each vertex (adjacency list, Θ(V + E) space).

- **A. Example graph used below** (undirected, 4 vertices, 4 edges): A–B, A–C, B–C, C–D.

```
   A ----- B
    \     /
     \   /
       C ----- D
```

- **B. Adjacency matrix**
  - A square table with one row and one column per vertex.
  - Entry in row u, column v = **1** if there is an edge u–v, **0** if not.

|  | A | B | C | D |
| --- | --- | --- | --- | --- |
| **A** | 0 | 1 | 1 | 0 |
| **B** | 1 | 0 | 1 | 0 |
| **C** | 1 | 1 | 0 | 1 |
| **D** | 0 | 0 | 1 | 0 |

- **B (facts).**
  - Undirected graph → the matrix is **symmetric** (row A, column B = row B, column A).
  - Diagonal is all 0 (no self-loops).
  - **Row sum = degree** of that vertex. Row C: 1 + 1 + 0 + 1 = 3, so deg(C) = 3.
  - Weighted graph: store the weight instead of 1, and 0 or ∞ where there is no edge.
  - Space: always V × V → **Θ(V²)**, even if there are few edges.
  - "Is there an edge u–v?" → look at one cell → **O(1)**.
  - "List all neighbours of u" → scan a whole row → **O(V)**.
- **C. Directed graph in a matrix** (A → B, B → C, C → A, C → D)

| From \\ To | A | B | C | D |
| --- | --- | --- | --- | --- |
| **A** | 0 | 1 | 0 | 0 |
| **B** | 0 | 0 | 1 | 0 |
| **C** | 1 | 0 | 0 | 1 |
| **D** | 0 | 0 | 0 | 0 |

- **C (facts).**
  - Not symmetric in general.
  - **Row sum = out-degree**; **column sum = in-degree**. Row C sum = 2 (C → A, C → D).
- **D. Adjacency list**
  - For each vertex, keep a list (usually a linked list) of just its neighbours.
  - Undirected example:
    - A → B → C
    - B → A → C
    - C → A → B → D
    - D → C
  - Directed example (A → B, B → C, C → A, C → D):
    - A → B
    - B → C
    - C → A → D
    - D → (empty)
  - Weighted graph: each list entry stores (neighbour, weight), e.g. A → (B, 4) → (C, 2).
  - Undirected graph: each edge appears **twice** (once in each end's list), so total entries = 2E.
  - Space: **Θ(V + E)**.
  - "Is there an edge u–v?" → walk u's list → **O(degree of u)**.
  - "List all neighbours of u" → **O(degree of u)**, very fast.
- **E. Comparison**

| Point | Adjacency matrix | Adjacency list |
| --- | --- | --- |
| Structure | V × V table of 0/1 (or weights) | Array of V lists of neighbours |
| Space | Θ(V²) | Θ(V + E) |
| Check if edge u–v exists | O(1) | O(degree of u) |
| Find all neighbours of u | O(V) | O(degree of u) |
| Add an edge | O(1) | O(1) |
| DFS / BFS time | Θ(V²) | Θ(V + E) |
| Best for | Dense graphs (many edges) | Sparse graphs (few edges), most real graphs |
| Undirected graph shows as | Symmetric matrix | Each edge stored twice |

**Exam tip:** when asked to "represent" a graph, give **both** forms for the given graph, then add the comparison table. Label rows and columns of the matrix clearly.

## 12. Divide and conquer: Karatsuba and Strassen multiplication (5/8)

Divide and conquer splits a problem into smaller copies, solves them recursively and combines the answers; Karatsuba multiplies big numbers with 3 half-size multiplications instead of 4 (Θ(n^1.585)), and Strassen multiplies matrices with 7 half-size multiplications instead of 8 (Θ(n^2.81)).

- **A. The divide-and-conquer pattern**
  1. **Divide** the problem into smaller sub-problems of the same type.
  2. **Conquer** each sub-problem recursively (tiny ones are solved directly).
  3. **Combine** the sub-answers into the full answer.
  - Time follows **T(n) = a·T(n/b) + f(n)**, solved with the Master theorem (topic 2).
  - Examples: binary search, merge sort, quick sort, Karatsuba, Strassen.
  - The trick in both algorithms below: **reduce the number of sub-problems (a)**, even at the cost of extra additions. Fewer recursive multiplications beat everything else for big n.
- **B. Karatsuba: multiplying large numbers**
  - **B1. The school method** multiplies every digit of one number by every digit of the other: n-digit numbers need n² digit multiplications → Θ(n²).
  - **B2. Split each number into halves.** For n-digit numbers x and y, with m = n/2:
    - x = a × 10^m + b, y = c × 10^m + d (a, c = left halves; b, d = right halves).
    - Then x × y = ac × 10^(2m) + (ad + bc) × 10^m + bd.
    - That needs 4 half-size multiplications (ac, ad, bc, bd) → T(n) = 4T(n/2) + n → still Θ(n²). No gain yet.
  - **B3. Karatsuba's trick**: get (ad + bc) with only one extra multiplication:
    - ad + bc = (a + b)(c + d) − ac − bd.
    - So only **3 multiplications**: ac, bd and (a + b)(c + d).

```latex
xy = ac\cdot 10^{2m} + \big[(a+b)(c+d) - ac - bd\big]\cdot 10^{m} + bd
```

- **B4. Worked example 1: 1234 × 5678** (n = 4, m = 2)
  - a = 12, b = 34, c = 56, d = 78.
  - ac = 12 × 56 = **672**
  - bd = 34 × 78 = **2652**
  - (a + b)(c + d) = 46 × 134 = **6164**
  - ad + bc = 6164 − 672 − 2652 = **2840**
  - Answer = 672 × 10⁴ + 2840 × 10² + 2652 = 6,720,000 + 284,000 + 2,652 = **7,006,652** ✔
- **B5. Worked example 2: 23 × 14** (n = 2, m = 1)
  - a = 2, b = 3, c = 1, d = 4.
  - ac = 2; bd = 12; (a + b)(c + d) = 5 × 5 = 25; ad + bc = 25 − 2 − 12 = 11.
  - Answer = 2 × 100 + 11 × 10 + 12 = **322** ✔
- **B6. Complexity**
  - T(n) = 3T(n/2) + cn (the additions and shifts cost about n).
  - Master theorem: a = 3, b = 2 → n^(log₂ 3) ≈ **n^1.585**. Faster than n².
- **C. Strassen: multiplying matrices**
  - **C1. Ordinary method**: for two n × n matrices, each of the n² answer entries needs n multiplications → **n³ multiplications**. For 2 × 2 matrices: 8 multiplications.
  - **C2. Split into quarters.** Each n × n matrix becomes four (n/2) × (n/2) blocks:
    - A = \[A11 A12 ; A21 A22\], B = \[B11 B12 ; B21 B22\], C = A × B.
    - Plain block method: 8 block multiplications → T(n) = 8T(n/2) + n² → still Θ(n³).
  - **C3. Strassen's 7 products** (memorise these):

```
M1 = (A11 + A22) × (B11 + B22)
M2 = (A21 + A22) ×  B11
M3 =  A11        × (B12 − B22)
M4 =  A22        × (B21 − B11)
M5 = (A11 + A12) ×  B22
M6 = (A21 − A11) × (B11 + B12)
M7 = (A12 − A22) × (B21 + B22)

C11 = M1 + M4 − M5 + M7        C12 = M3 + M5
C21 = M2 + M4                  C22 = M1 − M2 + M3 + M6
```

- **C4. Memory aids**
  - C12 and C21 are the easy ones: two M's each (C12 = M3 + M5, C21 = M2 + M4).
  - C11 and C22 use four M's each and both start with M1.
  - M1 uses both diagonals (11 and 22). M5 and M2 contain "top row of A" and "bottom row of A" sums.
- **C5. Worked example:** A = \[1 3 ; 7 5\], B = \[6 8 ; 4 2\]
  - So A11 = 1, A12 = 3, A21 = 7, A22 = 5; B11 = 6, B12 = 8, B21 = 4, B22 = 2.

| Product | Calculation | Value |
| --- | --- | --- |
| M1 | (1 + 5) × (6 + 2) = 6 × 8 | 48 |
| M2 | (7 + 5) × 6 = 12 × 6 | 72 |
| M3 | 1 × (8 − 2) = 1 × 6 | 6 |
| M4 | 5 × (4 − 6) = 5 × (−2) | −10 |
| M5 | (1 + 3) × 2 = 4 × 2 | 8 |
| M6 | (7 − 1) × (6 + 8) = 6 × 14 | 84 |
| M7 | (3 − 5) × (4 + 2) = (−2) × 6 | −12 |

- **C5 (combine).**
  - C11 = 48 + (−10) − 8 + (−12) = **18**
  - C12 = 6 + 8 = **14**
  - C21 = 72 + (−10) = **62**
  - C22 = 48 − 72 + 6 + 84 = **66**
  - Result C = \[18 14 ; 62 66\]. Check by the ordinary method: 1×6 + 3×4 = 18, 1×8 + 3×2 = 14, 7×6 + 5×4 = 62, 7×8 + 5×2 = 66 ✔
- **C6. Operation count and complexity**
  - For 2 × 2: **7 multiplications and 18 additions/subtractions** (10 inside the M's, 8 in the C's), versus 8 multiplications and 4 additions normally.
  - Recurrence: T(n) = 7T(n/2) + Θ(n²).
  - Master theorem: a = 7, b = 2 → n^(log₂ 7) ≈ **n^2.81**. Faster than n³ for large n.
  - Drawbacks: more additions, more memory, and only worth it for large matrices.

**Exam tip:** write the 7 Strassen formulas from memory first, then fill the M-table, then the four C's, then verify with the ordinary method. For Karatsuba, show a, b, c, d, the three products and the final assembly.

## 13. Algorithm basics: definition, properties, time vs space complexity (5/8)

An algorithm is a finite list of clear, unambiguous steps that turns any valid input into the correct output in a finite time; we judge it by its time complexity (how many steps) and space complexity (how much memory), both as functions of the input size n.

- **A. Definition**
  - An **algorithm** is a finite sequence of unambiguous instructions for solving a problem: for every valid input it produces the required output in a finite amount of time.
  - The word comes from the name of the 9th-century Persian mathematician al-Khwarizmi.
- **B. The five properties (Knuth's list, very frequently asked)**
  1. **Input**: takes zero or more inputs.
  2. **Output**: produces at least one output.
  3. **Definiteness**: every step is precise and has only one meaning. ("Add a pinch of salt" is not definite.)
  4. **Finiteness**: it always stops after a finite number of steps. ("Keep counting upwards" never stops.)
  5. **Effectiveness**: every step is simple enough to be done exactly, in principle with pencil and paper.
  - Often added: **Correctness** (right answer for every valid input) and **Generality** (works for all inputs of the problem, not just one).
- **C. Example algorithm: find the largest of n numbers**

```
FindMax(A[1..n])
  max ← A[1]
  for i ← 2 to n
      if A[i] > max then max ← A[i]
  return max
```

- **C (checking the properties).**
  - Input: the array A. Output: max. Definite: each line has one meaning. Finite: the loop runs n − 1 times. Effective: only comparisons and copying.
  - Trace on \[4, 9, 2, 7\]: max = 4 → 9 > 4 so max = 9 → 2 no → 7 no → answer 9.
  - Comparisons: always n − 1 → Θ(n).
- **D. Algorithm vs program**

| Algorithm | Program |
| --- | --- |
| An idea or method, written in steps or pseudocode | That method written in a real programming language (C, Python…) |
| Independent of computer and language | Depends on language and machine |
| Must always finish (finiteness) | May run forever (e.g. an operating system) |
| Designed and analysed | Implemented and tested |

- **E. Ways to write an algorithm**: plain English steps, a flowchart (boxes and arrows), or pseudocode.
- **F. Steps in designing an algorithm**
  1. Understand the problem.
  2. Choose a design technique (brute force, divide and conquer, greedy, backtracking…).
  3. Write the algorithm.
  4. Prove it is correct.
  5. Analyse its efficiency.
  6. Code and test it.
- **G. Time complexity**
  - How the **number of basic operations** grows with input size n. Written T(n).
  - We count steps, not seconds, because seconds depend on the computer; step counts do not.
  - Example: FindMax does n − 1 comparisons → T(n) = n − 1 = Θ(n).
- **H. Space complexity**
  - How much **memory** the algorithm needs as n grows. Written S(n).
  - S(P) = **fixed part c** (the code, simple variables, constants) + **variable part Sₚ** (memory that depends on n, e.g. arrays, recursion stack).
  - Example: FindMax stores the array (n boxes) + 2 variables (max, i). Extra space beyond the input = Θ(1).
  - Example: recursive factorial(n) uses n stack frames → Θ(n) space.
- **I. Best, worst and average case**
  - Same algorithm, different inputs of the same size n, different step counts.
  - **Best case**: the fewest steps over all inputs of size n (linear search: key is first, 1 step).
  - **Worst case**: the most steps (linear search: key last or absent, n steps). The usual guarantee.
  - **Average case**: the expected steps over typical inputs (linear search: (n + 1)/2).
- **J. Time vs space: comparison**

| Point | Time complexity | Space complexity |
| --- | --- | --- |
| Measures | Number of basic operations | Amount of memory used |
| Depends on | Loops, recursion, comparisons | Variables, arrays, recursion stack |
| Written as | T(n), e.g. Θ(n²) | S(n), e.g. Θ(n) |
| Example (bubble sort) | Θ(n²) | Θ(1) extra |
| Example (merge sort) | Θ(n log n) | Θ(n) extra |

- **K. Time–space trade-off**
  - Often you can save time by using more memory, or save memory by spending more time.
    - Fibonacci: plain recursion uses little extra memory but exponential time; storing earlier answers in a table uses Θ(n) memory but only Θ(n) time (topic 16).
    - A lookup table of precomputed answers is fast but takes space.

**Exam tip:** "Define algorithm and explain its properties" is a guaranteed few marks: write the definition, list all five properties with a one-line example each, and add the FindMax example.

## 14. Mathematical induction proofs: sum of n, sum of squares (4/8)

Mathematical induction proves a formula for every n by showing it holds for the first value (base case) and that "true for k" always forces "true for k + 1" (inductive step); the two standard exam proofs are 1 + 2 + … + n = n(n+1)/2 and 1² + 2² + … + n² = n(n+1)(2n+1)/6.

- **A. The domino idea**
  - Picture an endless row of dominoes.
    - If the **first** one falls (base case), and
    - whenever **any** domino falls it knocks over the **next** (inductive step),
    - then **all** dominoes fall.
- **B. The four-part template (write all four headings in the exam)**
  1. **Statement**: name it P(n) and write it out.
  2. **Base case**: check P(1) by putting n = 1 into both sides.
  3. **Inductive hypothesis**: assume P(k) is true for some k ≥ 1.
  4. **Inductive step**: using that assumption, prove P(k + 1). Then conclude "by induction, P(n) is true for all n ≥ 1".
- **C. Proof 1: sum of the first n natural numbers**
  - **Statement**: P(n): 1 + 2 + 3 + … + n = n(n + 1)/2.
  - **Base case (n = 1)**: LHS = 1. RHS = 1 × 2 / 2 = 1. Equal, so P(1) is true.
  - **Hypothesis**: assume 1 + 2 + … + k = k(k + 1)/2.
  - **Step**: we must show 1 + 2 + … + k + (k + 1) = (k + 1)(k + 2)/2.
    - LHS = \[1 + 2 + … + k\] + (k + 1)
    - = k(k + 1)/2 + (k + 1)  (using the hypothesis)
    - = (k + 1) × \[k/2 + 1\]  (take (k + 1) out as a common factor)
    - = (k + 1)(k + 2)/2 = RHS. ✔
  - **Conclusion**: by induction, the formula holds for all n ≥ 1.
  - Quick check: n = 4 → 1 + 2 + 3 + 4 = 10 and 4 × 5 / 2 = 10.
- **D. Proof 2: sum of the first n squares**
  - **Statement**: P(n): 1² + 2² + … + n² = n(n + 1)(2n + 1)/6.
  - **Base case (n = 1)**: LHS = 1. RHS = 1 × 2 × 3 / 6 = 1. True.
  - **Hypothesis**: assume 1² + 2² + … + k² = k(k + 1)(2k + 1)/6.
  - **Step**: we must reach (k + 1)(k + 2)(2k + 3)/6. (That is the formula with n = k + 1, since 2(k + 1) + 1 = 2k + 3.)
    - LHS = k(k + 1)(2k + 1)/6 + (k + 1)²
    - = (k + 1) × \[k(2k + 1) + 6(k + 1)\] / 6  (common factor (k + 1), common denominator 6)
    - = (k + 1) × \[2k² + k + 6k + 6\] / 6
    - = (k + 1)(2k² + 7k + 6)/6
    - = (k + 1)(k + 2)(2k + 3)/6  (because (k + 2)(2k + 3) = 2k² + 7k + 6) = RHS. ✔
  - **Conclusion**: true for all n ≥ 1.
  - Quick check: n = 3 → 1 + 4 + 9 = 14 and 3 × 4 × 7 / 6 = 14.

```latex
\sum_{i=1}^{n} i = \frac{n(n+1)}{2} \qquad \sum_{i=1}^{n} i^2 = \frac{n(n+1)(2n+1)}{6}
```

- **E. Bonus proofs (same template, in case they are asked)**
  - **Sum of cubes**: 1³ + 2³ + … + n³ = \[n(n + 1)/2\]².
    - Base: 1 = (1 × 2 / 2)² = 1.
    - Step: k²(k + 1)²/4 + (k + 1)³ = (k + 1)² × \[k² + 4(k + 1)\]/4 = (k + 1)²(k + 2)²/4. ✔
  - **Powers of 2**: 1 + 2 + 4 + … + 2^(n−1) = 2ⁿ − 1.
    - Base: 1 = 2 − 1.
    - Step: (2^k − 1) + 2^k = 2 × 2^k − 1 = 2^(k+1) − 1. ✔
  - **Sum of odd numbers**: 1 + 3 + 5 + … + (2n − 1) = n².
    - Step: k² + (2k + 1) = (k + 1)². ✔
- **F. Why this appears in an algorithms course**
  - Counting loop steps: bubble sort's comparisons (n−1) + … + 1 = n(n−1)/2 come straight from Proof 1.
  - Proving recurrence answers (guess-and-prove, topic 2) and proving algorithms correct.
- **G. Common mistakes**
  - Skipping the base case. Without it, the proof is incomplete.
  - Assuming P(k + 1) instead of proving it.
  - Forgetting to write the target expression for k + 1 before starting the algebra.

**Exam tip:** write the four headings (Statement, Base case, Inductive hypothesis, Inductive step) every time, and underline where you use the hypothesis.

## 15. Backtracking and branch and bound (4/8)

Both techniques search a tree of possible choices and cut off branches that cannot help: backtracking abandons a partial solution as soon as it breaks a rule (e.g. 4-queens), while branch and bound abandons a branch whose best possible value cannot beat the best answer already found (e.g. 0/1 knapsack).

- **A. The shared setting: a state-space tree**
  - Some problems are solved by making a series of choices (put queen 1 here, queen 2 there…).
  - All possible choice sequences form a tree: root = no choice made; each level = one more choice; leaves = complete candidates.
  - Trying every leaf (brute force) is far too slow. Both techniques **prune** (cut off) useless branches early.
- **B. Backtracking**
  - **B1. Idea**: build the solution one piece at a time. After each piece, check: can this still lead to a valid solution? If not, undo the last piece (**backtrack**) and try the next option.
    - Like solving a maze or a Sudoku with a pencil and an eraser.
  - **B2. How it explores**: depth-first (topic 7) through the state-space tree.
  - **B3. Used for**: problems asking for a **valid** (feasible) solution, or all of them: n-queens, sum of subsets, graph colouring, Hamiltonian cycle.
  - **B4. Worked example: 4-queens.** Place 4 queens on a 4 × 4 board so that no two share a row, column or diagonal. Place one queen per row; Q(r) = column of the queen in row r. Two queens clash diagonally if |row difference| = |column difference|.

| Step | Try | Result |
| --- | --- | --- |
| 1 | Q1 = 1 | OK |
| 2 | Q2 = 1, 2 | Column clash, diagonal clash |
| 3 | Q2 = 3 | OK |
| 4 | Q3 = 1, 2, 3, 4 | All clash. Dead end, backtrack to row 2 |
| 5 | Q2 = 4 | OK |
| 6 | Q3 = 1 (clash), Q3 = 2 | Q3 = 2 OK |
| 7 | Q4 = 1, 2, 3, 4 | All clash. Backtrack to row 3 |
| 8 | Q3 = 3, 4 | Both clash. Backtrack to row 2 (no columns left), then to row 1 |
| 9 | Q1 = 2 | OK |
| 10 | Q2 = 1, 2, 3 clash; Q2 = 4 | Q2 = 4 OK |
| 11 | Q3 = 1 | OK |
| 12 | Q4 = 1, 2 clash; Q4 = 3 | OK: **solution found (2, 4, 1, 3)** |

- **B4 (result).** Board for (2, 4, 1, 3):

```
  . Q . .
  . . . Q
  Q . . .
  . . Q .
```

- **B4 (note).** The only other solution is its mirror image, (3, 1, 4, 2).
- **C. Branch and bound**
  - **C1. Idea**: for **optimisation** problems (find the maximum or minimum). At every node, compute a **bound** = the best value any solution below this node could possibly reach.
    - If the bound is no better than the best complete solution found so far, **prune** that node.
  - **C2. How it explores**: usually breadth-first, or **best-first** (always expand the node with the most promising bound, using a priority queue).
  - **C3. Used for**: 0/1 knapsack, travelling salesperson (TSP), assignment problem, job sequencing.
  - **C4. Worked example: 0/1 knapsack** (take whole items only). Capacity W = 10.

| Item | Weight | Value | Value/weight |
| --- | --- | --- | --- |
| 1 | 4 | 40 | 10 |
| 2 | 7 | 42 | 6 |
| 3 | 5 | 25 | 5 |
| 4 | 3 | 12 | 4 |

- **C4 (the bound).** Upper bound at a node = value so far + (capacity left) × (best ratio among the remaining items). Items are already sorted by ratio.

| Node | Decisions so far | Weight | Value | Upper bound | What happens |
| --- | --- | --- | --- | --- | --- |
| Root | none | 0 | 0 | 0 + 10 × 10 = 100 | Expand |
| 1 | take item 1 | 4 | 40 | 40 + 6 × 6 = 76 | Expand (best bound) |
| 2 | skip item 1 | 0 | 0 | 0 + 10 × 6 = 60 | Wait |
| 3 | take 1, take 2 | 11 | – | – | Over capacity: prune |
| 4 | take 1, skip 2 | 4 | 40 | 40 + 6 × 5 = 70 | Expand |
| 5 | take 1, 3 | 9 | 65 | 65 + 1 × 4 = 69 | Expand |
| 6 | take 1, skip 3 | 4 | 40 | 40 + 6 × 4 = 64 | Wait |
| 7 | take 1, 3, 4 | 12 | – | – | Over capacity: prune |
| 8 | take 1, 3, skip 4 | 9 | 65 | 65 | Complete solution: best so far = 65 |
| 6, 2 | – | – | – | 64 and 60 | Both below 65: prune |

- **C4 (result).** Best choice: items 1 and 3, weight 9, **value 65**. Only a handful of nodes were examined out of 16 possible subsets.
- **D. Backtracking vs branch and bound**

| Point | Backtracking | Branch and bound |
| --- | --- | --- |
| Problem type | Feasibility: find a valid solution (or all) | Optimisation: find the best (min/max) solution |
| Search order | Depth-first | Breadth-first or best-first (least-cost) |
| Prunes a node when | It breaks a rule (not feasible) | Its bound cannot beat the best found so far (and when not feasible) |
| Extra work per node | A feasibility check | A feasibility check + computing a bound |
| Data structure | Stack / recursion | Queue or priority queue |
| Classic examples | n-queens, sum of subsets, graph colouring, Hamiltonian cycle | 0/1 knapsack, TSP, assignment problem |

**Exam tip:** for backtracking, draw the state-space tree (or a step table like the 4-queens one) and mark dead ends with ×. For branch and bound, write the bound formula first, then show each node's bound and why it was pruned.

## 16. Counting operations: matrix addition and multiplication, polynomial evaluation, Fibonacci (4/8)

To analyse an algorithm, pick its basic operation and count how many times it runs: n × n matrix addition does n² additions, matrix multiplication n³ multiplications, Horner's rule evaluates a degree-n polynomial with only n multiplications, and recursive Fibonacci is exponential while the loop version is linear.

- **A. Counting rules for loops**
  - One loop running n times → n operations.
  - Two nested loops, each 1 to n → n × n = n².
  - Three nested loops → n³.
  - Inner loop from i to n → n + (n−1) + … + 1 = n(n+1)/2.
  - A loop that doubles i each time (1, 2, 4, 8 … n) → about log₂ n.
- **B. Matrix addition**
  - A matrix is a table of numbers. Adding two matrices = adding matching entries.

```
MatrixAdd(A, B, n)              // n × n matrices
  for i ← 1 to n
      for j ← 1 to n
          C[i][j] ← A[i][j] + B[i][j]
```

- **B (count).**
  - Basic operation: one addition. It runs once for every (i, j) pair → **n² additions → Θ(n²)**.
  - For an m × n matrix: m × n additions.
  - Example: 2 × 2 matrices → 4 additions. \[1 2 ; 3 4\] + \[5 6 ; 7 8\] = \[6 8 ; 10 12\].
- **C. Matrix multiplication**
  - Entry C\[i\]\[j\] = (row i of A) · (column j of B) = A\[i\]\[1\]×B\[1\]\[j\] + A\[i\]\[2\]×B\[2\]\[j\] + … + A\[i\]\[n\]×B\[n\]\[j\].

```
MatrixMultiply(A, B, n)
  for i ← 1 to n
      for j ← 1 to n
          C[i][j] ← 0
          for k ← 1 to n
              C[i][j] ← C[i][j] + A[i][k] × B[k][j]
```

- **C (count).**
  - Three nested loops → **n³ multiplications** and n³ additions (or n²(n − 1) additions if each entry starts from the first product instead of 0) → **Θ(n³)**.
  - 2 × 2 case: 8 multiplications, 4 additions. Example: \[1 2 ; 3 4\] × \[5 6 ; 7 8\] = \[1×5+2×7, 1×6+2×8 ; 3×5+4×7, 3×6+4×8\] = \[19 22 ; 43 50\].
  - Strassen (topic 12) cuts this to about n^2.81.
- **D. Polynomial evaluation**: find p(x) = aₙxⁿ + … + a₂x² + a₁x + a₀ for a given x.
  - **D1. Brute force** (compute every power from scratch)
    - Term aᵢxⁱ needs i multiplications (i − 1 for the power, 1 for the coefficient).
    - Total = 1 + 2 + … + n = **n(n + 1)/2 multiplications**, n additions → **Θ(n²)**.
  - **D2. Better: keep a running power** (x² = x × x, x³ = x² × x, …)
    - 2 multiplications per term → about **2n multiplications**, n additions → Θ(n).
  - **D3. Horner's rule (best)**: rewrite p(x) with nested brackets:
    - p(x) = ( … ((aₙx + aₙ₋₁)x + aₙ₋₂)x + … )x + a₀

```
Horner(a[0..n], x)
  p ← a[n]
  for i ← n − 1 down to 0
      p ← p × x + a[i]
  return p
```

- **D3 (worked example).** p(x) = 2x³ − 6x² + 2x − 1 at x = 3.

| Step | Coefficient added | p ← p × 3 + coefficient | p |
| --- | --- | --- | --- |
| Start | – | p = 2 | 2 |
| 1 | −6 | 2 × 3 − 6 | 0 |
| 2 | 2 | 0 × 3 + 2 | 2 |
| 3 | −1 | 2 × 3 − 1 | **5** |

- **D3 (check and count).**
  - Check directly: 2 × 27 − 6 × 9 + 2 × 3 − 1 = 54 − 54 + 6 − 1 = 5 ✔
  - Horner uses exactly **n multiplications and n additions** (here 3 and 3) → **Θ(n)**.

| Method | Multiplications | Additions | Order |
| --- | --- | --- | --- |
| Brute force | n(n+1)/2 | n | Θ(n²) |
| Running power | 2n | n | Θ(n) |
| Horner's rule | n | n | Θ(n) |

- **E. Fibonacci numbers**
  - Definition: F(0) = 0, F(1) = 1, F(n) = F(n−1) + F(n−2).
  - Sequence: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55 …
  - **E1. Recursive algorithm**

```
Fib(n)
  if n ≤ 1 then return n
  return Fib(n − 1) + Fib(n − 2)
```

- **E1 (count).**
  - Additions A(n) = A(n−1) + A(n−2) + 1, with A(0) = A(1) = 0. Solution: **A(n) = F(n+1) − 1**.
  - Total calls = 2F(n+1) − 1. For Fib(5): 7 additions, 15 calls.
  - It recomputes the same values again and again. Fib(5) computes Fib(3) twice and Fib(2) three times.

```
                  Fib(5)
            /               \
        Fib(4)             Fib(3)
       /      \            /     \
   Fib(3)   Fib(2)     Fib(2)   Fib(1)
   /    \    /   \     /   \
Fib(2) F(1) F(1) F(0) F(1) F(0)
 /   \
F(1) F(0)
```

- **E1 (growth).** F(n) grows like 1.618ⁿ (the golden ratio φ), so the time is **exponential, Θ(φⁿ)**. Fib(50) would take billions of calls.
- **E2. Iterative (loop) algorithm**

```
FibIter(n)
  if n ≤ 1 then return n
  a ← 0;  b ← 1
  for i ← 2 to n
      c ← a + b;  a ← b;  b ← c
  return b
```

- **E2 (count).** Exactly **n − 1 additions → Θ(n)** time and Θ(1) extra space (or Θ(n) if you store the whole sequence in an array).
  - Trace for n = 6: (a, b) = (0,1) → (1,1) → (1,2) → (2,3) → (3,5) → (5,8). Answer F(6) = 8, after 5 additions.
  - (An advanced method using matrix powers gets F(n) in Θ(log n).)

| Fibonacci method | Additions for F(n) | Time | Extra space |
| --- | --- | --- | --- |
| Recursive | F(n+1) − 1 | Θ(φⁿ), exponential | Θ(n) recursion stack |
| Iterative | n − 1 | Θ(n) | Θ(1) |

**Exam tip:** always name the basic operation first ("basic operation: multiplication"), then set up the count as a sum over the loops, then simplify and give the Θ order.

## 17. Quick sort: trace, partition in Θ(n), best case Θ(n log n) (3/8)

Quick sort picks a pivot, partitions the list so smaller items go left and larger go right (Θ(n) work), then sorts each side recursively; with even splits it runs in Θ(n log n), but an already-sorted list with a first-element pivot gives the worst case Θ(n²).

- **A. Idea in plain words**
  - Pick one item, the **pivot** (here: the first item).
  - Rearrange the list so everything smaller than the pivot is on its left and everything larger is on its right. The pivot is now in its **final** place.
  - Repeat the same thing on the left part and the right part. Parts of size 0 or 1 are already sorted.
  - A divide-and-conquer algorithm (topic 12): the hard work is in the **divide** (partition) step; there is nothing to combine.
- **B. The partition step** (Hoare-style, pivot = first element)
  1. p = A\[low\] (the pivot). Pointer i starts just after the pivot; pointer j starts at the end.
  2. Move i right while A\[i\] < p (stop at an item ≥ p).
  3. Move j left while A\[j\] > p (stop at an item ≤ p).
  4. If i < j, swap A\[i\] and A\[j\], then continue from step 2.
  5. If i ≥ j (pointers crossed), swap the pivot with A\[j\]. The pivot is now at position j. Done.

```
QuickSort(A, low, high)
  if low < high then
      s ← Partition(A, low, high)     // pivot ends at position s
      QuickSort(A, low, s − 1)
      QuickSort(A, s + 1, high)

Partition(A, low, high)
  p ← A[low];  i ← low;  j ← high + 1
  repeat
      repeat i ← i + 1 until A[i] ≥ p
      repeat j ← j − 1 until A[j] ≤ p
      if i < j then swap A[i], A[j]
  until i ≥ j
  swap A[low], A[j]
  return j
```

- **C. Full trace: sort \[5, 3, 1, 9, 8, 2, 4, 7\]** (positions 1 to 8)

| Step | i stops at | j stops at | Action | List after |
| --- | --- | --- | --- | --- |
| Pivot 5 | 9 (pos 4) | 4 (pos 7) | i < j: swap 9 and 4 | 5, 3, 1, 4, 8, 2, 9, 7 |
| Continue | 8 (pos 5) | 2 (pos 6) | i < j: swap 8 and 2 | 5, 3, 1, 4, 2, 8, 9, 7 |
| Continue | 8 (pos 6) | 2 (pos 5) | Crossed: swap pivot 5 with 2 | 2, 3, 1, 4, **5**, 8, 9, 7 |
| Left part \[2, 3, 1, 4\], pivot 2 | 3 (pos 2) | 1 (pos 3) | Swap 3 and 1 | 2, 1, 3, 4 |
| Continue | 3 (pos 3) | 1 (pos 2) | Crossed: swap pivot 2 with 1 | 1, **2**, 3, 4 |
| Part \[3, 4\], pivot 3 | 4 (pos 2) | 3 (pos 1) | Crossed: pivot stays | **3**, 4 |
| Right part \[8, 9, 7\], pivot 8 | 9 (pos 2) | 7 (pos 3) | Swap 9 and 7 | 8, 7, 9 |
| Continue | 9 (pos 3) | 7 (pos 2) | Crossed: swap pivot 8 with 7 | 7, **8**, 9 |

- **C (result).** Sorted list: **1, 2, 3, 4, 5, 7, 8, 9**.
- **D. Why partition is Θ(n)**
  - i only moves right and j only moves left, and they stop once they cross.
  - So each of the n items is compared with the pivot about once: **n + 1 comparisons if the pointers cross, n if they meet** → Θ(n).
- **E. Best case: Θ(n log n)**
  - Happens when every pivot lands exactly in the middle, splitting the list into two equal halves.
  - Recurrence: **C(n) = 2C(n/2) + n**, C(1) = 0.
  - Master theorem (a = 2, b = 2, f(n) = n = n^(log₂ 2)) → case 2 → **Θ(n log n)**. For n a power of 2, exactly C(n) = n log₂ n.
  - Recursion-tree view: log₂ n levels, each doing about n comparisons (same picture as topic 2, example 5).
- **F. Worst case: Θ(n²)**
  - Happens when every pivot is the smallest (or largest) item, e.g. an **already sorted** list with the first element as pivot. Each split leaves 0 items on one side and n − 1 on the other.
  - C(n) = (n + 1) + n + … + 3 = (n + 1)(n + 2)/2 − 3 → **Θ(n²)**.
- **G. Average case: Θ(n log n)**, about 1.39 n log₂ n comparisons. This is why quick sort is fast in practice.
- **H. Avoiding the worst case**
  - Pick a **random** pivot, or the **median of three** (the middle value of the first, middle and last items).
- **I. Properties**
  - In place: only O(log n) extra space on average, for the recursion stack.
  - **Not stable**: equal items may change order.
- **J. Quick sort among the other sorts**

| Algorithm | Best | Average | Worst | Extra space |
| --- | --- | --- | --- | --- |
| Bubble sort | Θ(n) with flag | Θ(n²) | Θ(n²) | Θ(1) |
| Quick sort | Θ(n log n) | Θ(n log n) | Θ(n²) | Θ(log n) average |
| Merge sort | Θ(n log n) | Θ(n log n) | Θ(n log n) | Θ(n) |

**Exam tip:** trace one full partition in detail (show where i and j stop and each swap), then show the sub-lists. For analysis, write the best-case recurrence and solve it with the Master theorem.

## Last-minute revision cheat sheet

Read this page the night before the exam: every complexity and formula from the 17 topics, in one place.

- **A. Complexities to remember**

| Algorithm | Best case | Worst case | Note |
| --- | --- | --- | --- |
| Linear search | Θ(1) | Θ(n) | Average (n+1)/2 comparisons |
| Binary search | Θ(1) | Θ(log n) | List must be sorted |
| Bubble sort | Θ(n) with flag | Θ(n²) | n(n−1)/2 comparisons, stable |
| Quick sort | Θ(n log n) | Θ(n²) | Average Θ(n log n); partition Θ(n) |
| Merge sort | Θ(n log n) | Θ(n log n) | T(n) = 2T(n/2) + n |
| Euclid's GCD | Θ(1) | Θ(log n) | Worst on consecutive Fibonacci numbers |
| DFS / BFS | Θ(V + E) list | Θ(V²) matrix | Stack / queue |
| Kruskal | – | O(E log E) | Sort edges, union–find |
| Prim | – | O(V²) or O(E log V) | Grows one tree |
| Dijkstra | – | O(V²) or O((V+E) log V) | No negative weights |
| Fractional knapsack | – | O(n log n) | Sort by profit/weight |
| Change-making (greedy) | – | O(k) | k = number of denominations |
| Matrix addition | Θ(n²) | Θ(n²) | n² additions |
| Matrix multiplication | Θ(n³) | Θ(n³) | n³ multiplications |
| Strassen | Θ(n^2.81) | Θ(n^2.81) | 7 multiplications, 18 additions (2 × 2) |
| Karatsuba | Θ(n^1.585) | Θ(n^1.585) | 3 half-size multiplications |
| Horner's rule | Θ(n) | Θ(n) | n multiplications, n additions |
| Fibonacci, recursive | – | Θ(φⁿ) | F(n+1) − 1 additions |
| Fibonacci, loop | Θ(n) | Θ(n) | n − 1 additions |

- **B. Formulas to know by heart**
  - Order of growth: 1 < log n < n < n log n < n² < n³ < 2ⁿ < n!
  - Big-O: f(n) ≤ c·g(n) for n ≥ n₀. Big-Ω: f(n) ≥ c·g(n). Big-Θ: c₁g(n) ≤ f(n) ≤ c₂g(n).
  - Master theorem, T(n) = aT(n/b) + n^d: a < b^d → Θ(n^d); a = b^d → Θ(n^d log n); a > b^d → Θ(n^(log\_b a)).
  - 1 + 2 + … + n = n(n+1)/2. 1² + 2² + … + n² = n(n+1)(2n+1)/6.
  - gcd(m, n) = gcd(n, m mod n); gcd(m, 0) = m.
  - Karatsuba middle term: ad + bc = (a+b)(c+d) − ac − bd.
  - Strassen: C11 = M1 + M4 − M5 + M7, C12 = M3 + M5, C21 = M2 + M4, C22 = M1 − M2 + M3 + M6.
  - Tree on n vertices: n − 1 edges. Complete graph Kₙ: n(n−1)/2 edges. Sum of degrees = 2E.
- **C. Five-mark answer checklist**
  - Definition or idea in one or two lines.
  - Algorithm in pseudocode.
  - A worked trace in a table.
  - Complexity with a one-line reason.
  - A comparison table if the question says "compare" or "differentiate".

## Sources

- [The Outline Note-Taking Method: Examples & Step-by-Step Guide, e-student.org](https://e-student.org/outline-note-taking-method/): the outline method's structure, six steps, pros and its weakness for maths-heavy subjects.
- The algorithm content follows the standard treatment in IGNOU's BCA course and the common reference text by Levitin (Introduction to the Design and Analysis of Algorithms). Every worked example above was re-computed by hand for these notes.

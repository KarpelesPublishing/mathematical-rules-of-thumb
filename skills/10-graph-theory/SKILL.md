---
name: math-thumb-graph-theory
description: "Apply Chapter 10 (Graph Theory: Structural Tests for Networks) of Mathematical Rules of Thumb to solve, check, or teach problems. Use it to use a graph obstruction or structure test without mistaking a necessary condition for a proof."
---

# Chapter 10. Graph Theory: Structural Tests for Networks

Apply Chapter 10 of *Mathematical Rules of Thumb* to the reader's own problem. The chapter notebook, [10-graph-theory.ipynb](../../notebooks/10-graph-theory.ipynb), works through calculations from the chapter; use it as a template and replace its inputs with the reader's numbers.

## Start from the reader's task

Infer solve, learn, or audit mode from the request. In solve mode, use their supplied numbers and target; in learn mode, use their chosen rule and the notebook; in audit mode, inspect their actual calculation before replacing it. Gather only missing information that changes the choice: Vertices and edges; directed or undirected; simple or multigraph; weights and their signs; connectivity; path versus edge-traversal objective.

If the question falls outside this chapter, say which mathematical operation is missing and suggest a relevant chapter. The master skill for the book can route the task onward; this chapter skill also works on its own.

## Select and apply a rule

- **Are only $|V|$ and $|E|$ known?** Compute average degree and compare the edge count with $n-1$. These may settle the question before adjacency data is inspected.
- **Is a graph at the $n-1$ threshold?** Verify either connectedness or acyclicity. The count alone does not prove it is a tree.
- **Is the desired split binary?** Two-color each component. A conflict should be reported with its odd-cycle witness.
- **Is a planar drawing requested?** Apply the appropriate edge ceiling first. Failure proves nonplanarity; success merely permits further testing.
- **Is the task a one-to-one assignment?** Model a bipartite graph and look for a subset whose neighborhood is too small before attempting exhaustive assignments.
- **Must every edge be traversed once?** Count odd degrees and check connectivity among edge-bearing vertices. Do not confuse the task with visiting every vertex once.
- **Is a coloring required?** Decide whether a guaranteed $\Delta+1$ construction is sufficient or optimization is worth the additional effort.
- **Is the task shortest path?** Equal costs suggest BFS. Unequal nonnegative costs suggest Dijkstra. Any negative weight requires a different correctness argument.

Check the selected rule's conditions from the index below before applying its formula. Preserve the numbered citation and role. **Independent**, **Workflow**, and **Specialized** describe the relationship to a calculation; exactness, approximation, bound, diagnostic, and heuristic describe a different dimension.

Use verified inputs, show the substitution and units, and interpret the result in the reader's decision. Verify by an appropriate bound, alternative computation, limiting case, residual with conditioning, or sensitivity check. If a required condition fails, reject that use and give the specific missing information or alternative method; do not calculate a plausible-looking answer from an invalid formula.

**Essential boundary:** The planar edge bound is only a rejection test, and m=n-1 alone does not prove a tree. Separate Euler edge coverage from Hamiltonian vertex coverage.

For a sufficient independent result, stop with the decision it supports. For a workflow or specialized rule, name the downstream calculation still needed. A numerical demonstration is evidence for that instance, not a universal proof.

## Rule index

| Rule | Title | Role | Kind | Conditions |
|---|---|---|---|---|
| 10.1.1 | Use handshaking to convert edges into average degree | Independent | exact | finite undirected graph; loops counted twice in degree |
| 10.1.2 | Use n-minus-one as the connectedness edge floor | Independent | guaranteed bound | finite undirected graph; connected graph |
| 10.1.3 | Recognize a tree by the n-minus-one edge count plus one condition | Independent | exact under assumptions | finite undirected graph; any two of connected, acyclic, n minus 1 edges |
| 10.2.1 | Test bipartiteness by searching for an odd cycle | Independent | exact | undirected graph |
| 10.2.2 | Use the planar edge bound as a quick nonplanarity screen | Independent | guaranteed bound | simple planar graph; at least three vertices |
| 10.2.3 | Check Hall bottlenecks before seeking a perfect matching | Independent | exact under assumptions | finite bipartite graph; all subsets considered or equivalent certificate |
| 10.3.1 | Count odd-degree vertices before seeking an Euler trail | Independent | exact under assumptions | all nonisolated vertices connected; undirected graph |
| 10.3.2 | Use maximum degree plus one as a greedy coloring ceiling | Independent | guaranteed bound | finite simple graph; proper sequential coloring |
| 10.3.3 | Use breadth-first search for unweighted shortest paths | Workflow | exact under assumptions | unweighted or equal weight edges; finite reachable graph |
| 10.3.4 | Use Dijkstra only with nonnegative edge weights | Workflow | exact under assumptions | nonnegative edge weights; finite graph |

"Independent" rules finish a calculation on their own; "Workflow" rules prepare or check a step that another calculation completes.

## Apply it to your own inputs

1. State the question, the inputs with units, and the accuracy or decision threshold.
2. Pick the rule from the index and confirm each listed condition holds for these inputs. If one fails, say so and choose another route.
3. Substitute the inputs and show each step of the arithmetic.
4. Check the result with an independent calculation, a bound, a limiting case, or a sensitivity test.
5. To run it, open [10-graph-theory.ipynb](../../notebooks/10-graph-theory.ipynb), find the cell closest to the chosen rule, change the input values, and run the cell again.

## Worked checks from the notebook

- **Test a tree with connectivity and edge count** (rule 10.1.3). Why is the triangle-plus-isolate not a tree? It has n−1 edges but is disconnected and contains a cycle. The edge count alone is insufficient.
- **Close a cycle with two colors** (rule 10.2.1). Is a five-cycle bipartite? No. Its odd cycle forces adjacent vertices to receive the same color when alternating two colors.
- **Count odd degrees before planning an Euler trail** (rule 10.3.1). Can a triangle with an isolated vertex still have an edge-covering closed trail? Yes. The triangle is the connected edge-bearing component, with all degrees even. It is not a spanning traversal of the isolated vertex.
- **Break Dijkstra with one negative edge** (rule 10.3.4). Does any negative edge make Dijkstra wrong? Not always. At w=−0.5 the detour costs 2.5, longer than 2, so the answer is still right. The guarantee is gone, though, and at w=−2 it fails.
- **See the planar edge bound reject but never certify** (rule 10.2.2). K3,3 has 9 edges and the ceiling is 12. Is it planar? No. The screen passes but cannot certify planarity. The triangle-free ceiling 2n−4=8 is exceeded, so K3,3 is nonplanar.

## Teach and check understanding

Start with 10.1.1, 10.1.3, 10.3.4 when the reader wants a starting exercise. Ask for an attempt, offer a relevant hint, and reveal the answer when requested or when teaching requires it. Do not force a quiz when the reader asked for a worked solution.

Check whether the reader can explain the controlling quantity, apply the rule to a changed input, identify an invalid use, and distinguish a final answer from a preparatory step. Track only demonstrated work. Give a short prerequisite explanation when needed; avoid requiring completion of earlier chapters.

## Return a usable result

Include the chosen rule numbers, assumptions that matter, calculation, verification, and next action. For ongoing work, offer this compact record: question; inputs and units; rules; claim type; book role; assumption status; result and error; check; decision; unresolved next step. Write a progress file only when asked.

Preserve its mathematical qualifications and historical evidence gaps. Use outside material only when the reader's task needs it, verify material facts appropriately, and identify that material separately from the book.

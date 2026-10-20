# Graph search for motion planning

Graph search is how the course first solves the geometric motion planning problem: discretize the
[configuration space](configuration-space.md), turn it into a graph, and search the graph for a
path from start to goal. It is the subject of
[Lecture 2](02-discrete-motion-planning.md#planning-as-graph-search), which walks breadth-first
search, depth-first search and A\* through the same 5-by-5 grid. Slide numbers and timestamps on
this page refer to Lecture 2.

## From a planning problem to a graph

A **graph** is a set of vertices (or nodes) and edges, where an edge means the robot can go from
one vertex to the other in a single hop (slide 27, ≈36:45–37:30). A grid over the configuration
space becomes a graph in three steps (slide 28, ≈37:30–38:16):

![Slide 27 — Graph Search (definition of a graph)](../raw/images/02-discrete-motion-planning/slide-27.jpg)

*Slide 27 — a graph: vertices joined by edges, the edges defining which vertices are connected. [Deck](https://www.dropbox.com/scl/fi/pnwucnirlwgviqwaj67hl/Lecture2.pdf?rlkey=6s2et2apw9rtnvr8x2ke243sp&dl=0)*

1. put one vertex at the **centre** of each grid cell;
2. connect vertices with edges by **4-connectivity** (north, south, east, west) or
   **8-connectivity** (diagonals too);
3. delete every vertex whose cell intersects an obstacle, with its edges.

The grid itself embodies choices, none of them fundamental (slide 26, ≈35:12–36:45). A uniform
grid could instead be adaptive, finer around obstacles and narrow passages. The connectivity is a
choice. So is the resolution: a finer grid approximates the space better and can find paths
through narrow passages, but makes planning more expensive.

## One template, four algorithms

Every graph search algorithm in the course has the same skeleton, **forward search** (slide 35,
≈40:35–41:21). It keeps a queue $Q$ of vertices still to be explored. It repeatedly takes one out
with Q.GetVertex(), stops with success if that vertex is in the goal set, and otherwise adds the
vertex's unvisited neighbours to $Q$, recording the vertex as each neighbour's parent. The
algorithms differ **only in how Q.GetVertex() chooses** (≈42:51–43:38):

| Algorithm | Q.GetVertex() takes out | What Lecture 2 says about it |
| --- | --- | --- |
| Breadth-first search (BFS) | the vertex added first (first in, first out) | searches all paths of length $k$ before any of length $k + 1$, so it finds a path with the fewest edges (slide 49, ≈52:07) |
| Depth-first search (DFS) | the vertex added last (last in, first out, a stack) | follows one path deeply until a dead end or the goal; can do well when the path is long and there are few ways to the goal (slide 60) |
| Dijkstra's algorithm | the vertex with the smallest $F$, with $H = 0$ | the special case of A\* with a zero heuristic (slide 65) |
| A\* | the vertex with the smallest $F = C + H$ | returns optimal paths if $H$ never overestimates the cost-to-go (slide 64, ≈56:46) |

The walk-throughs are on the [lecture page](02-discrete-motion-planning.md), all on the same
5-by-5 grid. After four iterations, BFS has visited seven vertices spread evenly around the start
(slide 46).

![Slide 46 — Example (BFS, iteration 4)](../raw/images/02-discrete-motion-planning/slide-46.jpg)

*Slide 46 — BFS after iteration 4: seven visited vertices spreading out around A; the queue holds (1,2), (2,1), (1,5). [Deck](https://www.dropbox.com/scl/fi/pnwucnirlwgviqwaj67hl/Lecture2.pdf?rlkey=6s2et2apw9rtnvr8x2ke243sp&dl=0)*

DFS instead runs in a single line up the left side and across the top, and reaches the goal in
eight iterations (slide 59).

![Slide 59 — Depth-First Search (DFS): iteration 8, done](../raw/images/02-discrete-motion-planning/slide-59.jpg)

*Slide 59 — DFS finished: the expanded vertices form one line from A up the left column and along the top row to B, and the right side of the grid is never visited. [Deck](https://www.dropbox.com/scl/fi/pnwucnirlwgviqwaj67hl/Lecture2.pdf?rlkey=6s2et2apw9rtnvr8x2ke243sp&dl=0)*

A\* scores every vertex it meets with $F$ and always expands the alive vertex with the smallest
value, here after three iterations (slide 74).

![Slide 74 — A* step: neighbours of (1,4)](../raw/images/02-discrete-motion-planning/slide-74.png)

*Slide 74 — A\* expanding (1,4), the ringed vertex: dead vertices red, alive ones yellow with their F values. [Deck](https://www.dropbox.com/scl/fi/pnwucnirlwgviqwaj67hl/Lecture2.pdf?rlkey=6s2et2apw9rtnvr8x2ke243sp&dl=0)*

**Recovering the path.** The search marks vertices but does not by itself return a path. Keep
each vertex's parent, the vertex it was reached from, then follow parents back from the goal to
the start and reverse the result (slide 48, ≈47:28–48:14).

## Cost and optimality

To talk about the best path, attach a cost (or "loss") $l(e)$ to each edge $e$. A plan's total
cost is the sum of its edge costs, and the goal is to minimize it (slide 63, ≈53:41–54:28). Costs
must be non-negative. With a single negative edge, a path could go back and forth across it
forever and drive its cost to negative infinity, which Majumdar likens to reward hacking
(≈54:28–55:15).

BFS is optimal only when the cost is path length, the number of hops. For any other cost, such as
energy for a drone flying in a wind that favours some directions, it may not be (≈52:55). BFS
also explores slowly, expanding uniformly in every direction even when we know where the goal is
(slide 62, ≈53:41). A\* addresses both.

## Heuristics and A\*

A\* takes out the vertex with the smallest

$$F(x) \triangleq C(x) + H(x)$$

where $C(x)$ is the estimated cost-to-come from the start A to $x$ and $H(x)$ is the estimated
cost-to-go from $x$ to the goal B (slide 64, ≈55:15–56:46).

**The heuristic must be an underestimate**: $H(x)$ must be a lower bound on the optimal cost-to-go.
The version of A\* in the course is only guaranteed to give optimal paths when this holds.
Majumdar states it as a claim and suggests building counterexamples as an exercise (slide 64,
≈56:46–59:52).

**Good underestimates are cheap because they ignore obstacles.** The slide's example is the
Euclidean distance to B for distance-optimal planning. On a 4-connected grid with unit edge costs,
the worked example uses the Manhattan (L1) distance, the number of steps north or south plus the
number east or west (slide 68, ≈57:34–58:19). Real paths must go around obstacles, so they are at
least this long. Taking obstacles into account in $H$ would be "almost as hard as solving the
planning problem to begin with" (≈1:05:14). Choosing $H = 0$ everywhere is always valid and gives
Dijkstra's algorithm, versions of which, with fancier heuristics, power route-finding such as
Google Maps (slides 65 and 66, ≈59:06–59:52).

**Heuristics can be fooled.** An adversarial environment, such as a wall placed so that heading
for the goal is exactly wrong, makes a goal-directed heuristic waste effort. Worst-case complexity
differs from average-case complexity, and most robotics problems are not adversarial
(≈1:10:39–1:11:27). State-of-the-art planners use **learned heuristics** instead of hand-designed
ones. Lecture 2's example is from Tesla's AI Day, 2021, where a search guided by Euclidean
distance used 400,000 nodes and one guided by a navigation route used 22,000 (slide 77,
≈1:11:27–1:13:45).

## A\* bookkeeping

- **Three kinds of vertex** (slide 69). **Unvisited** vertices have not been encountered.
  **Alive** vertices are in $Q$, encountered but not yet taken out. **Dead** vertices have been
  taken out of $Q$.
- **Ties** in $F$ need a rule. Lecture 2 uses the smaller $H$, and mentions first in, first out
  and last in, first out as alternatives (≈1:05:14–1:06:47). In its first tie both vertices had
  $H = 6$, so the rule did not decide it (slide 73).
- **Cost-to-come is incremental.** When $x'$ is reached from $x$, its cost-to-come is $C(x)$ plus
  the cost of the edge from $x$ to $x'$ (≈1:07:34–1:08:19).
- **Finding the smallest $F$** can be a linear scan of the queue, which is all the course assumes
  (≈1:08:19–1:09:05).
- **The full algorithm** keeps a dead set and a tentative cost-to-come for each neighbour. It
  updates a neighbour's parent, $C$ and $F$ whenever it finds a cheaper path to it (slide 79,
  reproduced on the [lecture page](02-discrete-motion-planning.md#the-full-a-algorithm)).

## Where it appears

- [Lecture 2 — Discrete Motion Planning](02-discrete-motion-planning.md): discretization, the
  forward search template, BFS, DFS, Dijkstra's algorithm and A\*, each worked on a 5-by-5 grid.
  Implementing A\* is part of Assignment 1 (see [`sources.md`](../sources.md)).

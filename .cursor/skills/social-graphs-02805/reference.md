# 02805 reference

Fetch live pages when they disagree with this file. Week 1 is live as of 2 Sep 2026.

## Calendar (Fall 2026)

Wednesdays 09:00, building 303A (Aud 43, Aud 44, Classroom 46).

| Date | What |
| --- | --- |
| 2 Sep | Week 1 · Networks |
| 9 Sep | Week 2 · Models & null models |
| 16 Sep | Week 3 · Who matters, and why |
| 23 Sep | Week 4 · Communities & backbones |
| 30 Sep | Test 1 (first hour, weeks 1–4, 25%) then Week 5 · NLP I |
| 7 Oct | Week 6 · NLP II |
| 14 Oct | Autumn break — no teaching |
| 21 Oct | Week 7 · NLP III |
| 28 Oct | Week 8 · Networks × language |
| 4 Nov | Test 2 (first hour, weeks 5–8, 25%) then project kickoff |
| 11–25 Nov | Project period |
| 2 Dec | Demo fair (project 50%) |

Groups of 3 (smaller OK, larger not). Iron rule: everyone must be able to solve everything.

## Formulas (week 1)

Undirected simple network, `n` nodes, `m` edges:

- Handshaking: `∑ k_i = 2m`
- Average degree: `⟨k⟩ = 2m / n`
- Possible pairs: `n(n-1)/2`
- Density: `2m / [n(n-1)]`

Directed:

- Mean in-degree = mean out-degree = `m / n`
- Reciprocal pairs collapse when going undirected, so directed edge count ≥ undirected pair count

Path = sequence of edges; distance = shortest-path length; connected component = mutually reachable set (directed: see Atlas; week 1 uses the undirected giant component informally). Many real networks have one giant component plus islands.

## Marvel week-1 snapshot

Source: Wikipedia Category:Marvel Comics superheroes, snapshot 26 Aug 2026. Edges from **running article text**, not navboxes. Redirects resolved.

| Quantity | Value |
| --- | --- |
| `n` | 303 |
| Directed edges | 1,784 |
| Mean in = mean out | `1784/303 ≈ 5.9` |
| Undirected pairs `m` | 1,434 (350 reciprocal) |
| Undirected `⟨k⟩` | `2·1434/303 ≈ 9.5` |
| Possible pairs | `303·302/2 = 45,753` |
| Density | `1434/45753 ≈ 0.031` (~3%) |
| Isolates | 17 |
| Giant component | 277 (91%) |
| Other island | 9 nodes |
| Top in-degree | Spider-Man, `k = 106` |
| Top out-degree | Betsy Braddock, `k = 28` |

In-degree can keep growing (other pages confer fame). Out-degree has a writing ceiling. Do not mix them into one undirected distribution if you care about mechanism.

Files: `week1_nodes.tsv`, `week1_edges.tsv` on the [data page](https://sunelehmann.com/socialgraphs2026-web/data). TSV, `#` comments, node ids = Wikipedia titles with underscores. Blurbs may contain quotes → `quoting=3`.

```python
import pandas as pd
import networkx as nx

nodes = pd.read_csv(
    "week1_nodes.tsv", sep="\t", comment="#", quoting=3
)
edges = pd.read_csv(
    "week1_edges.tsv", sep="\t", comment="#", names=["source", "target"]
)

G = nx.DiGraph()
G.add_nodes_from(nodes.node_id)
G.add_edges_from(edges.itertuples(index=False))
# expect 303 nodes, 1784 edges
```

Node file has names, Wikidata ids, URLs, blurbs — **no** precomputed degrees.

## Week-1 binning (Goodies)

Working in `u = k+1` (log axis cannot show 0):

- Width-1 bins for `u = 1, …, 7`
- Then doubling: `[8, 16)`, `[16, 32)`, `[32, 64)`, `[64, 128)`
- Divide each bin’s count by **bin width** (density, not raw count)
- Plot doubling bins at the geometric mean of integers covered (`[8,16)` → `√(8·15) ≈ 10.95`)
- Width-1 bins must coincide with raw `P(k)`
- Careless binning: forget to divide by width; bin where data is dense; arithmetic midpoint on a log axis; `np.logspace` edges that skip integers or double-count; last degree sitting on a half-open edge

Binning is not for fitting power-law slopes. Cumulative distribution arrives in week 2.

## Week 1 exercises (modes)

| ID | Mode | Notes |
| --- | --- | --- |
| 1.1 | Learn | Nodes/edges; personal network; two representations of one system |
| 1.2 | Tool | 10 factual LLM questions; score vs trusted source; AI_METHODS paragraph |
| 1.3 | Builder | Karate Club; hand-verify a degree; rebuild adjacency-matrix explorable |
| 1.4 | Learn | Marvel in vs out; binning; why undirected is least useful |
| 1.5 | Learn | Paper: edge list A–F; degrees, density, matrix, triangles, cut vertex, directed rewrite, distances |
| 1.6 | Builder | Load Marvel correctly; plots vs `k+1`; official binning; exponential vs power-law specimens |
| 1.7 | Learn | Layout = decoration vs data |
| 1.8 | Builder | Group GitHub Pages + go-nuts post on frozen Marvel data — work in `02806-social-graph-project/` (own GitHub remote, already connected) |

## On the test (week 1)

Closed book, student should be able to:

- Translate a system into nodes and edges and defend (or change) the choice
- Classify directed/undirected, weighted/unweighted; spot a representation wrong for the question
- On ≤6 nodes: degrees, in/out, `m`, `⟨k⟩`, density; degrees sum to `2m`
- Directed vs undirected counts; why mean in = mean out; isolates dropped by edge-list-only loads
- Write/read an adjacency matrix; undirected ⇒ symmetric; degrees in rows/columns
- Read degree distributions: linear vs log–log; heavy tails; in-tail vs short out-tail as mechanism
- What binning does; where binned = raw; why `k+1`; two ways binning invents/destroys a power law
- Path, distance, connected component on a small example
- Drawing: data vs layout; one conclusion the picture invites that the data does not support
- Node property vs edge property vs network property

## Links worth knowing

- Course: https://sunelehmann.com/socialgraphs2026-web/
- New way: https://sunelehmann.com/socialgraphs2026-web/the-new-way.html
- Week 1: https://sunelehmann.com/socialgraphs2026-web/weeks/week1
- Data: https://sunelehmann.com/socialgraphs2026-web/data
- Site source: https://github.com/suneman/socialgraphs2026-web (`docs/` is what GitHub Pages serves)

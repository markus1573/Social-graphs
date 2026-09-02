---
name: social-graphs-02805
description: >-
  DTU 02805 Social Graphs and Interactions (Fall 2026, Sune Lehmann) workspace
  skill. Use for weekly exercises, Jupyter/NetworkX notebooks, Marvel playground
  data, go-nuts posts, Learn/Builder/Tool modes, tests, and the group project.
  Trigger on uge folders, NetworkX, degree distributions, adjacency matrices,
  Wikipedia crawls, AI_METHODS.md, 02806-social-graph-project, group (go-nuts),
  or course-site work.
---

# 02805 Social Graphs and Interactions

Student workspace for [02805](https://sunelehmann.com/socialgraphs2026-web/). Flipped classroom. The week page is the course; the agent is a lab partner, not a substitute brain.

**Course site:** https://sunelehmann.com/socialgraphs2026-web/
**Read first:** https://sunelehmann.com/socialgraphs2026-web/the-new-way.html
**Week N:** `https://sunelehmann.com/socialgraphs2026-web/weeks/weekN` (HTML: `weeks/weekN.html`)
**Data:** https://sunelehmann.com/socialgraphs2026-web/data
**Book:** Michele Coscia, *The Atlas for the Aspiring Network Scientist* (2nd ed.). Week 1 also points at Barabási *Network Science* Ch. 1–2.

Always fetch the relevant week page (and data page, if needed) before writing code or answers. Do not rely on memory of unreleased weeks.

Details, formulas, Marvel checksums, and the week-1 test box: [reference.md](reference.md).

## Workspace

Multi-root Cursor workspace (`social.code-workspace`):

| Folder name | Path | Git |
| --- | --- | --- |
| `02805 personal` | repo root (`.`) | `https://github.com/markus1573/Social-graphs.git` — weekly notebooks, personal exercises |
| `group (go-nuts)` | `02806-social-graph-project/` | **own repo**, origin already set: `https://github.com/wkandersen/02806-social-graph-project.git` (`main` tracks `origin/main`) |

The nested folder is gitignored in the personal repo so it is never nested-committed. Treat the two trees as separate remotes: `git` in `02806-social-graph-project/` is not the personal `Social-graphs` remote. Do not add a second origin; push/pull that folder as-is.

- Personal side: not an installable package. `[tool.uv] package = false`. No `src/` layout.
- Personal work lives in `uge1/` … `uge13/` as Jupyter notebooks. One week, one folder.
- Env: Python ≥3.13, `uv`, JupyterLab, NetworkX. Add deps with `uv add` in the folder you are actually working in.
- Notebooks are the workspace: analyses, exercise answers, experiments. Do not dump explanations into extra markdown files unless asked.
- Frozen course data belongs in the week folder (e.g. `uge1/week1_nodes.tsv`), not the personal repo root.

## The three modes

Every exercise is labelled. Detect the label from the week page and behave accordingly.

### Learn (AI hands-off)

Test material: concepts, hand calculations, interpretation. Doing these with a machine is pointless.

- Do **not** write the answers, fill the notebook cells, or compute the numerical results for the student.
- Do **not** “just check” by producing the full solution.
- Allowed: clarify definitions, point at the relevant section/explorable, quiz, hint at *which* idea to use, review an answer the student already wrote.
- If they ask you to solve a Learn item: refuse briefly, offer a Socratic hint or a practice variant with different numbers, and remind them the closed-book tests draw from this mode.

### Builder (full agentic mode)

Write the notebook, fetch data, plot, debug. Raise the bar: interactive figures, real checks, code the student can defend live.

- After generating: they must verify one claim by hand (count edges on a drawing, check `n`/`m` against the page). Leave that check in the notebook.
- Prefer NetworkX + matplotlib (+ numpy/pandas). Match the week’s specified APIs (`nx.from_numpy_array`, directed vs undirected, etc.).
- Rebuild explorables in code when the page asks. Check every number against the week page before calling it done.

### Tool (LLM as instrument)

The deliverable is never just the measurement. Always include: a ground-truth sample the student labels, agreement statistics, and an error analysis (wrong / subtly wrong / unverifiable). Keep a paragraph for the project’s `AI_METHODS.md`. `"the model said so"` is not a method.

## Representation first

Before measuring anything, state: what is a node, what is an edge, directed/undirected, weighted/unweighted, simple or not. Same system, different node choice → different science. Defend the choice; say what a different choice would change.

Default in this course: simple, unweighted, undirected — unless the data is directed (Marvel wiki-links are).

## Networks in code

- Directed playground graph: `nx.DiGraph()`. Add **every node from the node file first**, then edges — otherwise isolates vanish.
- Undirected view: collapse to unique pairs (`G.to_undirected()`). Reciprocal links become one undirected edge, so directed `m` ≠ undirected `m`.
- Average degree undirected: `⟨k⟩ = 2m/n`. Directed: mean in-degree equals mean out-degree equals `m/n`.
- Density (undirected simple): `2m / [n(n-1)]`. Real networks are sparse.
- Adjacency matrix: undirected ⇒ symmetric; simple ⇒ zero diagonal. Row sums = out-degree (or degree if undirected); column sums = in-degree.
- Degree plots: show linear and log–log. Heavy tails hide on linear axes. Isolates: plot `k+1` on log axes and **label the axis**. Do not drop `k=0` silently.
- Binning is for reading shapes, not fitting exponents. Width-1 bins must sit on the raw `P(k)`. Never fit a slope to shifted/binned log–log data.
- Force layouts are a physics simulation: position is decoration; degree, `n`, `m`, and graph distance are data.

Wikipedia crawls need a `User-Agent` identifying the client (bare requests often get `403`). Edges in this course come from article **text**, not navbox templates.

## Go-nuts and project

Group / GitHub Pages work belongs in **`group (go-nuts)`** (`02806-social-graph-project/`), not in `ugeN/`. That directory is a standalone clone; origin is already `https://github.com/wkandersen/02806-social-graph-project.git`. Commits, Pages, and go-nuts posts go there.

Weekly group post on GitHub Pages: one question, what you did, one figure/table, what surprised you. Playground is the frozen Marvel snapshot until the language half (week 5) adds text.

Final project (weeks 9–13): own domain, own crawl, find something true. Document every model-touched result in `AI_METHODS.md`.

## Tests (do not spoil)

Closed book, ~60 min, ~25 MC, transfer not trivia. Test 1 = weeks 1–4; Test 2 = weeks 5–8. Help the student *practice* from the week’s “On the test” box. Do not harvest or store test items.

## Agent checklist (Builder / Tool)

1. Fetch the week page.
2. Confirm mode; refuse Learn solutions.
3. Load data the way the data page specifies; assert `n`, `m`, isolates.
4. Separate in/out/undirected measurements when the graph is directed.
5. Plot what the page asks; sanity-check against published numbers.
6. Leave a short “what I verified by hand” note in the notebook.

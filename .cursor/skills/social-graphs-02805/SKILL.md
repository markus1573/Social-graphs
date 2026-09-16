---
name: social-graphs-02805
description: >-
  DTU 02805 Social Graphs and Interactions (Fall 2026, Sune Lehmann) workspace
  skill. Use for weekly exercises, Jupyter/NetworkX notebooks, Marvel playground
  data, go-nuts posts, Learn/Builder/Tool modes, tests, and the group project.
  Trigger on uge folders, Essentials, traditional exercises, NetworkX, degree
  distributions, adjacency matrices, Wikipedia crawls, AI_METHODS.md,
  02806-social-graph-project, group (go-nuts), course-site work, finish for the
  day, wrap up, Learn catch-up, or test review.
---

# 02805 Social Graphs and Interactions

Student workspace for [02805](https://sunelehmann.com/socialgraphs2026-web/). Flipped classroom. The week page is the course; the agent is a lab partner, not a substitute brain.

**Course site:** https://sunelehmann.com/socialgraphs2026-web/
**Read first:** https://sunelehmann.com/socialgraphs2026-web/the-new-way.html
**Week N:** `https://sunelehmann.com/socialgraphs2026-web/weeks/weekN` (HTML: `weeks/weekN.html`)
**Data:** https://sunelehmann.com/socialgraphs2026-web/data
**Book:** Michele Coscia, *The Atlas for the Aspiring Network Scientist* (2nd ed.). Local copy at the personal-repo root: `sna_book.pdf` (also https://www.networkatlas.eu/). Week 1 also points at Barabási *Network Science* Ch. 1–2 (`http://networksciencebook.com/`). When summarizing or citing Atlas chapters, read from `sna_book.pdf` rather than guessing.

Always fetch the relevant week page (and data page, if needed) before writing code or answers. Do not rely on memory of unreleased weeks.

Details, formulas, Marvel checksums, and test boxes: [reference.md](reference.md). Default weekly work is the **Essentials** flow below.

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
- **Math in notebook markdown: `$…$` inline, `$$…$$` display. Never `\(…\)` or `\[…\]`** — Jupyter’s MathJax ignores those and renders the raw backslashes. (Chat replies are the opposite: Cursor wants `\(…\)` / `\[…\]`. Do not copy chat math into a cell unconverted.)
- Writing a notebook as raw JSON: every LaTeX backslash must be doubled (`$\\alpha$`), or the file will not parse. Safer: build/edit cells with the notebook edit tool, or a small `json` script, rather than hand-writing `.ipynb` text.
- Frozen course data belongs in the week folder (e.g. `uge1/week1_nodes.tsv`), not the personal repo root.

## Default weekly flow: Essentials

The student studies from the week page’s **Essentials** box (and **On the test**), not by grinding every labelled item on the page. Traditional exercises: the agent poses questions; the student solves; help is allowed.

When starting a week, or when they ask for Essentials / traditional practice:

1. Fetch the week page. Treat **Essentials** + **On the test** as the syllabus. Atlas chapters named on the page are backup, not extra homework.
2. Write an original practice set into that week’s notebook (`ugeN/exN.ipynb`) as **markdown**. Numbered problems, small drawn graphs, short calculations, one-sentence “why” items. Hit every Essential; match the closed-book skills in **On the test**.
3. Do **not** paste the course’s Learn/Builder/Tool wording. Write variants (different graphs, different numbers, same ideas). Goodies and stretch explorables stay off this set unless they ask.
4. Leave empty cells under each problem for their work. In chat, work one problem (or a tight cluster) at a time; the notebook is the problem sheet.
5. **Help is allowed** on Essentials items: definitions, which idea to use, hints, checking their reasoning, a nudge if they stall. Do not dump a full worked solution on first ask. After a real attempt, you may finish the algebra with them. If they want only a check, say what is right and where it broke.
6. Keep it exam-shaped: pen-and-paper first. NetworkX is for checking *after* they have written the rings / sums / fractions, not instead of that.
7. Official page exercises (1.3, 3.5, go-nuts, …) still exist. Run them only if they ask to do the course items. Then use the three modes below. Live Learn hands-off does **not** apply to Essentials-flow practice.

## The three modes (official week-page exercises)

Every official exercise is labelled. Detect the label from the week page and behave accordingly.

### Learn (live = hands-off; end of day = catch-up)

Test material: concepts, hand calculations, interpretation. Tests are closed-book; the student still needs a readable trail of the items they skipped.

**While studying (default):** do **not** write answers, fill cells, or compute the numerical results. Do **not** “just check” by producing the full solution. Allowed: definitions, the relevant Atlas/week section, quizzes, which idea to use, review of an answer they already wrote. If they ask to solve a Learn item mid-session: refuse briefly, hint or give a practice variant with different numbers.

**End of day / catch-up:** when they say they are done for today, wrapping up, out of time, or want remaining Learn filled for test prep — complete **every unfinished Learn exercise** for the week(s) they were on (fetch the week page; scan the notebook for empty/partial Learn cells). Goal: something they can read before the test, not a dump of numbers.

Write catch-up into the week notebook (`ugeN/`), marked as catch-up so they know they did not do it live. For each Learn item:

- Restate what is being asked in one line.
- Work the solution with the same reasoning they would need closed-book (definitions → method → numbers → what would change if the representation changed).
- Tie it to that week’s “On the test” box (transfer, not trivia). Do not harvest or store actual test items.
- Prefer markdown + small worked examples over unexplained code. If a figure or NetworkX check helps them *see* the idea, include it and say what to remember without the notebook.
- If they already answered part of an item, keep their work and only fill the gaps.

Do not skip Learn items because they are “meant to be done by hand.” Catch-up exists because they will not have time to finish everything before the tests.

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

### Site layout: one folder, one identity per week

`docs/` is what Pages serves. Structure is fixed:

- `docs/index.html` + `docs/home.css` — front page indexing every week. Add a card when a week ships.
- `docs/weekN/` — that week's `index.html`, `styles.css`, `app.js`, and `data/`. Self-contained, permanently live, never overwritten.
- `analyse_weekN.py` at the repo root generates only its own week's JSON into `docs/weekN/data/`.
- Each week page links back to `../` (wordmark + a nav item, so it survives the mobile breakpoint).

**Hard rule: every week gets a brand-new layout.** Do not copy, adapt, or "evolve" a previous week's page. Start the CSS from an empty file. Concretely, week N must differ from every earlier week in *all* of:

- **typeface pairing** — new display + mono fonts, not last week's;
- **palette** — new background/accent system, not a recolor of the old variables;
- **layout paradigm** — if a previous week was full-bleed scroll sections, use a sidebar rail, dashboard grid, horizontal deck, split-screen, canvas, or something else entirely;
- **navigation and component vocabulary** — new class names, new section chrome, new card/panel shapes.

Reusing week 1's `--ink`/`--paper`/`--lime` variables, its `.section`/`.section-intro`/`.eyebrow` scaffolding, or its giant-`clamp()`-headline rhythm counts as copying. The interactivity bar still only goes up: each week should be more playable than the last. The science stays honest regardless of the skin — representation stated, numbers asserted against the week page, one human check left in.

Final project (weeks 9–13): own domain, own crawl, find something true. Document every model-touched result in `AI_METHODS.md`.

## Tests (do not spoil)

Closed book, ~60 min, ~25 MC, transfer not trivia. Test 1 = weeks 1–4; Test 2 = weeks 5–8. Help the student *practice* from the week’s “On the test” box. Do not harvest or store test items.

## Agent checklist

1. Fetch the week page. Default path: **Essentials** practice in `ugeN/exN.ipynb`, not the full exercise list.
2. If they are on Essentials: questions in markdown (`$…$` math, never `\(…\)`), help allowed, no full dump on first ask, pen-and-paper before NetworkX.
3. If they asked for official items: confirm mode. Live Learn: no solutions. End-of-day / catch-up: finish all remaining Learn items as study notes in the notebook.
4. Load data the way the data page specifies; assert `n`, `m`, isolates.
5. Separate in/out/undirected measurements when the graph is directed.
6. Plot what the page asks; sanity-check against published numbers.
7. Leave a short “what I verified by hand” note on Builder work; on Learn catch-up, leave a catch-up heading plus closed-book takeaways.

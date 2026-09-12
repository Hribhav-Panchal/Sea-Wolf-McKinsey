# Sea Wolf Solver

A fast, client-side solver for the **McKinsey Solve — Sea Wolf** game. Enter a
site's microbe prospect pool and target requirements, and it exhaustively
checks every possible treatment and ranks them by effectiveness.

Everything runs in the browser — no build step, no server. Open `index.html`.

## The game, in one line

For each site: pick exactly **3 microbes** whose **attribute averages** (Size,
Energy, Mobility — each 1–10) all land inside the site's **target ranges**,
include **at least one** microbe with the **desired trait**, and include **none**
with the **undesired trait**.

## How the solver scores

Each candidate treatment starts at 100% effectiveness and loses **20% per missed
condition**:

- each attribute whose average falls outside its target range,
- a missing desired trait,
- any undesired trait present.

Because the prospect pool is small (10 microbes, choose 3 = 120 combinations),
the solver brute-forces **every** combination and sorts them best-first, so the
top result is always the mathematically optimal treatment available. Ties are
broken toward combinations that sit most comfortably inside their ranges (most
robust).

## Features

- **Configurable attributes** — rename, add, or remove attribute columns for any
  site variant.
- **Adjustable pick count** — defaults to 3.
- **Live ranking** — results re-rank as you type.
- **Per-attribute range indicators** — see each average against its target band.
- **Works with partial data** — when no 100% solution exists, it shows the
  closest treatments.
- Loads with example data; **Clear** to enter your own. Inputs persist locally.

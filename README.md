# coragora-corpus

The open, grounded **Erdős open-problem corpus** that powers the Coragora
[Problem Atlas](https://coragora.com) — a research graph where an *open problem*
is a first-class object `P = ⟨U, Σ, A⟩`.

This repository is the **data surface**, published in the open. The engine that
computes over it (lifecycle, edge algebra, keystone/reduction/frontier
analytics, grand-problem proposal) lives elsewhere and is not part of this repo.

## What's here

```
erdos/
├── problems.json     # the open problems (and closed ones, with their closure)
├── mechanisms.json   # proof mechanisms / techniques
├── edges.json        # typed relations between problems and mechanisms
└── events.json       # lifecycle events (pose / refine / close / reopen)
```

23 problems, 8 mechanisms, 27 edges — grounded in the published record. Every
`status` reflects the real state of the mathematics (e.g. the cap-set problem is
`closed`, Ellenberg–Gijswijt 2016; the sunflower conjecture is `open`). Edge
provenance is honest: each edge is marked `documented` (a relationship attested
in the literature) or `editorial` (an organizing link we drew).

## The object model

Each **problem** is `P = ⟨U, Σ, A⟩`:

- **`unknowns` (U)** — what is genuinely unresolved (a `proof`, a `value`, a
  `design`, …). A problem with no unknown is not a problem — it's a claim.
- **`success_modes` (Σ)** — how the problem could be settled. Each mode carries
  `criteria` with a `class` (`FORMAL`, `JUDGED`, …); a `JUDGED` criterion must
  name a rubric. Modes may be positive (`m-pos`, a proof) or negative (`m-neg`,
  a counterexample/refutation) — impossibility is first-class.
- **`assumptions` (A)** — the standing hypotheses under which the problem is posed.

A closed problem records its `closure`: `kind` (`resolved` | `dissolved`),
the `mode` it closed in, and the `artifact` (the paper/result that settled it).

**Mechanisms** are proof techniques (`signature` = the shape of problem they
apply to). **Edges** are typed:

- `GENERALIZES` — one problem subsumes another (the keystone/specialization structure).
- `REDUCES_TO` — solving the target would settle the source (mutual reductions ⇒ equivalence).
- `INVOLVES` — a problem is attacked by a mechanism (the clustering structure).
- `DECOMPOSES_INTO` — a problem breaks into sub-problems.

**Events** are the lifecycle log — e.g. `events.json` records the May-2026
disproof of the unit-distance conjecture (Erdős #90) as a `CLOSE` in the
negative mode.

## Using it

The files are the source of truth — a corpus is just a directory of these four
JSON files. Load them with any JSON reader; the schema above is the whole
contract. Contributions that keep the data grounded and the provenance honest
are welcome.

## License

The data in this repository is licensed under
**[Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/)**.
You may share and adapt it, including commercially, with attribution to
*Coragora*. See [`LICENSE`](./LICENSE).

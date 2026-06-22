# Bayland Health BI Take-Home — TikTok Shop Affiliate Creator Performance

Welcome, and thanks for taking the time on this exercise. This repository contains
everything you need to get started. Read this page first, then dive into the assignment.

---

## Start here

1. **Read the assignment:** [`bia_takehome_affiliate_performance.md`](bia_takehome_affiliate_performance.md)
   — the background, the business question, the six parts of the work, and exactly what to
   submit. **Read it in full before you begin.**
2. **Read the data dictionary:** [`data_dictionary.md`](data_dictionary.md) — a
   plain-language description of every column in the four data files, plus how the tables
   join together. Read it before you touch the data.
3. **Find the data:** the four files live in [`data/`](data/). They are exported
   from real systems, so expect them to be **raw** — cleaning them is part of the exercise.

---

## What's in this repo

| Path | What it is |
|---|---|
| `bia_takehome_affiliate_performance.md` | The assignment: background, business question, Parts 1–6, and the deliverables. |
| `data_dictionary.md` | Plain-language description of every column in the four data files, with the join diagram. |
| `data/creators.csv` | One row per creator: id, handle, follower count, niche, region, commission rate, join date, status. |
| `data/videos.csv` | One row per video: which creator posted it, post date, views, likes, comments. |
| `data/orders.csv` | One row per order line: which video/creator drove the order, product, quantity, gross sales, status, commission. |
| `data/products.csv` | One row per SKU: product name and category. |

---

## A few reminders

- **Document your decisions as you go.** We care more about your judgment and reasoning than
  about a polished final number.
- **The files relate to each other.** A creator has many videos; a video can drive many
  orders. Be careful how you join and aggregate so you don't count the same thing twice.
- **State your assumptions and proceed.** If something is unclear, note the assumption and
  keep going — that's part of the job.

See the assignment for the full list of deliverables, the time expectation (~2–4 hours), and
the AI-tool usage policy.

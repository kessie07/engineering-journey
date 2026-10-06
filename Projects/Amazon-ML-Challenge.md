# Amazon ML Challenge

**Status:** Worked on (partial, stopped at candidate generation)
**When:** September 2026
**Code:** Colab notebook, not published

## The problem

The task was entity matching. There's one source of records (S1, about 2.2M rows) and two other sources (S2 about 5.0M, S3 about 5.3M). For each S1 record you have to find the records in S2/S3 that refer to the same real-world entity. The ground truth gives the matched IDs for training.

You can't compare every S1 record with every S2/S3 record, so the first real problem is **blocking**: cheaply narrowing things down to a candidate set that still contains the true matches.

## What I did

Working in Colab with DuckDB querying the parquet files directly, because the data didn't fit comfortably in pandas memory:

1. Loaded the cleaned columns (name, address, country, a composite key) and checked shapes and memory.
2. Tried three blocking rules (same name, same address, same composite key) and measured **recall**: what fraction of true matches end up in the candidate set.
3. Name blocking blew up (tens of millions of candidate pairs), so I tried **capping** name buckets by frequency and measured how recall and candidate count traded off at different caps.
4. Started an embedding-based approach: multilingual MiniLM sentence embeddings for S2+S3, stored on disk, to search with FAISS. The Colab session had no GPU, which is where this stalled.

## What I learned

The rule-based blocks combined only recovered about **47% of true matches**:

| Block | Recall |
| :--- | :--- |
| Name | ~41% |
| Address | ~8% |
| Composite | ~2.6% |
| Union of all three | ~46.8% |

So exact-match blocking was never going to be enough, which is why I moved to embeddings. I don't have a final submission score recorded, so I'm not claiming one.

## What's next

Write up the blocking experiments properly. If I revisit it, try fuzzy or embedding-based candidates on a sample first, before committing to the full 15 GB embedding file.

## Evidence

- Notebook outputs with the shapes, candidate counts and recall numbers above (exported cell outputs from the Colab notebook).
- No charts saved yet.

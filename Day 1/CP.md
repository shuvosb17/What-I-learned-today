
# 📌 Note: Multiset Partition & MEX (for “MEX Partition” problems)

## 1) Multiset

A **multiset** is like a set, but it **allows duplicates**.

Example:
( A = {1,2,3,3} )
Here, `3` appears twice.

---

## 2) Partition of a Multiset

A **partition** of a multiset (B) is a collection of multisets
( s_1, s_2, \dots, s_k ) such that:

* Every element of (B) is distributed into the parts.
* **Counts are preserved**.

Meaning:

> For every value (x),
> (how many times (x) appears in (B))
> = (total times (x) appears across all parts).

✅ Valid partitions of ({1,2,3,3}):

* ({1,3} + {2,3})
* ({1,2,3,3}) (one part is allowed)
* ({2} + {1,3} + {3})

❌ Not a partition:

* ({1,2} + {3})
  because one `3` is missing.

---

## 3) MEX (Minimum Excluded Value)

The **mex** of a multiset is:

> The **smallest non-negative integer** (0,1,2,…)
> that is **NOT present** in the multiset.

### How to find mex

Start checking from 0 upward:

* If 0 is missing → mex = 0
* Else if 1 is missing → mex = 1
* Else if 2 is missing → mex = 2
  …and so on.

### Examples

* mex(({1,2,3})) = 0
* mex(({0,2,3})) = 1
* mex(({0,1,2,4})) = 3
* mex(({0,1,2,3,4,5})) = 6

**Shortcut intuition:**
mex is the **first gap starting from 0**.

---

## 4) Valid Partition (in this problem)

A partition ( s_1, s_2, …, s_k ) is called **valid** if:

> All parts have the **same mex**.

So if:

* mex((s_1)) = mex((s_2)) = … = mex((s_k))
  then the partition is valid.

Example:
(A={0,0,0})

Partition:

* ({0} + {0} + {0})

Each part has mex = 1 → valid.

---

## 5) Score of a Valid Partition

If a partition is valid, its **score** is:

> that common mex value.

So in the example above, score = 1.

---

## 6) What the Problem Asks

You are given multiset (A).
You can partition it in any way you want, **but only valid partitions count**.

Goal:

> Find the **minimum possible score**
> among all valid partitions of (A).

---

### Tiny sanity rules

* If (A) has **no 0**, every part misses 0 → mex always 0 → min score 0.
* If every part must contain 0 but no part can contain 1 → mex forced to 1.
* mex can **never be negative**, so minimum score is ≥ 0.

---

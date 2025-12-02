
# ✅ Topic: Making Elements Unique / Distinct in C++

You’re learning two very common ways to get distinct (no-duplicate) values from an array/vector:

1. **Sort + unique + erase**
2. **Using a set**

Let’s understand both clearly.

---

## 1) Sort + `unique()` + `erase()`

### Code

```cpp
vector<int> v = arr;    
sort(v.begin(), v.end());
v.erase(unique(v.begin(), v.end()), v.end());
```

### What each line does

#### ✅ `vector<int> v = arr;`

* Makes a copy of `arr` into `v`.
* So the original array stays unchanged.

#### ✅ `sort(v.begin(), v.end());`

* Sorts `v` in increasing order.
* Sorting puts duplicates next to each other, like:

  ```
  before:  3 1 2 3 2 1
  after:   1 1 2 2 3 3
  ```

#### ✅ `unique(v.begin(), v.end())`

* **Does NOT delete elements by itself.**
* It only moves unique elements to the front and returns an iterator (`it`) to the new logical end.

Example:

```
v = [1 1 2 2 3 3]
unique(...) rearranges to:
v = [1 2 3 ? ? ?]
           ^
           iterator returned here
```

#### ✅ `v.erase(it, v.end())`

* Deletes everything from that iterator to the real end.
* Final result:

  ```
  v = [1 2 3]
  ```

---

### Final output meaning

After these 3 lines:

* `v` contains **distinct elements**
* **sorted**
* no duplicates

---

### Time & memory

* Sorting cost: **O(n log n)**
* Extra memory: **O(n)** (because you copy arr)

---

### When to use this

✅ Use this when:

* you want **sorted distinct values**
* ordering doesn’t matter (or sorted is fine)
* you might need to do neighbor comparisons after

---

## 2) Using a `set` for distinct values

### Code

```cpp
set<int> distinct(arr.begin(), arr.end());
```

### What this does

* A `set` stores only **unique values**.
* Any duplicate insertion is ignored automatically.
* Also keeps values **sorted**.

Example:

```
arr:  3 1 2 3 2 1
set: {1, 2, 3}
```

---

### How to print them

```cpp
for(int x : distinct){
    cout << x << " ";
}
```

---

### Time & memory

* Each insert is `O(log n)`
* Total: **O(n log n)**
* Extra memory: **O(k)** for k unique elements

---

### When to use this

✅ Use this when:

* you want distinct values quickly
* you don’t care about original order
* you want auto-sorting without calling `sort()`

---

## ⚔️ Comparison

| Method                | Result Order | Speed            | Notes                   |
| --------------------- | ------------ | ---------------- | ----------------------- |
| sort + unique + erase | sorted       | fast in practice | best for vectors        |
| set<int>              | sorted       | a bit slower     | simpler but no indexing |

---

## ⚠️ Important warnings

### 🔸 `unique()` only removes adjacent duplicates

So you must sort first.
If you skip sort:

```
3 1 3 2
unique() won't remove the two 3s
```

### 🔸 `set` has no indexing

You can’t do:

```cpp
distinct[i];  // ❌ invalid
```

You must iterate.

---

## ✅ Quick mental summary

* **Vector way** = “sort then collapse duplicates”
* **Set way** = “auto unique + auto sorted”

---

# How `map` Works in This Problem 🗺️

## What is a Map?

A `map` is like a **dictionary** or **phone book**:
- **Key** → **Value**
- Example: `map<int, int>` means Integer Key → Integer Value

---

## Visual Representation

### Our `needed` map:

```cpp
map<int, int> needed;
needed[0] = 3;
needed[1] = 1;
needed[2] = 2;
needed[3] = 1;
needed[5] = 1;
```

**Visualized as a table:**

```
┌─────────┬─────────┐
│   KEY   │  VALUE  │
│ (digit) │ (count) │
├─────────┼─────────┤
│    0    │    3    │  ← Need THREE 0's
│    1    │    1    │  ← Need ONE 1
│    2    │    2    │  ← Need TWO 2's
│    3    │    1    │  ← Need ONE 3
│    5    │    1    │  ← Need ONE 5
└─────────┴─────────┘
```

---

## How `current` map gets updated:

Let's trace through **Example: 2 0 1 2 3**

### Initial State:
```cpp
map<int, int> current;  // Empty map
```

```
current map: EMPTY
┌─────────┬─────────┐
│   KEY   │  VALUE  │
└─────────┴─────────┘
```

---

### Step 1: Draw digit `2`

```cpp
current[arr[i]]++;  // current[2]++
```

**What happens internally:**
1. Check if key `2` exists in map → NO
2. Create new entry with key `2`, value `0`
3. Increment: `0 + 1 = 1`

```
current map:
┌─────────┬─────────┐
│   KEY   │  VALUE  │
├─────────┼─────────┤
│    2    │    1    │
└─────────┴─────────┘
```

---

### Step 2: Draw digit `0`

```cpp
current[0]++;
```

```
current map:
┌─────────┬─────────┐
│   KEY   │  VALUE  │
├─────────┼─────────┤
│    0    │    1    │  ← NEW
│    2    │    1    │
└─────────┴─────────┘
```

---

### Step 3: Draw digit `1`

```cpp
current[1]++;
```

```
current map:
┌─────────┬─────────┐
│   KEY   │  VALUE  │
├─────────┼─────────┤
│    0    │    1    │
│    1    │    1    │  ← NEW
│    2    │    1    │
└─────────┴─────────┘
```

---

### Step 4: Draw digit `2` (again!)

```cpp
current[2]++;  // Key 2 already exists!
```

**What happens:**
1. Key `2` exists? → YES
2. Get current value: `1`
3. Increment: `1 + 1 = 2`

```
current map:
┌─────────┬─────────┐
│   KEY   │  VALUE  │
├─────────┼─────────┤
│    0    │    1    │
│    1    │    1    │
│    2    │    2    │  ← UPDATED!
└─────────┴─────────┘
```

---

### Step 5: Draw digit `3`

```cpp
current[3]++;
```

```
current map:
┌─────────┬─────────┐
│   KEY   │  VALUE  │
├─────────┼─────────┤
│    0    │    1    │
│    1    │    1    │
│    2    │    2    │
│    3    │    1    │  ← NEW
└─────────┴─────────┘
```

---

## The Comparison Logic 🔍

```cpp
for(auto& p : needed){
    if(current[p.first] < p.second){
        canForm = false;
        break;
    }
}
```

### What is `auto& p`?

`p` is a **pair** with:
- `p.first` = KEY (the digit)
- `p.second` = VALUE (count needed)

### Visual Comparison at Step 5:

```
NEEDED map:              CURRENT map:
┌─────┬─────┐           ┌─────┬─────┐
│  0  │  3  │           │  0  │  1  │  ❌ 1 < 3
│  1  │  1  │           │  1  │  1  │  ✅ 1 = 1
│  2  │  2  │           │  2  │  2  │  ✅ 2 = 2
│  3  │  1  │           │  3  │  1  │  ✅ 1 = 1
│  5  │  1  │           │  5  │  0  │  ❌ 0 < 1 (key doesn't exist = 0)
└─────┴─────┘           └─────┴─────┘

Result: canForm = FALSE (missing enough 0's and 5's)
```

---

## Key Map Operations in Our Code:

### 1. **Insertion/Update:**
```cpp
current[arr[i]]++;
```
- If key exists → increment value
- If key doesn't exist → create with value 0, then increment to 1

### 2. **Access:**
```cpp
current[p.first]
```
- If key exists → return its value
- If key doesn't exist → return 0 (default for int)

### 3. **Iteration:**
```cpp
for(auto& p : needed)
```
Loops through each key-value pair:
```
Iteration 1: p.first=0, p.second=3
Iteration 2: p.first=1, p.second=1
Iteration 3: p.first=2, p.second=2
Iteration 4: p.first=3, p.second=1
Iteration 5: p.first=5, p.second=1
```

---

## Real Example Trace:

**Input:** `2 0 1 2 3 2 5 0 0`

```
Step 9: current[0]++ (third time)

Before: current[0] = 2
After:  current[0] = 3

Check against needed:
┌──────┬────────┬─────────┬────────┐
│Digit │ Need   │ Have    │ Status │
├──────┼────────┼─────────┼────────┤
│  0   │   3    │   3     │   ✅   │
│  1   │   1    │   1     │   ✅   │
│  2   │   2    │   3     │   ✅   │
│  3   │   1    │   1     │   ✅   │
│  5   │   1    │   1     │   ✅   │
└──────┴────────┴─────────┴────────┘

ALL ✅ → canForm = true → Answer = 9
```

---

## Summary:

**Map = Counter for digits**
- **Key** = Which digit (0-9)
- **Value** = How many times we've seen it
- **`++`** = Add one to the count
- **Compare** = Check if we have enough of each digit

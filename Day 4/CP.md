# Problem Explanation: A. Equal Occurrences

Let me break this down with clear visuals!

---

## Understanding "Balanced"

**Balanced array:** All elements appear the **same number of times**.

### Examples:

```
✓ [1,1,3,3,6,6]
  1 appears 2 times
  3 appears 2 times
  6 appears 2 times
  All equal → Balanced!

✓ [2,2,2,2]
  2 appears 4 times
  Only one element → Balanced!

✗ [1,2,3,3]
  1 appears 1 time
  2 appears 1 time
  3 appears 2 times
  Not all equal → NOT Balanced!
```

---

## Problem Goal

Given array `a`, find the **longest subsequence** that is balanced.

**Subsequence:** Can skip elements, but maintain order.

---

## Example 1: `[1, 1, 4, 4, 4]`

### Step 1: Count occurrences
```
Element | Count
--------|------
   1    |   2
   4    |   3
```

### Step 2: Try different frequencies

**Frequency = 1:** Take 1 of each element
```
[1, 4]
Length = 2
```

**Frequency = 2:** Take 2 of each element
```
[1, 1, 4, 4]  ← Take first 2 ones, first 2 fours
Length = 4 ✓
```

**Frequency = 3:** Take 3 of each element
```
Need: 1 appears 3 times (but only have 2) ✗
Can't do this!
```

**Best:** Length = 4

---

## Example 2: `[1, 2]`

### Count occurrences
```
Element | Count
--------|------
   1    |   1
   2    |   1
```

### Try frequencies

**Frequency = 1:** Take 1 of each
```
[1, 2]
Length = 2 ✓
```

**Best:** Length = 2

---

## Example 3: `[1,1,1,1,1, 2,2,2,2, 3,3,3, 4,4, 5]`

### Count occurrences
```
Element | Count
--------|------
   1    |   5
   2    |   4
   3    |   3
   4    |   2
   5    |   1
```

### Try frequencies

**Frequency = 1:**
```
[1, 2, 3, 4, 5]
Length = 5 × 1 = 5
```

**Frequency = 2:**
```
[1,1, 2,2, 3,3, 4,4]
Elements: 1,2,3,4 (need ≥2 each)
Length = 4 × 2 = 8
```

**Frequency = 3:**
```
[1,1,1, 2,2,2, 3,3,3]
Elements: 1,2,3 (need ≥3 each)
Length = 3 × 3 = 9 ✓
```

**Frequency = 4:**
```
Need 1,2 with count ≥4
[1,1,1,1, 2,2,2,2]
Length = 2 × 4 = 8
```

**Frequency = 5:**
```
Only element 1 has count ≥5
[1,1,1,1,1]
Length = 1 × 5 = 5
```

**Best:** Length = 9

---

## Example 4: `[3,3,3,3,3]`

### Count occurrences
```
Element | Count
--------|------
   3    |   5
```

All frequencies work since there's only one element:
```
Frequency = 5: [3,3,3,3,3]
Length = 5 ✓
```

---

## Algorithm

```
1. Count frequency of each element
2. For each possible frequency k (from 1 to max_count):
   - Count how many elements have frequency ≥ k
   - Length = (number of elements) × k
3. Return maximum length
```

---

## Visual Algorithm

```
Array: [1,1,4,4,4]

Frequency count:
1 → 2 times
4 → 3 times

Try k=1:
┌───┬───┐
│ 1 │ 4 │  Elements with count ≥ 1: both
└───┴───┘  
Length = 2 elements × 1 = 2

Try k=2:
┌───┬───┬───┬───┐
│ 1 │ 1 │ 4 │ 4 │  Elements with count ≥ 2: both
└───┴───┴───┴───┘
Length = 2 elements × 2 = 4 ✓

Try k=3:
┌───┬───┬───┬───┬───┐
│ 1 │ 1 │ 1 │ 4 │ 4 │  Elements with count ≥ 3: only 4
└───┴───┴───┴───┴───┘  
But 1 only has 2! Can't use k=3 for all ✗
Only 4 works: Length = 1 × 3 = 3

Maximum = 4
```

---

## Solution Code

```cpp
#include <bits/stdc++.h>
using namespace std;

int main()
{
    int t;
    cin >> t;
    
    while(t--){
        int n;
        cin >> n;
        vector<int> a(n);
        
        for(int i = 0; i < n; i++){
            cin >> a[i];
        }
        
        // Count frequency of each element
        map<int, int> freq;
        for(int i = 0; i < n; i++){
            freq[a[i]]++;
        }
        
        int maxLength = 0;
        
        // Try each possible frequency k
        for(int k = 1; k <= n; k++){
            int count = 0;
            
            // Count how many distinct elements have frequency >= k
            for(auto& p : freq){
                if(p.second >= k){
                    count++;
                }
            }
            
            // Length = count × k
            int length = count * k;
            maxLength = max(maxLength, length);
        }
        
        cout << maxLength << endl;
    }
    
    return 0;
}
```

---

## Test with Example 1

```
Input: [1,1,4,4,4]

Frequency map:
1 → 2
4 → 3

k=1: Elements with freq≥1: 2 → Length = 2×1 = 2
k=2: Elements with freq≥2: 2 → Length = 2×2 = 4 ✓
k=3: Elements with freq≥3: 1 → Length = 1×3 = 3
k=4: Elements with freq≥4: 0 → Length = 0×4 = 0

Maximum = 4 ✓
```

---

## Key Insight

```
For frequency k:
- Only use elements that appear ≥ k times
- Take exactly k copies of each such element
- Result: all elements have same count (k)

Formula: Length = (# of elements with count ≥ k) × k
```






# Detailed Visualization: Frequency Loop

Let me visualize this step-by-step with Example 1!

---

## Example: `[1, 1, 4, 4, 4]`

### Step 1: Build Frequency Map

```cpp
map<int, int> freq;
// After counting:

freq = {
    1 → 2,  // Element 1 appears 2 times
    4 → 3   // Element 4 appears 3 times
}
```

---

## Step 2: Try Different Values of k

### **Iteration k=1**

```cpp
for(int k = 1; k <= n; k++){  // k = 1
    int count = 0;
    
    for(auto& p : freq){
        if(p.second >= k){  // Check if frequency >= 1
            count++;
        }
    }
```

**Visual Check:**

```
Checking k = 1 (need elements with frequency ≥ 1)

freq map:
┌─────────┬───────────┐
│ Element │ Frequency │
├─────────┼───────────┤
│    1    │     2     │ ← 2 >= 1? YES ✓ count++
│    4    │     3     │ ← 3 >= 1? YES ✓ count++
└─────────┴───────────┘

count = 2 elements qualify

Subsequence we can form:
[1, 4]  (take 1 copy of each)
       ↑  ↑
    element element
       1     4

Length = count × k = 2 × 1 = 2
```

---

### **Iteration k=2**

```cpp
for(int k = 1; k <= n; k++){  // k = 2
    int count = 0;
    
    for(auto& p : freq){
        if(p.second >= k){  // Check if frequency >= 2
            count++;
        }
    }
```

**Visual Check:**

```
Checking k = 2 (need elements with frequency ≥ 2)

freq map:
┌─────────┬───────────┐
│ Element │ Frequency │
├─────────┼───────────┤
│    1    │     2     │ ← 2 >= 2? YES ✓ count++
│    4    │     3     │ ← 3 >= 2? YES ✓ count++
└─────────┴───────────┘

count = 2 elements qualify

Subsequence we can form:
[1, 1, 4, 4]  (take 2 copies of each)
 ↑  ↑  ↑  ↑
 element 1  element 4
 (2 times)  (2 times)

Length = count × k = 2 × 2 = 4 ✓
```

---

### **Iteration k=3**

```cpp
for(int k = 1; k <= n; k++){  // k = 3
    int count = 0;
    
    for(auto& p : freq){
        if(p.second >= k){  // Check if frequency >= 3
            count++;
        }
    }
```

**Visual Check:**

```
Checking k = 3 (need elements with frequency ≥ 3)

freq map:
┌─────────┬───────────┐
│ Element │ Frequency │
├─────────┼───────────┤
│    1    │     2     │ ← 2 >= 3? NO ✗ skip
│    4    │     3     │ ← 3 >= 3? YES ✓ count++
└─────────┴───────────┘

count = 1 element qualifies

Subsequence we can form:
[4, 4, 4]  (take 3 copies of element 4)
 ↑  ↑  ↑
 element 4
 (3 times)

Can't include element 1 (only has 2 copies)

Length = count × k = 1 × 3 = 3
```

---

### **Iteration k=4**

```cpp
for(int k = 1; k <= n; k++){  // k = 4
    int count = 0;
    
    for(auto& p : freq){
        if(p.second >= k){  // Check if frequency >= 4
            count++;
        }
    }
```

**Visual Check:**

```
Checking k = 4 (need elements with frequency ≥ 4)

freq map:
┌─────────┬───────────┐
│ Element │ Frequency │
├─────────┼───────────┤
│    1    │     2     │ ← 2 >= 4? NO ✗ skip
│    4    │     3     │ ← 3 >= 4? NO ✗ skip
└─────────┴───────────┘

count = 0 elements qualify

No subsequence possible!

Length = count × k = 0 × 4 = 0
```

---

### **Iteration k=5**

```cpp
Same as k=4, no elements have frequency ≥ 5
count = 0
Length = 0
```

---

## Summary Table

```
┌─────┬─────────────────────────┬─────────┬──────────┐
│  k  │ Elements with freq ≥ k  │  count  │  Length  │
├─────┼─────────────────────────┼─────────┼──────────┤
│  1  │ {1, 4}                  │    2    │  2×1=2   │
│  2  │ {1, 4}                  │    2    │  2×2=4   │ ← MAX!
│  3  │ {4}                     │    1    │  1×3=3   │
│  4  │ {}                      │    0    │  0×4=0   │
│  5  │ {}                      │    0    │  0×5=0   │
└─────┴─────────────────────────┴─────────┴──────────┘

Maximum Length = 4
```

---

## Visual Flow Diagram

```
Array: [1, 1, 4, 4, 4]
         ↓
    Count Frequencies
         ↓
    ┌──────────┐
    │ freq map │
    │  1 → 2   │
    │  4 → 3   │
    └──────────┘
         ↓
    Try k=1, k=2, k=3, ...
         ↓
    ┌─────────────────────────┐
    │ k=1: Both qualify (2,3≥1)│
    │ → 2 elements × 1 = 2     │
    ├─────────────────────────┤
    │ k=2: Both qualify (2,3≥2)│
    │ → 2 elements × 2 = 4 ✓   │
    ├─────────────────────────┤
    │ k=3: Only 4 (3≥3, 2<3)   │
    │ → 1 element × 3 = 3      │
    └─────────────────────────┘
         ↓
    Return Maximum = 4
```

---

## What `p.second >= k` Means

```cpp
for(auto& p : freq){
    // p is a pair: {element, frequency}
    // p.first = element value (1 or 4)
    // p.second = frequency (2 or 3)
    
    if(p.second >= k){
        count++;
    }
}
```

**Example when k=2:**

```
Iteration 1:
p = {1, 2}
p.first = 1 (element)
p.second = 2 (frequency)
Is 2 >= 2? YES → count = 1

Iteration 2:
p = {4, 3}
p.first = 4 (element)
p.second = 3 (frequency)
Is 3 >= 2? YES → count = 2
```

---

## Real-World Analogy

```
Think of it like organizing a team:

k = Required team size per element

freq map = Available players
- Element 1 has 2 players
- Element 4 has 3 players

Question: "Can we form balanced teams of size k?"

k=1: Need 1 player per element
     ✓ Both have ≥1 → 2 teams of 1 = 2 total

k=2: Need 2 players per element
     ✓ Both have ≥2 → 2 teams of 2 = 4 total

k=3: Need 3 players per element
     ✓ Only element 4 has ≥3 → 1 team of 3 = 3 total

k=4: Need 4 players per element
     ✗ Nobody has ≥4 → 0 teams = 0 total
```

Perfect! 🎯

# How `map<int, int>` Works Internally

Let me explain with detailed visualizations!

---

## What is a Map?

```cpp
map<int, int> freq;
```

A `map` is a **self-balancing binary search tree** (specifically, a **Red-Black Tree** in C++ STL).

---

## Internal Structure

### Visual Representation:

```
map<int, int> freq;

Internally stored as a Red-Black Tree:

            ┌─────────┐
            │ Key: 4  │
            │ Val: 3  │
            └────┬────┘
                 │
        ┌────────┴────────┐
        │                 │
    ┌───┴───┐         ┌───┴───┐
    │ Key: 1│         │ Key: 7│
    │ Val: 2│         │ Val: 1│
    └───────┘         └───────┘

Properties:
✓ Keys are sorted (1 < 4 < 7)
✓ Balanced tree (O(log n) operations)
✓ No duplicate keys
```

---

## Step-by-Step: `freq[a[i]]++`

Let's trace through: `array = [1, 4, 1, 4, 4]`

---

### **Iteration 1: i=0, a[0]=1**

```cpp
freq[1]++;
// Equivalent to:
// freq[1] = freq[1] + 1;
```

**What happens:**
1. Search for key `1` in map
2. Key `1` doesn't exist → **create new entry** with default value `0`
3. Increment: `0 + 1 = 1`

```
Map after:
┌─────────┐
│ Key: 1  │
│ Val: 1  │ ← Created and set to 1
└─────────┘
```

---

### **Iteration 2: i=1, a[1]=4**

```cpp
freq[4]++;
```

**What happens:**
1. Search for key `4` in map
2. Key `4` doesn't exist → **create new entry** with default value `0`
3. Increment: `0 + 1 = 1`

```
Map after:
    ┌─────────┐
    │ Key: 1  │
    │ Val: 1  │
    └────┬────┘
         │
         └─────────┐
                   │
               ┌───┴───┐
               │ Key: 4│
               │ Val: 1│ ← Created and set to 1
               └───────┘
```

---

### **Iteration 3: i=2, a[2]=1**

```cpp
freq[1]++;
```

**What happens:**
1. Search for key `1` in map
2. Key `1` **already exists** with value `1`
3. Increment: `1 + 1 = 2`

```
Map after:
    ┌─────────┐
    │ Key: 1  │
    │ Val: 2  │ ← Updated to 2
    └────┬────┘
         │
         └─────────┐
                   │
               ┌───┴───┐
               │ Key: 4│
               │ Val: 1│
               └───────┘
```

---

### **Iteration 4: i=3, a[3]=4**

```cpp
freq[4]++;
```

**What happens:**
1. Search for key `4` in map
2. Key `4` **already exists** with value `1`
3. Increment: `1 + 1 = 2`

```
Map after:
    ┌─────────┐
    │ Key: 1  │
    │ Val: 2  │
    └────┬────┘
         │
         └─────────┐
                   │
               ┌───┴───┐
               │ Key: 4│
               │ Val: 2│ ← Updated to 2
               └───────┘
```

---

### **Iteration 5: i=4, a[4]=4**

```cpp
freq[4]++;
```

**What happens:**
1. Search for key `4` in map
2. Key `4` **already exists** with value `2`
3. Increment: `2 + 1 = 3`

```
Final Map:
    ┌─────────┐
    │ Key: 1  │
    │ Val: 2  │
    └────┬────┘
         │
         └─────────┐
                   │
               ┌───┴───┐
               │ Key: 4│
               │ Val: 3│ ← Updated to 3
               └───────┘
```

---

## Behind `freq[key]++`

### Step-by-step breakdown:

```cpp
freq[1]++;

// Is equivalent to:
freq.operator[](1)++;

// Which does:
1. Search for key 1 in the tree
2. If NOT found:
   - Insert new node with key=1, value=0 (default)
3. If found:
   - Return reference to existing value
4. Increment the value
```

---

## Visual Memory Layout

```
Array: [1, 4, 1, 4, 4]

Step 1: freq[1]++
┌───────────┐
│ Node      │
│ key: 1    │
│ value: 1  │
│ left: null│
│ right:null│
└───────────┘

Step 2: freq[4]++
┌───────────┐
│ Node      │
│ key: 1    │────┐
│ value: 1  │    │
│ left: null│    │
│ right: ●  │───→│   ┌───────────┐
└───────────┘    └──→│ Node      │
                     │ key: 4    │
                     │ value: 1  │
                     │ left: null│
                     │ right:null│
                     └───────────┘

Step 3: freq[1]++
┌───────────┐
│ Node      │
│ key: 1    │────┐
│ value: 2  │← Update!
│ left: null│    │
│ right: ●  │───→│   ┌───────────┐
└───────────┘    └──→│ Node      │
                     │ key: 4    │
                     │ value: 1  │
                     └───────────┘

... and so on
```

---

## Key Operations & Time Complexity

```
┌──────────────────┬──────────────┬─────────────┐
│   Operation      │ Time         │ Reason      │
├──────────────────┼──────────────┼─────────────┤
│ freq[key]        │ O(log n)     │ Tree search │
│ freq[key]++      │ O(log n)     │ Search+inc  │
│ Insert new       │ O(log n)     │ Balance tree│
│ Search           │ O(log n)     │ Tree height │
│ Iterate all      │ O(n)         │ Visit all   │
└──────────────────┴──────────────┴─────────────┘

n = number of elements in map
```

---

## Why Red-Black Tree?

```
Benefits:
✓ Always sorted keys (in-order traversal gives sorted sequence)
✓ Balanced tree (height = O(log n))
✓ Fast operations: insert, delete, search = O(log n)
✓ No duplicates automatically

Example:
Insert order: [4, 1, 7, 3, 9, 2]

Stored as:
        4
       / \
      2   7
     / \   \
    1   3   9

Iteration gives: 1, 2, 3, 4, 7, 9 (sorted!)
```

---

## Alternative: `unordered_map`

```cpp
unordered_map<int, int> freq;  // Hash table instead

Differences:
┌────────────────┬─────────────┬──────────────────┐
│   Feature      │    map      │ unordered_map    │
├────────────────┼─────────────┼──────────────────┤
│ Structure      │ Red-Black   │ Hash Table       │
│                │ Tree        │                  │
├────────────────┼─────────────┼──────────────────┤
│ Time           │ O(log n)    │ O(1) average     │
│                │             │ O(n) worst       │
├────────────────┼─────────────┼──────────────────┤
│ Ordered keys?  │ YES ✓       │ NO ✗             │
├────────────────┼─────────────┼──────────────────┤
│ Memory         │ More        │ Less             │
└────────────────┴─────────────┴──────────────────┘
```

---

## Complete Example

```cpp
#include <bits/stdc++.h>
using namespace std;

int main(){
    map<int, int> freq;
    
    vector<int> arr = {1, 4, 1, 4, 4};
    
    cout << "Processing array: [1, 4, 1, 4, 4]\n\n";
    
    for(int i = 0; i < arr.size(); i++){
        freq[arr[i]]++;
        
        cout << "After freq[" << arr[i] << "]++:\n";
        for(auto& p : freq){
            cout << "  " << p.first << " → " << p.second << "\n";
        }
        cout << "\n";
    }
    
    return 0;
}
```

**Output:**
```
Processing array: [1, 4, 1, 4, 4]

After freq[1]++:
  1 → 1

After freq[4]++:
  1 → 1
  4 → 1

After freq[1]++:
  1 → 2
  4 → 1

After freq[4]++:
  1 → 2
  4 → 2

After freq[4]++:
  1 → 2
  4 → 3
```

---

## Summary

```
map<int, int> freq;
freq[key]++;

How it works:
1. Search tree for 'key' → O(log n)
2. If not found:
   - Create node with value = 0
3. Increment value
4. Rebalance tree if needed

Result: Efficient counting with sorted keys!
```

Perfect! 🎯

# 🗂️ Arrays

## 📖 Definition

An **array** is a collection of items of the same data type stored at **contiguous (one after another) memory locations**.

<img src="image-3.png" alt="Arrays" width="300" height="350">

Arrays are one of the **simplest and most widely used data structures**, and they have a **small memory footprint** compared to other structures.

✅ **Use case**: Use arrays when you need to **store and iterate over data** efficiently.

---

## 🧠 Visual Memory Layout

Here’s a simple view of how arrays are stored in **contiguous memory**:

```
Index:   0     1     2     3
Value:  [10]  [20]  [30]  [40]
Address:1000 1004  1008  1012  → (for 4-byte integers)
```

Each element sits **next to each other** in memory, which allows **constant-time access (O(1))** using its index.

---

## ⏱️ Time & Space Complexity

![Time Complexity](image-4.png)

* **Space Complexity**:

  * Worst case: `O(n)`

---

## 🧩 Types of Arrays

### 1. 📌 Static Arrays

* **Fixed size** at creation — cannot grow or shrink.
* Memory is allocated **once** and stays constant.
* Contents can change, but **capacity cannot**.

#### 💡 Example

**C**

```c
#include <stdio.h>

int main() {
    int numbers[5] = {1, 2, 3, 4, 5};

    // Access elements
    printf("First element: %d\n", numbers[0]);

    // Modify element
    numbers[2] = 99;
    printf("Modified 3rd element: %d\n", numbers[2]);

    return 0;
}
```

**Python**

```python
numbers = [1, 2, 3, 4, 5]
print("First element:", numbers[0])

numbers[2] = 99
print("Modified 3rd element:", numbers[2])
```

---

### 2. 📌 Dynamic Arrays

* Can **grow or shrink** during runtime.
* Allow **adding/removing** elements dynamically.
* Commonly used in **modern programming languages** (like Python, JavaScript, C++ `vector`).

#### 💡 Example

**C++ (using `vector`)**

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> nums = {1, 2, 3};
    nums.push_back(4); // Add element
    nums.erase(nums.begin() + 1); // Remove 2nd element

    for (int n : nums)
        cout << n << " "; // Output: 1 3 4
}
```

**Python**

```python
nums = [1, 2, 3]
nums.append(4)    # Add
nums.pop(1)       # Remove 2nd element

print(nums)  # [1, 3, 4]
```

---

## ⚙️ When to Use Arrays

✅ **Arrays are good at:**

* Fast lookups → `O(1)`
* Fast push/pop (at end)
* Ordered data

❌ **Arrays are bad at:**

* Slow inserts (not at end)
* Slow deletes (not at end)
* Fixed size *(if static array)*

---

## ⚖️ Visual Summary

| Feature           | Static Array  | Dynamic Array                     |
| ----------------- | ------------- | --------------------------------- |
| Size              | Fixed         | Flexible                          |
| Memory Allocation | Compile-time  | Runtime                           |
| Insert/Delete     | Slow          | Moderate                          |
| Lookup            | Fast (`O(1)`) | Fast (`O(1)`)                     |
| Examples          | C array       | Python list, JS array, C++ vector |

---

## 🧮 Truth Table (Conceptual Behavior)

| Operation          | Static Array    | Dynamic Array   |
| ------------------ | --------------- | --------------- |
| `Insert at end`    | ✅ Fast          | ✅ Fast          |
| `Insert in middle` | ❌ Slow          | ⚠️ Moderate     |
| `Delete last`      | ✅ Fast          | ✅ Fast          |
| `Delete middle`    | ❌ Slow          | ⚠️ Moderate     |
| `Resize`           | ❌ Not possible  | ✅ Possible      |
| `Access index`     | ✅ Constant time | ✅ Constant time |

---

## 💬 Key Takeaway

Arrays are **foundational data structures** that offer:

* **Speed** for access and traversal.
* **Predictable memory use**.
* The tradeoff of **fixed size** (static) vs **dynamic resizing** (dynamic).

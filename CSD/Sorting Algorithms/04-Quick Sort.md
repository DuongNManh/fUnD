# 📘 Quick Sort

## 🧭 1. Overview

Quick Sort is a **divide-and-conquer**, **in-place**, and highly practical sorting algorithm invented by **Tony Hoare**. It is widely used in real-world systems because it is fast, requires very little memory overhead, and minimizes data movement.

---

## ⭐ 2. Key Characteristics

* **In-place sorting**: Does not require additional arrays (unlike Merge Sort).
* **Divide and Conquer**: Divides the array into two partitions based on a *pivot*.
* **Efficient on average**: Average time complexity: **O(n log n)**.
* **Worst-case**: **O(n²)** if pivots are consistently bad (e.g., always picking min/max).
* **Pivot selection matters**: Good choices include random pivot or median-of-three.

---

## 🎯 3. The Core Idea

Quick Sort works by repeatedly partitioning the array around a *pivot* element.

### ⚡ Steps

Given an input array **A**, Quick Sort works in three main steps:

1. **Select a pivot** (commonly the last element, but could be random).
2. **Partition** the array so that:

   * All elements **≤ pivot** go to the left
   * All elements **≥ pivot** go to the right
   * Pivot ends up in its **final sorted position**
3. **Recursively apply Quick Sort** to the left and right subarrays.
4. Stop when subarray size is 0 or 1.

---

### 🔀 Divide & Conquer Comparison

| Algorithm  | Divide Step             | Combine Step            |
| ---------- | ----------------------- | ----------------------- |
| Merge Sort | trivial (split in half) | heavy (merge)           |
| Quick Sort | heavy (partition, Θ(n)) | trivial (concat halves) |

---

### 🧠 Why this works

After partitioning:

* All values on the left are ≤ pivot.
* All values on the right are ≥ pivot.
* The pivot is already in its final correct position.

So we only need to sort the left and right halves.

---

## 🔍 4. Visual Example of Partitioning

Array before sorting:

```cpp
[1, 7, 2, 4, 6, 8, 3]
```

Choose pivot (last element):

```cpp
pivot = 3
```

Partition result (one possible outcome):

```cpp
[1, 2, | 3 | 4, 6, 7, 8]
```

* Left side (≤3): `1, 2`
* Right side (≥3): `4, 6, 7, 8`
* Pivot `3` is now in correct position.

Then recursively sort:

* Left → `[1, 2]`
* Right → `[4, 6, 7, 8]`

Complete sorted array:

```cpp
[1, 2, 3, 4, 6, 7, 8]
```

Or you can see the sample below:

![quicksort](quicksort.gif)

---

## 🧩 5. Pseudocode (Conceptual)

### **Quicksort Pseudocode**

```cpp
QuickSort(A, left, right):
    if right - left <= 1:
        # 0 or 1 element: already sorted
        # 2 elements: compare and swap
        return

    pivot = A[right]
    p = Partition(A, left, right)

    QuickSort(A, left, p - 1)
    QuickSort(A, p + 1, right)
```

### **Partition Pseudocode**

Rearrange A in-place so all elements ≤ pivot go left, ≥ pivot go right.
Returns the pivot's final index.

```cpp
PARTITION(A, left, right):
    pivotValue = A[right]
    partitionIndex = left

    for i from left to right - 1:
        if A[i] < pivotValue:
            swap A[i] and A[partitionIndex]
            partitionIndex++

    swap A[partitionIndex] and A[right]
    return partitionIndex
```

---

## 💻 6. Implementations

### 🔵 C++

```cpp
#include <iostream>
#include <vector>
using namespace std;

void swapVals(int &a, int &b) {
    int temp = a;
    a = b;
    b = temp;
}

int partition(vector<int>& arr, int left, int right) {
    int pivot = arr[right]; // we usely pick the last ele to pivot
    int partitionIndex = left; // init the index should placed the swaped ele

    for (int i = left; i < right; i++) { // scan the array
        if (arr[i] < pivot) {
            swapVals(arr[i], arr[partitionIndex]); // swap the position if arr[i] < pivot to index
            partitionIndex++; // the next place 
        }
    }
    swapVals(arr[partitionIndex], arr[right]); // swap the pivot to partion index after arrange
    return partitionIndex; // using for break arr for futher recursive sorting
}

void quickSort(vector<int>& arr, int left, int right) {
    if (left < right) {
        int p = partition(arr, left, right); // get the break position
        quickSort(arr, left, p - 1); // sort left part
        quickSort(arr, p + 1, right); // sort right part
    }
}

int main() {
    vector<int> arr = {99, 44, 6, 2, 1, 5, 63, 87, 283, 4, 0};
    quickSort(arr, 0, arr.size() - 1);

    for (int n : arr) cout << n << " ";
}
```

---

### 🟢 Python

```python
def partition(arr, left, right):
    pivot = arr[right]
    partition_index = left

    for i in range(left, right):
        if arr[i] < pivot:
            arr[i], arr[partition_index] = arr[partition_index], arr[i]
            partition_index += 1

    arr[partition_index], arr[right] = arr[right], arr[partition_index]
    return partition_index


def quick_sort(arr, left, right):
    if left < right:
        p = partition(arr, left, right)
        quick_sort(arr, left, p - 1)
        quick_sort(arr, p + 1, right)
    return arr


numbers = [99, 44, 6, 2, 1, 5, 63, 87, 283, 4, 0]
result = quick_sort(numbers, 0, len(numbers) - 1)
print(result)
```

---

## 📊 7. Complexity

| Case        | Time       | Reason                        |
| ----------- | ---------- | ----------------------------- |
| **Best**    | O(n log n) | Balanced partitions           |
| **Average** | O(n log n) | Random distribution           |
| **Worst**   | O(n²)      | Pivot always smallest/largest |

Space complexity: **O(1)** auxiliary (in-place), plus recursion stack ~O(log n) on average.

---

## ⚖️ 8. Comparison with Merge Sort

| Feature              | Quick Sort                         | Merge Sort                     |
| -------------------- | ---------------------------------- | ------------------------------ |
| Space                | In-place                           | Requires extra array           |
| Performance          | Faster in practice                 | Stable performance             |
| Worst-case           | O(n²)                              | O(n log n)                     |
| Partitioning/Merging | Partition = heavy, merge = trivial | Merge = heavy, split = trivial |

---

## 📝 9. Summary

Quick Sort:

* Is fast and memory-efficient.
* Uses partition to divide the array.
* Places pivot in final position every step.
* Recursively sorts left and right subarrays.
* Is widely used due to performance and low overhead.

A solid understanding of the partitioning step is key to mastering Quick Sort.

---

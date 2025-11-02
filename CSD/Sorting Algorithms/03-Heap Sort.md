# ⚙️ Heap Sort

**Heap Sort** is a **comparison-based sorting algorithm** that uses a **binary heap** (usually a max-heap) to efficiently sort elements.
It’s an **in-place**, **O(n log n)** algorithm that does not require additional arrays (except temporary swaps).

---

## 🧩 Key Idea

To sort an array **A** in ascending order:

1. **Build a max-heap** from the input array.
2. **Repeatedly extract** the maximum element (the root) and place it at the **end** of the array.
3. **Heapify** the remaining unsorted portion to maintain the heap property.

---

## 🧠 Concept Visualization

Example array:

```cpp
A = [4, 10, 3, 5, 1]
```

### Step 1 — Build Max Heap

Transform the array into a max-heap.

```cpp
        10
       /  \
      5    3
     / \
    4   1
```

Heap array: `[10, 5, 3, 4, 1]`

---

### Step 2 — Sort by Extracting Max

Now, swap the **root (max)** with the **last element**, reduce heap size, and **heapify** again.

| Step | Heap (before swap) | Action                           | Result             |
| ---- | ------------------ | -------------------------------- | ------------------ |
| 1    | `[10, 5, 3, 4, 1]` | swap(10, 1) → heapify(0, size=4) | `[5, 4, 3, 1, 10]` |
| 2    | `[5, 4, 3, 1, 10]` | swap(5, 1) → heapify(0, size=3)  | `[4, 1, 3, 5, 10]` |
| 3    | `[4, 1, 3, 5, 10]` | swap(4, 3) → heapify(0, size=2)  | `[3, 1, 4, 5, 10]` |
| 4    | `[3, 1, 4, 5, 10]` | swap(3, 1) → heapify(0, size=1)  | `[1, 3, 4, 5, 10]` |

✅ **Final Sorted Array:** `[1, 3, 4, 5, 10]`

---

## 🧮 Visualize animation

![Heap Sort](heap_sort_1.gif)

---

## 🧮 Pseudocode

```cpp
procedure heapSort(A):
    n = length(A)

    # Build max heap
    for i = n/2 - 1 downto 0:
        heapify(A, n, i)

    # Extract elements one by one
    for i = n-1 downto 1:
        swap(A[0], A[i])          # Move current max to the end
        heapify(A, i, 0)          # Restore heap property on reduced heap


procedure heapify(A, n, i):
    largest = i
    left = 2*i + 1
    right = 2*i + 2

    if left < n and A[left] > A[largest]:
        largest = left
    if right < n and A[right] > A[largest]:
        largest = right

    if largest != i:
        swap(A[i], A[largest])
        heapify(A, n, largest)
```

---

## 💻 Example in C++

```cpp
#include <iostream>
using namespace std;

void heapify(int arr[], int n, int i) {
    int largest = i;
    int left = 2 * i + 1;
    int right = 2 * i + 2;

    if (left < n && arr[left] > arr[largest])
        largest = left;
    if (right < n && arr[right] > arr[largest])
        largest = right;

    if (largest != i) {
        swap(arr[i], arr[largest]);
        heapify(arr, n, largest);
    }
}

void heapSort(int arr[], int n) {
    // Build max heap
    for (int i = n / 2 - 1; i >= 0; i--)
        heapify(arr, n, i);

    // Extract elements one by one
    for (int i = n - 1; i >= 0; i--) {
        swap(arr[0], arr[i]);
        heapify(arr, i, 0);
    }
}

int main() {
    int arr[] = {4, 10, 3, 5, 1};
    int n = sizeof(arr) / sizeof(arr[0]);

    heapSort(arr, n);

    cout << "Sorted array: ";
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
}
```

🔹 Output:

```cpp
Sorted array: 1 3 4 5 10
```

---

## 🐍 Example in Python

```python
def heapify(arr, n, i):
    largest = i
    left = 2 * i + 1
    right = 2 * i + 2

    if left < n and arr[left] > arr[largest]:
        largest = left
    if right < n and arr[right] > arr[largest]:
        largest = right

    if largest != i:
        arr[i], arr[largest] = arr[largest], arr[i]
        heapify(arr, n, largest)

def heap_sort(arr):
    n = len(arr)

    # Build max heap
    for i in range(n // 2 - 1, -1, -1):
        heapify(arr, n, i)

    # Extract elements one by one
    for i in range(n - 1, 0, -1):
        arr[i], arr[0] = arr[0], arr[i]
        heapify(arr, i, 0)

arr = [4, 10, 3, 5, 1]
heap_sort(arr)
print("Sorted array:", arr)
```

🔹 Output:

```cpp
Sorted array: [1, 3, 4, 5, 10]
```

---

## 📊 Time and Space Complexity

| Phase             | Time Complexity     |
| ----------------- | ------------------- |
| Build Heap        | **O(n)**            |
| Extract (n times) | **O(n log n)**      |
| **Total**         | **O(n log n)**      |
| Space             | **O(1)** (in-place) |

---

## 🧩 Summary

| Property             | Heap Sort                                                       |
| -------------------- | --------------------------------------------------------------- |
| **Type**             | Comparison-based                                                |
| **Data Structure**   | Binary Heap                                                     |
| **Time Complexity**  | O(n log n)                                                      |
| **Space Complexity** | O(1)                                                            |
| **Stable**           | ❌ No                                                            |
| **In-place**         | ✅ Yes                                                           |
| **Best For**         | Arrays where memory is limited and consistent O(n log n) needed |

---

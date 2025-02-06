Here’s an overview of **various sorting algorithms** and their respective time complexities, including their best, worst, and average-case complexities:

---

### 1. **Bubble Sort**
   - **Best Case Complexity**: \(O(n)\) (when the array is already sorted)
   - **Average Case Complexity**: \(O(n^2)\)
   - **Worst Case Complexity**: \(O(n^2)\)
   - **Space Complexity**: \(O(1)\) (in-place sorting)
   - **Stable**: Yes
   - **Description**: Repeatedly compares adjacent elements and swaps them if they are in the wrong order. The process repeats until no swaps are needed.

---

### 2. **Selection Sort**
   - **Best Case Complexity**: \(O(n^2)\)
   - **Average Case Complexity**: \(O(n^2)\)
   - **Worst Case Complexity**: \(O(n^2)\)
   - **Space Complexity**: \(O(1)\) (in-place sorting)
   - **Stable**: No
   - **Description**: Selects the minimum element from the unsorted part of the array and swaps it with the first unsorted element.

---

### 3. **Insertion Sort**
   - **Best Case Complexity**: \(O(n)\) (when the array is already sorted)
   - **Average Case Complexity**: \(O(n^2)\)
   - **Worst Case Complexity**: \(O(n^2)\)
   - **Space Complexity**: \(O(1)\) (in-place sorting)
   - **Stable**: Yes
   - **Description**: Builds the sorted array one element at a time by inserting each element into its correct position in the already-sorted portion of the array.

---

### 4. **Merge Sort**
   - **Best Case Complexity**: \(O(n \log n)\)
   - **Average Case Complexity**: \(O(n \log n)\)
   - **Worst Case Complexity**: \(O(n \log n)\)
   - **Space Complexity**: \(O(n)\) (requires extra space for the auxiliary array)
   - **Stable**: Yes
   - **Description**: A divide-and-conquer algorithm that divides the array into halves, recursively sorts them, and then merges the sorted halves.

---

### 5. **QuickSort**
   - **Best Case Complexity**: \(O(n \log n)\)
   - **Average Case Complexity**: \(O(n \log n)\)
   - **Worst Case Complexity**: \(O(n^2)\) (when the pivot is poorly chosen, e.g., sorted input)
   - **Space Complexity**: \(O(\log n)\) (due to recursion stack)
   - **Stable**: No
   - **Description**: A divide-and-conquer algorithm that partitions the array into two halves around a pivot, recursively sorting each half.

---

### 6. **HeapSort**
   - **Best Case Complexity**: \(O(n \log n)\)
   - **Average Case Complexity**: \(O(n \log n)\)
   - **Worst Case Complexity**: \(O(n \log n)\)
   - **Space Complexity**: \(O(1)\) (in-place sorting)
   - **Stable**: No
   - **Description**: Builds a binary heap (either max-heap or min-heap), repeatedly extracts the maximum (or minimum), and reheapifies.

---

### 7. **Radix Sort**
   - **Best Case Complexity**: \(O(n \cdot k)\) where \(k\) is the number of digits
   - **Average Case Complexity**: \(O(n \cdot k)\)
   - **Worst Case Complexity**: \(O(n \cdot k)\)
   - **Space Complexity**: \(O(n + k)\)
   - **Stable**: Yes
   - **Description**: Non-comparative integer sorting algorithm that processes numbers digit by digit, starting from the least significant digit.

---

### 8. **Counting Sort**
   - **Best Case Complexity**: \(O(n + k)\)
   - **Average Case Complexity**: \(O(n + k)\)
   - **Worst Case Complexity**: \(O(n + k)\)
   - **Space Complexity**: \(O(k)\), where \(k\) is the range of input values
   - **Stable**: Yes
   - **Description**: Non-comparative sorting algorithm that counts the occurrences of each distinct element and uses this count to place elements in the correct position.

---

### 9. **Bucket Sort**
   - **Best Case Complexity**: \(O(n + k)\)
   - **Average Case Complexity**: \(O(n + k)\)
   - **Worst Case Complexity**: \(O(n^2)\) (if all elements fall into the same bucket)
   - **Space Complexity**: \(O(n + k)\)
   - **Stable**: Yes
   - **Description**: Divides the input into a number of buckets, sorts the individual buckets (using a different sorting algorithm), and then concatenates the results.

---

### 10. **Shell Sort**
   - **Best Case Complexity**: \(O(n \log n)\)
   - **Average Case Complexity**: \(O(n^{3/2})\) to \(O(n^{5/4})\) (depending on gap sequence)
   - **Worst Case Complexity**: \(O(n^2)\)
   - **Space Complexity**: \(O(1)\) (in-place sorting)
   - **Stable**: No
   - **Description**: An optimized version of insertion sort that allows the exchange of far apart elements by using a gap sequence to compare and sort elements at certain distances.

---

### 11. **Timsort**
   - **Best Case Complexity**: \(O(n)\)
   - **Average Case Complexity**: \(O(n \log n)\)
   - **Worst Case Complexity**: \(O(n \log n)\)
   - **Space Complexity**: \(O(n)\)
   - **Stable**: Yes
   - **Description**: A hybrid sorting algorithm derived from merge sort and insertion sort. Used in Python's built-in `sorted()` function and Java’s `Arrays.sort()` for objects.

---

### Summary Table

| **Algorithm**   | **Best Case**     | **Average Case**   | **Worst Case**    | **Space Complexity** | **Stable** |
|-----------------|-------------------|--------------------|-------------------|----------------------|------------|
| **Bubble Sort** | \(O(n)\)          | \(O(n^2)\)         | \(O(n^2)\)        | \(O(1)\)             | Yes        |
| **Selection Sort** | \(O(n^2)\)      | \(O(n^2)\)         | \(O(n^2)\)        | \(O(1)\)             | No         |
| **Insertion Sort** | \(O(n)\)        | \(O(n^2)\)         | \(O(n^2)\)        | \(O(1)\)             | Yes        |
| **Merge Sort**   | \(O(n \log n)\)   | \(O(n \log n)\)    | \(O(n \log n)\)   | \(O(n)\)             | Yes        |
| **QuickSort**    | \(O(n \log n)\)   | \(O(n \log n)\)    | \(O(n^2)\)        | \(O(\log n)\)        | No         |
| **HeapSort**     | \(O(n \log n)\)   | \(O(n \log n)\)    | \(O(n \log n)\)   | \(O(1)\)             | No         |
| **Radix Sort**   | \(O(n \cdot k)\)  | \(O(n \cdot k)\)   | \(O(n \cdot k)\)  | \(O(n + k)\)         | Yes        |
| **Counting Sort**| \(O(n + k)\)      | \(O(n + k)\)       | \(O(n + k)\)      | \(O(k)\)             | Yes        |
| **Bucket Sort**  | \(O(n + k)\)      | \(O(n + k)\)       | \(O(n^2)\)        | \(O(n + k)\)         | Yes        |
| **Shell Sort**   | \(O(n \log n)\)   | \(O(n^{3/2})\)     | \(O(n^2)\)        | \(O(1)\)             | No         |
| **Timsort**      | \(O(n)\)          | \(O(n \log n)\)    | \(O(n \log n)\)   | \(O(n)\)             | Yes        |

---

### Conclusion:
- **Comparison-based algorithms** (like QuickSort, MergeSort, and HeapSort) have a lower bound of \(O(n \log n)\).
- **Non-comparison-based algorithms** (like Radix Sort, Counting Sort, and Bucket Sort) can achieve linear time complexity \(O(n)\), but typically rely on additional constraints such as a bounded range of data or integer values.


## sort two vector at the same time
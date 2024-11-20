WIP
To see the size limits for arrays in C++, you can examine the following:

### 1. **Stack Size Limit**
   - The stack size varies depending on your operating system and compiler settings.
   - On Linux, you can check and change the stack size limit with these commands:
     ```bash
     ulimit -s        # Show the stack size limit (in KB)
     ulimit -s <size> # Set the stack size limit (e.g., ulimit -s 8192 for 8MB)
     ```
   - On Windows, you usually need to set the stack size during compilation or in the linker settings.

### 2. **Heap Size Limit**
   - Heap memory is typically limited by the total system memory, but allocating huge amounts (like several GBs) may still fail due to memory fragmentation.
   - In practice, your available heap size is the remaining system memory, minus what other processes are using. Tools like `top` on Linux or Task Manager on Windows can give an idea of available memory.

### 3. **Array Index Size Limits**
   - The maximum size of a single array is limited by the type `size_t`, which holds the maximum number of elements an array can have. On most 64-bit systems, `size_t` can support arrays up to around 4 billion elements (2^32 for 32-bit systems, 2^64 for 64-bit).
   - To get the maximum number of elements an array can hold:
     ```cpp
     #include <iostream>
     #include <limits>

     int main() {
         std::cout << "Max size_t: " << std::numeric_limits<size_t>::max() << std::endl;
         return 0;
     }
     ```

### 4. **Practical Example for Large Arrays with `std::vector`**
   - For dynamically-sized arrays, use `std::vector` as it’s managed on the heap and helps avoid stack size issues. You can also check the maximum size it can hold:
     ```cpp
     #include <iostream>
     #include <vector>

     int main() {
         std::vector<int> vec;
         std::cout << "Max vector size: " << vec.max_size() << std::endl;
         return 0;
     }
     ```

If you’re working on a system with limited memory, understanding these thresholds can help prevent memory allocation errors. Let me know if you'd like further examples!
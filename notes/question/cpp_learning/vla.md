To check if your compiler supports **Variable Length Arrays (VLA)** and how to disable them, follow these steps based on your compiler:

### 1. **Check for VLA support in GCC/Clang:**

In **GCC** and **Clang**, VLAs are supported as an extension even though they are not part of standard C++. Here's how you can check and disable VLA:

#### Check if VLA is supported:

Create a simple test program like this:

```cpp
#include <iostream>

int main() {
    int size = 5;
    int arr[size];  // This is a VLA
    std::cout << "VLA created with size: " << size << std::endl;
    return 0;
}
```

Compile it without any special flags:

```bash
g++ -std=c++11 -o test_vla test_vla.cpp
```

If the code compiles, your compiler supports VLAs as an extension.

#### Disable VLA in GCC/Clang:

To **disable VLAs** in **GCC** or **Clang**, use the `-Werror=vla` flag. This will cause the compiler to treat VLAs as an error. Example:

```bash
g++ -std=c++11 -Werror=vla -o test_vla test_vla.cpp
```

If your code tries to use a VLA, it will generate an error like:

```
error: variable-length array type ‘int[size]’ is used [-Werror=vla]
```

### 2. **Check for VLA support in MSVC (Microsoft Visual C++):**

**MSVC** does not support VLAs at all, as VLAs are a GCC/Clang-specific extension. So, if you're using MSVC, VLAs will result in a compilation error by default.

### 3. **Other compilers:**

For other compilers, consult their specific documentation, but in general, VLAs are not part of the standard C++ language. If a compiler supports it, it likely follows similar patterns as GCC or Clang.

### Conclusion:
- **GCC/Clang**: Use `-Werror=vla` to disable VLAs.
- **MSVC**: VLAs are not supported, so no special action is needed.
- To write portable C++ code, avoid using VLAs, and use `std::vector` if you need a dynamically sized array.









In C++, the rules for array dimensions vary depending on the version of the standard you're using.

### Key Points from C++ Primer:
- The **dimension of an array must be a constant expression**. This means that the size of the array must be known at compile time for the array to be valid in C++.

### Understanding Your Code:
Let's break down your code based on the different types of variables you're using for the array sizes:

1. **`constexpr int a = 20;`**:
   - `a` is a constant expression because `constexpr` guarantees that it is evaluated at compile time.
   - `int arra[a];` is valid because `a` is a constant expression.

2. **`const int b = 30;`**:
   - `b` is a constant, but it's a **runtime constant** in the traditional C++ standard before C++11.
   - In **C++11 and later**, a `const` integer initialized with a literal can be treated as a constant expression if its value is known at compile time. Therefore, `int arrb[b];` may also compile, depending on the compiler.

3. **`int c = 40;`**:
   - `c` is a regular `int` variable, and its value isn't a constant expression because it can change at runtime.
   - `int arrc[c];` is not valid in **standard C++** (pre-C++11), but it might compile if you're using a compiler that supports **Variable Length Arrays (VLA)** as an extension. VLAs are not part of the standard C++, but some compilers (like GCC) allow this as an extension.

### Why Your Code Compiles:
- If you're using a **GNU Compiler (GCC)** or another compiler that supports VLAs, `int arrc[c];` will compile. However, VLAs are not part of the C++ standard, so this behavior is compiler-specific and **non-portable**.
- `int arra[a];` and `int arrb[b];` will compile under **standard C++** (post-C++11) because `a` is a `constexpr`, and `b` can be treated as a constant expression.

### Conclusion:
- If your code compiles successfully, it's likely due to **compiler-specific extensions** (for `arrc`) or C++11+ rules for `constexpr` and `const`.
- If you want fully standard-compliant C++ code, avoid using regular variables like `int c = 40;` for array sizes, as it is not guaranteed to work in all compilers.


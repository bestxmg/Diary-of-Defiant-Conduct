To see the actual range of the `short` type on your machine in C++, you can use the `<limits>` header, which provides the `std::numeric_limits` template. This allows you to query the minimum and maximum values for various fundamental types, including `short`. Here's a simple example:

```cpp
#include <iostream>
#include <limits>

int main() {
    std::cout << "Range of short:" << std::endl;
    std::cout << "Minimum: " << std::numeric_limits<short>::min() << std::endl;
    std::cout << "Maximum: " << std::numeric_limits<short>::max() << std::endl;
    return 0;
}
```

### Explanation:
1. **Include `<limits>`**: This header defines the `std::numeric_limits` template.
2. **Use `std::numeric_limits<short>`**: This provides type-specific information about `short`.
3. **Access `min()` and `max()`**: These member functions return the minimum and maximum values that a `short` can hold.

### Compile and Run
Compile and run this program, and it will display the actual range of the `short` type on your machine. 

### Expected Output
Typically, on most platforms, you will see something like:
```
Range of short:
Minimum: -32768
Maximum: 32767
```

### Note
Keep in mind that the range of `short` can vary depending on the compiler and platform, but the standard size is typically 16 bits, leading to the aforementioned range.


WIP
## Why modern C++ program should avoid using NULL and use nullptr instead🐶
Modern C++ programs should avoid using `NULL` in favor of `nullptr` for several reasons:

1. **Type Safety**: `nullptr` is a type-safe null pointer constant. It has its own type (`std::nullptr_t`), which helps avoid ambiguous conversions that can occur with `NULL`, which is often defined as `0` or `((void*)0)`.

2. **Overloaded Functions**: Using `nullptr` helps resolve ambiguities in overloaded functions. For example, if you have overloaded functions that take either integer or pointer parameters, passing `NULL` could lead to confusion, whereas `nullptr` clearly indicates a pointer.

3. **Consistency**: `nullptr` improves code readability and consistency, as it explicitly indicates that it’s a null pointer, enhancing clarity for anyone reading the code.

4. **Future-Proofing**: As C++ evolves, using `nullptr` aligns with modern best practices and standards, ensuring your code is more robust and maintainable.

### Example:

```cpp
void func(int);
void func(char*);

func(NULL);     // Ambiguous: could call either function
func(nullptr);  // Clear: calls func(char*)
```

Using `nullptr` is considered a best practice in modern C++.
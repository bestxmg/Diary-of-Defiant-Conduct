WIP
**Direct initialization** is a syntax in C++ used to initialize an object or a variable. It involves passing values directly to the constructor or using braces (for certain types), rather than assigning values afterward. It is called "direct" because the initialization occurs at the moment of object creation, often invoking a constructor.

### Syntax Forms of Direct Initialization

1. **Using Parentheses (`()`)**
   - For non-aggregate types (e.g., classes, structs with constructors), parentheses are used to pass arguments to the constructor.

   ```cpp
   int x(5); // Directly initialize an int with value 5
   std::string str("Hello"); // Calls std::string's constructor with "Hello"
   MyClass obj(10, "example"); // Calls MyClass's constructor
   ```

2. **Using Braces (`{}`)** (Uniform Initialization)
   - Introduced in C++11, brace initialization is used to initialize objects, aggregates, and even classes. It has some advantages over parentheses, such as preventing **narrowing conversions**.

   ```cpp
   int x{5}; // Directly initialize an int with value 5
   std::string str{"Hello"}; // Calls std::string's constructor
   MyClass obj{10, "example"}; // Calls MyClass's constructor
   ```

   Braces are preferred for modern C++ because they work consistently for most types and avoid ambiguity in some cases.

3. **Direct Initialization with Temporary Objects**
   - When creating temporary objects for immediate use.

   ```cpp
   MyClass(10, "example"); // Temporary object directly initialized
   ```

---

### Direct Initialization vs. Copy Initialization

**Copy Initialization (`=`)** is different from direct initialization because it involves assigning a value after the object is created, and it may invoke copy constructors or assignments.

For example:

```cpp
int x = 5; // Copy initialization
int y(5);  // Direct initialization
```

Key differences:
- **Direct initialization**: Preferable when you want to explicitly call a specific constructor.
- **Copy initialization**: May involve implicit conversions if the types are different.

---

### Why Use Direct Initialization?

1. **Precision**: Direct initialization allows you to specify exactly which constructor to call.
2. **Performance**: Avoids creating temporary objects that might happen with copy initialization.
3. **Modern Syntax**: Brace initialization (`{}`) helps prevent unintended conversions, making the code safer and clearer.

### Example Comparison

```cpp
#include <iostream>
#include <string>

class MyClass {
public:
    MyClass(int a, const std::string& b) {
        std::cout << "Constructor called with: " << a << ", " << b << std::endl;
    }
};

int main() {
    MyClass obj1(42, "direct init");   // Direct initialization
    MyClass obj2 = MyClass(42, "temp"); // Copy initialization
    return 0;
}
```

Output:
```
Constructor called with: 42, direct init
Constructor called with: 42, temp
```
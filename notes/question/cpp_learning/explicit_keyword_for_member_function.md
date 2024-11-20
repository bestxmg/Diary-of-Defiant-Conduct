The message **"Class 'Sales_data' has a constructor with 1 argument that is not explicit"** refers to the fact that one of the constructors in your `Sales_data` class allows **implicit conversions**, which might lead to unexpected behavior.

---

### **Key Context**
In your class, this constructor is the one being referred to:

```cpp
Sales_data(const std::string &s) : bookNo(s) {}
```

#### **Why This Happens**
- This constructor has **a single parameter** (`const std::string &s`).
- In C++, a constructor with one parameter can act as a **conversion constructor**, meaning it can automatically convert an argument of the parameter's type (`std::string`) into an instance of the class (`Sales_data`).

Unless marked as `explicit`, this conversion can happen **implicitly** wherever the compiler thinks it’s appropriate, sometimes in ways you don't intend.

---

### **Examples of Implicit Conversion**
Given the constructor:
```cpp
Sales_data(const std::string &s) : bookNo(s) {}
```

#### Example 1: Intended Behavior
```cpp
Sales_data item("12345"); // Calls Sales_data(const std::string &s)
```

This is fine because you clearly want to construct a `Sales_data` object using a `std::string`.

#### Example 2: Implicit Conversion
```cpp
void process(Sales_data data);

process("12345"); // Implicitly converts "12345" (const char*) to std::string, then to Sales_data
```

Here, `"12345"` (a `const char*`) is implicitly converted to `std::string`, and then the `Sales_data(const std::string &s)` constructor is called. This conversion happens automatically, which might be unexpected or unwanted in some contexts.

#### Example 3: Overload Confusion
```cpp
Sales_data data = "12345"; // Implicitly converts to Sales_data
```

This kind of implicit conversion can lead to ambiguous or surprising code.

---

### **Solution: Use `explicit` to Prevent Implicit Conversions**
To avoid these implicit conversions, you can mark the constructor with the `explicit` keyword:

```cpp
explicit Sales_data(const std::string &s) : bookNo(s) {}
```

#### **Effect of `explicit`**
- After marking the constructor `explicit`, it will no longer participate in implicit conversions.
- The following example would now cause a **compilation error**:
  ```cpp
  process("12345"); // Error: cannot convert const char* to Sales_data
  ```

- However, explicit object creation is still allowed:
  ```cpp
  Sales_data data("12345"); // OK: Direct initialization
  ```

---

### **When to Use `explicit`**
- Use `explicit` for constructors with **one parameter** when:
  - Implicit conversions could lead to ambiguity or unintended behavior.
  - The constructor is primarily for direct initialization, not conversion.

For your class:
```cpp
class Sales_data {
    // Other members remain unchanged
public:
    explicit Sales_data(const std::string &s) : bookNo(s) {}
    Sales_data(const std::string &s, unsigned n, double r) : bookNo(s), units_sold(n), revenue(r) {}
    Sales_data() : bookNo(""), units_sold(0), revenue(0.0) {}
    Sales_data(std::istream &i) { read(i, *this); }
};
```

---

### **Advantages of Marking `explicit`**
1. **Prevents Ambiguity**: No accidental conversions in overloaded functions or assignments.
2. **Improves Readability**: Makes the intent of constructors clear (direct initialization only).
3. **Avoids Bugs**: Reduces the risk of unintended behavior caused by implicit conversions.

Would you like an example showing where implicit conversions might cause subtle bugs?
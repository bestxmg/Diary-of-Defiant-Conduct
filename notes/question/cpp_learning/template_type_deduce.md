When deducing the template parameter type in C++, the behavior depends on whether the argument is an **lvalue** or an **rvalue** and how the parameter is specified (by value, by reference, or by rvalue reference). Here’s a detailed breakdown of how **type deduction** works in C++:

### **Template Type Deduction Rules**
C++ uses **reference collapsing** and the nature of the argument (lvalue or rvalue) to deduce the type of the template parameter. Below are the general rules:

#### **1. Template with By-Value Parameter (`T t`)**
- **Type Deduction**:  
  When a parameter is passed by value (e.g., `T t`), the type is **deduced as the type of the argument**, ignoring any references or rvalue references.

  - If an **lvalue** is passed, `T` is deduced as the base type (no reference).
  - If an **rvalue** is passed, `T` is deduced as the base type (again, no reference).
  
- **Examples**:
  ```cpp
  template <typename T>
  void f(T t);  // By value
  ```

  **Calling `f` with different argument types**:
  - `int x = 42; f(x);`  → `T` is deduced as `int`, `t` is of type `int`.
  - `f(42);`  → `T` is deduced as `int`, `t` is of type `int`.

  **Note**: No references are involved in the deduction here.

#### **2. Template with Lvalue Reference Parameter (`T& t`)**
- **Type Deduction**:  
  When the parameter is an lvalue reference (`T&`), the type is **deduced as the type of the argument without adding a reference**.
  
  - If an **lvalue** is passed, `T` is deduced as the type of the lvalue.
  - If an **rvalue** is passed, `T` is deduced as the base type **without reference**. The reference is discarded.

- **Examples**:
  ```cpp
  template <typename T>
  void g(T& t);  // Lvalue reference
  ```

  **Calling `g` with different argument types**:
  - `int x = 42; g(x);`  → `T` is deduced as `int`, `t` is of type `int&`.
  - `f(42);`  → `T` is deduced as `int`, `t` is of type `int&` (since 42 is an rvalue, but `T&` cannot bind to an rvalue, so `T` is deduced as `int`, and `t` is an lvalue reference).

#### **3. Template with Rvalue Reference Parameter (`T&& t`)**
- **Type Deduction**:  
  When the parameter is an rvalue reference (`T&&`), **type deduction works differently based on whether the argument is an lvalue or an rvalue**. This is key for enabling **perfect forwarding**.

  - If an **lvalue** is passed, `T&&` collapses to `T&` (via reference collapsing).
  - If an **rvalue** is passed, `T&&` stays as `T&&` (it remains an rvalue reference).
  
  **Reference collapsing rules** apply here:
  - `T& & → T&`
  - `T& && → T&`
  - `T&& & → T&`
  - `T&& && → T&&`

- **Examples**:
  ```cpp
  template <typename T>
  void h(T&& t);  // Rvalue reference
  ```

  **Calling `h` with different argument types**:
  - `int x = 42; h(x);`  → `T` is deduced as `int`, and `t` is of type `int&` (lvalue).
  - `h(42);`  → `T` is deduced as `int`, and `t` is of type `int&&` (rvalue).

---

### **Full Deduction Table**

| **Argument Type**          | **Template Parameter**         | **Deduced `T`**          | **Type of `t`**        |
|----------------------------|---------------------------------|--------------------------|------------------------|
| `lvalue` (e.g., `int x`)    | `T t`                           | `T = int`                | `t` is of type `int` (by value) |
| `lvalue` (e.g., `int x`)    | `T& t`                          | `T = int`                | `t` is of type `int&`  |
| `rvalue` (e.g., `42`)       | `T t`                           | `T = int`                | `t` is of type `int` (by value) |
| `rvalue` (e.g., `42`)       | `T& t`                          | `T = int`                | `t` is of type `int&`  |
| `lvalue` (e.g., `int x`)    | `T&& t`                         | `T = int`                | `t` is of type `int&`  |
| `rvalue` (e.g., `42`)       | `T&& t`                         | `T = int`                | `t` is of type `int&&` |
| `lvalue` (e.g., `int x`)    | `T& & t`                        | `T = int`                | `t` is of type `int&`  |
| `rvalue` (e.g., `42`)       | `T& & t`                        | `T = int`                | `t` is of type `int&`  |
| `lvalue` (e.g., `int x`)    | `T& && t`                       | `T = int`                | `t` is of type `int&`  |
| `rvalue` (e.g., `42`)       | `T& && t`                       | `T = int`                | `t` is of type `int&`  |
| `lvalue` (e.g., `int x`)    | `T&& & t`                       | `T = int`                | `t` is of type `int&`  |
| `rvalue` (e.g., `42`)       | `T&& & t`                       | `T = int`                | `t` is of type `int&`  |
| `lvalue` (e.g., `int x`)    | `T&& && t`                      | `T = int`                | `t` is of type `int&&` |
| `rvalue` (e.g., `42`)       | `T&& && t`                      | `T = int`                | `t` is of type `int&&` |

### **Important Rules**
1. **When passing by value (`T t`)**:
   - `T` is deduced based on the type of the argument, and no reference or rvalue reference is involved.
2. **When passing by lvalue reference (`T& t`)**:
   - `T` is deduced based on the base type of the argument.
3. **When passing by rvalue reference (`T&& t`)**:
   - If an **lvalue** is passed, `T&&` collapses to `T&`.
   - If an **rvalue** is passed, `T&&` stays as `T&&`.

---

### **Examples of Perfect Forwarding**
```cpp
template <typename T>
void wrapper(T&& arg) {
    f(std::forward<T>(arg));  // Perfect forwarding using std::forward
}
```
In this case, `std::forward` is used to **forward the argument** exactly as it was passed to the wrapper, preserving whether it was an lvalue or rvalue.

- If an **lvalue** is passed, `std::forward<T>(arg)` will cast `arg` back to `T&`.
- If an **rvalue** is passed, `std::forward<T>(arg)` will cast `arg` to `T&&`.

This is a key concept when using **universal references** in templates for **perfect forwarding**.

---

Let me know if you need further clarification!


WIP
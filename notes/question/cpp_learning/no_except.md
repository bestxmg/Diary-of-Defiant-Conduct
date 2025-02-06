WIP
When a member function is declared as `noexcept`, it signifies that the function is guaranteed not to throw any exceptions. This provides several benefits in terms of optimization, exception safety, and code clarity. Let’s explore what it means and how it works in C++.

### 1. **Syntax:**

A member function can be declared `noexcept` in one of two ways:
- **Directly in the declaration**:
  ```cpp
  void myFunction() noexcept;
  ```
- **Inline with the definition**:
  ```cpp
  void myFunction() noexcept {
      // function body
  }
  ```

### 2. **What Does `noexcept` Mean?**

When you declare a function `noexcept`, you're telling the compiler that this function will **not throw exceptions**. This allows the compiler to make certain optimizations and helps ensure that the code behaves as expected, particularly in exception-safe contexts.

### 3. **Key Aspects of `noexcept`:**

- **Optimization**: The compiler can make optimizations because it knows the function will not throw an exception. For example, it may skip certain exception-handling code or even optimize exception handling out of the generated code entirely.
- **Exception Safety**: By marking a function `noexcept`, you are guaranteeing that the function will not propagate exceptions, which simplifies error handling in higher layers of the code.
- **Conditional `noexcept`**: A function can be conditionally `noexcept`, based on the function’s argument types or other aspects of the code.

  ```cpp
  template <typename T>
  void foo(T&& arg) noexcept(noexcept(std::declval<T&>().bar())) {
      // Function body
  }
  ```

  In the above example, `foo` is marked as `noexcept` only if the expression `std::declval<T&>().bar()` is `noexcept`. This means that `foo` will be `noexcept` if the member function `bar()` of type `T` is `noexcept`.

- **The `noexcept` operator**: You can use `noexcept` as a condition to check whether a function can throw or not:
  
  ```cpp
  bool can_throw() noexcept(false) {
      return true;  // This function can throw, so it's not noexcept
  }

  bool cannot_throw() noexcept {
      return true;  // This function cannot throw
  }
  ```

  The `noexcept` operator can also be used to query whether a particular expression or function is `noexcept`:
  
  ```cpp
  static_assert(noexcept(func()), "func() must be noexcept");
  ```

### 4. **Effects of `noexcept` on Member Functions:**

#### 4.1. **Inheritance and `noexcept`:**

When a class inherits a function that is `noexcept`, the derived class must also ensure that the function remains `noexcept`, unless it overrides the function and explicitly marks it as `noexcept` or non-`noexcept`.

```cpp
class Base {
public:
    void myFunction() noexcept {
        // No exceptions allowed here
    }
};

class Derived : public Base {
public:
    void myFunction() noexcept override { // Marking as noexcept here
        // No exceptions allowed here either
    }
};
```

In the example above, `Derived::myFunction()` is `noexcept` because it overrides `Base::myFunction()`, which is `noexcept`. If you remove the `noexcept` specifier from `Derived::myFunction()`, the compiler will produce an error because it would contradict the `noexcept` promise of the base class.

#### 4.2. **`noexcept` and Overloading:**

When you overload a function, the `noexcept` specification can affect which version of the function is called. The compiler prefers the `noexcept` version over a non-`noexcept` version, if the context permits.

```cpp
class MyClass {
public:
    void myFunction() noexcept {
        std::cout << "noexcept version\n";
    }

    void myFunction() {
        std::cout << "non-noexcept version\n";
    }
};

int main() {
    MyClass obj;
    obj.myFunction();  // Calls the noexcept version if no exception is thrown
}
```

#### 4.3. **Exception Handling in `noexcept` Functions:**

If you attempt to throw an exception from a function marked as `noexcept`, it results in undefined behavior (UB). This is because a `noexcept` function promises not to throw exceptions, and throwing an exception from such a function violates that promise.

```cpp
void foo() noexcept {
    throw std::runtime_error("Error");  // This will lead to undefined behavior
}
```

#### 4.4. **`noexcept` and `std::vector`, `std::map`, etc.:**

Some standard library containers and algorithms are more efficient when dealing with `noexcept` functions. For example:
- `std::vector` and other containers can potentially optimize operations like **moving** elements instead of copying them if the move constructor or move assignment operator is `noexcept`.
  
  ```cpp
  class MyClass {
  public:
      MyClass() = default;
      MyClass(MyClass&&) noexcept { /* move constructor */ }
  };
  ```

  By declaring your move constructor `noexcept`, you enable the container to use move semantics optimally, which can improve performance by avoiding unnecessary copies.

#### 4.5. **Move Semantics and `noexcept`:**

The `noexcept` keyword plays a crucial role in move semantics. When moving objects, the compiler will prefer `noexcept`-marked move constructors and move assignment operators over non-`noexcept` ones.

```cpp
class MyClass {
public:
    MyClass(MyClass&&) noexcept;  // `noexcept` move constructor

    MyClass& operator=(MyClass&&) noexcept;  // `noexcept` move assignment operator
};
```

If `noexcept` is specified, it can enable optimizations like avoiding extra allocations or copying.

### 5. **Conclusion:**

- **`noexcept`** is a keyword that tells the compiler and users of your code that a function will not throw any exceptions.
- It allows the compiler to perform optimizations and guarantees exception safety.
- **Move semantics** are enhanced by marking move constructors and move assignment operators `noexcept`.
- A function that is marked `noexcept` cannot throw exceptions, and attempting to do so leads to undefined behavior.
- When inheriting or overloading, `noexcept` has specific rules to ensure consistency.
  
The `noexcept` specifier is a powerful tool in modern C++, especially when working with performance-critical code. By making clear promises about exception behavior, it can help compilers generate more efficient code and make your program safer by ensuring functions adhere to the specified behavior.
## enum🐶

### what's scoped enumeration and unscoped enumeration.
#### **example of unscoped** 
    ```cpp
    #include <iostream>

    enum Color {
        Red,
        Green,
        Blue
    };

    int main() {
        Color myColor = Red; // No need to use Color::Red
        std::cout << "My color is: " << myColor << std::endl; // Outputs: My color is: 0
        return 0;
    }
    ```

#### **example of scoped**  
    ```cpp
    #include <iostream>

    enum class Color {
        Red,
        Green,
        Blue
    };

    int main() {
        Color myColor = Color::Red; // Need to use Color::Red
        // std::cout << "My color is: " << myColor << std::endl; // This line would cause a compile error

        // If you want to output the value:
        std::cout << "My color is: " << static_cast<int>(myColor) << std::endl; // Outputs: My color is: 0
        return 0;
    }
    ```

#### **Key Differences**

1. **Scope:**
- Unscoped: Enumerators are available in the enclosing scope.
- Scoped: Enumerators are only accessible with the enumeration type name.

2. **Type Safety:**
- Unscoped: More prone to name clashes.
- Scoped: Provides better type safety, avoiding conflicts and errors.

3. **Implicit Conversion:**
- Unscoped: Implicitly convertible to `int`.
- Scoped: No implicit conversion, requiring explicit casting.
### Why unscoped enumeration can function as operand of %, while this not apply to scoped enumeration.
**Implicit Conversion:**
- Unscoped: Implicitly convertible to `int`.
- Scoped: No implicit conversion, requiring explicit casting.
### How Enumerators storages. Including scoped and unscoped(WIP)
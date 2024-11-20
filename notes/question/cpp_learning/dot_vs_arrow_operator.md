## What's the difference between using and typedef in C++🐶(WIP)


In C++, the **`->` (arrow operator)** is used to access members (methods or variables) of an object or structure through a **pointer**.

### How It Works:
- The **dot operator (`.`)** is used when you have a **direct object** or **reference**.
- The **arrow operator (`->`)** is used when you have a **pointer** to an object or structure. It dereferences the pointer and then accesses the member.

### Syntax:
```cpp
pointer->member
```
This is effectively equivalent to:
```cpp
(*pointer).member
```
The arrow operator is a shorthand for dereferencing a pointer and accessing its members.

### Example:
```cpp
#include <iostream>

struct Person {
    std::string name;
    int age;
    
    void greet() {
        std::cout << "Hello, my name is " << name << " and I'm " << age << " years old." << std::endl;
    }
};

int main() {
    Person p = {"Alice", 30};
    Person* ptr = &p;  // ptr is a pointer to the object 'p'

    // Accessing members using the arrow operator
    std::cout << ptr->name << std::endl;  // Outputs: Alice
    ptr->greet();  // Calls the greet method on the object 'p'

    return 0;
}
```

In this example:
- `ptr->name` accesses the `name` member of the `Person` object through the pointer `ptr`.
- `ptr->greet()` calls the `greet` method of the `Person` object through the pointer `ptr`.

The **`->` operator** is very useful when working with pointers to structures or objects.
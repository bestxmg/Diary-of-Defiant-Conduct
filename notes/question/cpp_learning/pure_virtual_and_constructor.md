WIP

Not exactly. A **pure virtual function** can still be **used** in the base class, but with some restrictions:  

### **1. A pure virtual function can have an implementation in the base class**  
Even though a function is marked as **pure virtual (`= 0`)**, you can still provide a definition for it inside the base class.  

#### **Example: A pure virtual function with an implementation**  
```cpp
#include <iostream>

class Base {
public:
    virtual void func() = 0;  // Pure virtual function

    void callFunc() {
        std::cout << "Calling func() from Base:\n";
        func();  // This is allowed if the derived class overrides it
    }
};

class Derived : public Base {
public:
    void func() override {
        std::cout << "Derived implementation of func()\n";
    }
};

int main() {
    Derived d;
    d.callFunc();  // Works fine
}
```
🔹 **Why does this work?**  
- `Base::callFunc()` calls `func()`, but since `Derived` overrides it, the **Derived version gets executed**.  
- The function is **pure virtual**, but it is still **callable from a base class method** if a derived class provides an override.  

---

### **2. A pure virtual function can have a base class implementation**
Even though a function is marked as `= 0`, it **can still have an implementation** inside the base class:  

#### **Example: A pure virtual function with an implementation in the base class**
```cpp
#include <iostream>

class Base {
public:
    virtual void func() = 0;  // Pure virtual function

    void defaultImplementation() {
        std::cout << "Base class default implementation\n";
    }
};

// Provide an implementation for the pure virtual function
void Base::func() {
    std::cout << "Base::func() implementation\n";
}

class Derived : public Base {
public:
    void func() override {
        std::cout << "Derived::func() implementation\n";
    }
};

int main() {
    Derived d;
    d.func();  // Calls Derived::func()
    
    Base* basePtr = &d;
    basePtr->Base::func();  // Calls Base::func() implementation
}
```
🔹 **Why does this work?**  
- `func()` is still **pure virtual**, meaning `Base` cannot be instantiated.  
- However, `Base::func()` has an implementation, so a derived class **can** explicitly call it using `Base::func()`.  

---

### **3. A pure virtual function cannot be called in the base class constructor**
As mentioned before, **you should not call a pure virtual function in a base class constructor** because the derived class is **not yet fully constructed**, and its override won’t be available.

#### **Bad Example: Calling a pure virtual function in the constructor**
```cpp
#include <iostream>

class Base {
public:
    Base() {
        func();  // BAD: Undefined behavior!
    }
    virtual void func() = 0;
};

class Derived : public Base {
public:
    void func() override {
        std::cout << "Derived::func() called\n";
    }
};

int main() {
    Derived d;  // Undefined behavior!
}
```
🚨 **Why is this bad?**  
- When `Base`’s constructor runs, `Derived` **has not been constructed yet**, so `Derived::func()` **does not exist at this point**.  
- This leads to **undefined behavior** if the function is pure virtual with no base class implementation.  

---

### **Conclusion**
✅ **A pure virtual function can be called inside the base class, but only indirectly** (e.g., via another method like `callFunc()`).  
✅ **A pure virtual function can have an implementation in the base class** (but the base class is still abstract).  
❌ **A pure virtual function should not be called in the base class constructor** because the derived class override isn't available yet.  

Would you like to test this behavior with more examples? 😊
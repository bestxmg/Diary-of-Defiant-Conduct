## A reference to const can be initialized with a literal🐶

### Const reference VS non-const reference
```cpp
int main(){
    const int &r2 = 42; // ok
    int &r3 = 42; // error: initial value of reference to non-const must be an lvalue
    return 0;
}
```
From the code above, we can see that ```A reference to const can be initialized with a literal```, but it doesn't work on non-const reference.

Because reference to const guarantees that the value will not be modified. This allows the compiler to create a temporary object that holds the value.

- [memory allocation in C++](./memory_allocation.md#1-how-c-allocate-memory-for-different-kind-of-objectswip)
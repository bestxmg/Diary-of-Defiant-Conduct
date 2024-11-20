To run `f()` and `g()` simultaneously in C++, you can use *threads*. The C++ Standard Library provides the `<thread>` library, which allows you to execute functions concurrently.

Here's an example of how you could use `std::thread` to run both `f()` and `g()` simultaneously:

```cpp
#include <iostream>
#include <thread>
#include <future>  // for std::async

// Example functions
int f() {
    // Simulate work in f
    std::this_thread::sleep_for(std::chrono::seconds(1));
    return 10;
}

int g() {
    // Simulate work in g
    std::this_thread::sleep_for(std::chrono::seconds(1));
    return 5;
}

int main() {
    // Run f() and g() in separate threads and get their results
    std::future<int> resultF = std::async(std::launch::async, f);
    std::future<int> resultG = std::async(std::launch::async, g);

    // Retrieve results and compare
    if (resultF.get() > resultG.get()) {
        std::cout << "f() > g()" << std::endl;
    } else {
        std::cout << "f() <= g()" << std::endl;
    }

    return 0;
}
```

### Explanation:
- `std::async(std::launch::async, f)` and `std::async(std::launch::async, g)` each run `f()` and `g()` in separate threads.
- The `.get()` calls will wait for each function to finish executing and retrieve their results.
- This way, both functions execute concurrently, and you can still use the results in the `if` condition.



WIP
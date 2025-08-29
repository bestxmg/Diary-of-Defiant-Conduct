Thread Safety
To manually release a lock in C++, you can use `std::unique_lock<std::mutex>`, which provides more flexibility than `std::lock_guard<std::mutex>`. Unlike `std::lock_guard`, `std::unique_lock` allows you to explicitly unlock the mutex before the lock object goes out of scope.

---

### **How to Manually Unlock a Mutex**
Use `std::unique_lock` instead of `std::lock_guard` and call `.unlock()` when needed.

```cpp
#include <iostream>
#include <mutex>
#include <thread>

std::mutex mtx;

void task(int id) {
    std::unique_lock<std::mutex> lock(mtx);
    std::cout << "Thread " << id << " acquired the lock\n";

    // Manually release the lock before the scope ends
    lock.unlock();
    
    std::cout << "Thread " << id << " released the lock\n";

    // Some operations that do not require the lock...
}

int main() {
    std::thread t1(task, 1);
    std::thread t2(task, 2);

    t1.join();
    t2.join();

    return 0;
}
```

---

### **Key Differences Between `std::lock_guard` and `std::unique_lock`**
| Feature              | `std::lock_guard` | `std::unique_lock` |
|----------------------|------------------|------------------|
| Locking behavior    | Locks on construction, unlocks on destruction | Locks on construction, but can be manually unlocked |
| Manual unlocking    | ❌ Not possible | ✅ `.unlock()` available |
| Movable?            | ❌ No | ✅ Yes (can transfer ownership) |
| Deferred locking    | ❌ No | ✅ `.lock()` can be called later |

---

### **When to Use Which?**
- Use `std::lock_guard` when you **always** want the lock for the entire scope.
- Use `std::unique_lock` when you **might** need to unlock early or defer locking.

🚀 **Use `std::lock_guard` for most cases (simpler & safer), but `std::unique_lock` when manual unlocking is needed!**


#include <iostream>
#include <mutex>
#include <thread>

std::mutex mtx;

void print_thread_id(int id) {
    std::unique_lock<std::mutex> lock(mtx);  // Lock the mutex
    std::cout << "Thread " << id << " is running\n";  // Critical section

    // Manually unlock the mutex before going out of scope
    lock.unlock();
    std::cout << "Thread " << id << " has unlocked the mutex\n";

    // Some code that doesn't need the mutex
}

int main() {
    std::thread t1(print_thread_id, 1);
    std::thread t2(print_thread_id, 2);

    t1.join();
    t2.join();

    return 0;
}


#include <iostream>
#include <mutex>
#include <thread>

std::mutex mtx;

void print_thread_id(int id) {
    std::lock_guard<std::mutex> lock(mtx);  // Lock the mutex automatically
    std::cout << "Thread " << id << " is running\n";  // Critical section
}

int main() {
    std::thread t1(print_thread_id, 1);
    std::thread t2(print_thread_id, 2);

    t1.join();
    t2.join();

    return 0;
}

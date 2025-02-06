## Naming convention🐶
Here's a detailed overview of naming conventions for various objects in C++ with examples for each category:

### 1. **Variables**
   - **Convention**: Lower Camel Case is commonly used, though some may use snake case.
   - **Example**:
     ```cpp
     int maxSpeed = 120;
     float temperatureValue = 36.5;
     string userName = "JohnDoe";
     ```

### 2. **Constants**
   - **Convention**: All uppercase with underscores (`SNAKE_CASE`). 
   - **Example**:
     ```cpp
     const int MAX_BUFFER_SIZE = 1024;
     const float PI = 3.14159;
     ```

### 3. **Functions**
   - **Convention**: Lower Camel Case.
   - **Example**:
     ```cpp
     void calculateSum(int a, int b) {
         int sum = a + b;
         cout << "Sum: " << sum << endl;
     }

     double getAverageScore(int total, int count) {
         return static_cast<double>(total) / count;
     }
     ```

### 4. **Classes and Structs**
   - **Convention**: Upper Camel Case (Pascal Case).
   - **Example**:
     ```cpp
     class AccountManager {
     public:
         void createAccount();
     };

     struct EmployeeData {
         string name;
         int id;
     };
     ```

### 5. **Member Variables**
   - **Convention**: Lower Camel Case with prefixes like `m_` or a trailing underscore `_` to distinguish them.
   - **Example**:
     ```cpp
     class Car {
     private:
         double m_speed;    // Prefix style
         string model_;     // Suffix style
     public:
         void setSpeed(double speed) {
             m_speed = speed;
         }
     };
     ```

### 6. **Global Variables**
   - **Convention**: Often prefixed with `g_` to indicate global scope.
   - **Example**:
     ```cpp
     int g_maxUsers = 100;
     double g_taxRate = 0.07;
     ```

### 7. **Enums**
   - **Convention**: Upper Camel Case for enum names and all caps or Upper Camel Case for enum values.
   - **Example**:
     ```cpp
     enum Color {
         RED,
         GREEN,
         BLUE
     };

     enum LogLevel {
         Info,
         Warning,
         Error
     };
     ```

### 8. **Namespaces**
   - **Convention**: Usually all lowercase or snake case.
   - **Example**:
     ```cpp
     namespace my_app {
         void run() {
             cout << "Running my application" << endl;
         }
     }

     namespace utils {
         void logMessage(const string& message) {
             cout << "Log: " << message << endl;
         }
     }
     ```

### 9. **Macros**
   - **Convention**: All caps with underscores.
   - **Example**:
     ```cpp
     #define MAX_CONNECTIONS 10
     #define DEBUG_MODE
     ```

### 10. **Template Parameters**
   - **Convention**: Upper Camel Case.
   - **Example**:
     ```cpp
     template <typename T>
     class Stack {
         T* elements;
     };

     template <class KeyType, class ValueType>
     class Map {
         // Implementation
     };
     ```

### 11. **File Names**
   - **Convention**: Typically lowercase with underscores, or sometimes Pascal Case, especially for headers (`.h` or `.hpp`) and source files (`.cpp`).
   - **Example**:
     - `account_manager.cpp`
     - `employee_data.hpp`
     - `MyClass.cpp`

### **Summary of Naming Conventions in C++**
- **Variables**: Lower Camel Case (`maxSpeed`)
- **Constants**: All Caps with underscores (`MAX_BUFFER_SIZE`) or prefixed (`kMaxSpeed`)
- **Functions**: Lower Camel Case (`calculateSum`)
- **Classes/Structs**: Upper Camel Case (`AccountManager`)
- **Member Variables**: Lower Camel Case with prefix (`m_speed`) or suffix (`speed_`)
- **Global Variables**: Prefixed with `g_` (`g_maxUsers`)
- **Enums**: Upper Camel Case or All Caps (`Color`, `RED`)
- **Namespaces**: Lowercase or snake case (`my_app`)
- **Macros**: All Caps with underscores (`MAX_CONNECTIONS`)
- **Template Parameters**: Upper Camel Case (`ValueType`)
- **File Names**: Lowercase with underscores or Pascal Case (`account_manager.cpp`)

Consistently following these conventions enhances code readability, maintainability, and clarity, making the code easier for others to understand and work with.

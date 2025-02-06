WIP
The C++ Standard Library provides a wide range of **mathematical functions** in the `<cmath>` (or `<math.h>` in C-style) header. These functions can handle a variety of common mathematical operations such as arithmetic, trigonometry, logarithms, and more.

Here's a list of some of the most commonly used functions from `<cmath>` in C++:

### **1. Basic Arithmetic Functions:**
These functions are used for basic mathematical operations like absolute value, power, square roots, etc.

- **`std::abs(x)`**: Absolute value of `x`
  ```cpp
  int absValue = std::abs(-5);  // absValue = 5
  ```

- **`std::sqrt(x)`**: Square root of `x`
  ```cpp
  double root = std::sqrt(16.0);  // root = 4.0
  ```

- **`std::pow(base, exponent)`**: `base` raised to the power of `exponent`
  ```cpp
  double power = std::pow(2, 3);  // power = 8.0
  ```

- **`std::fmod(x, y)`**: Remainder of `x` divided by `y`
  ```cpp
  double remainder = std::fmod(5.5, 2.0);  // remainder = 1.5
  ```

- **`std::ceil(x)`**: Smallest integer greater than or equal to `x`
  ```cpp
  double ceilValue = std::ceil(3.2);  // ceilValue = 4.0
  ```

- **`std::floor(x)`**: Largest integer less than or equal to `x`
  ```cpp
  double floorValue = std::floor(3.8);  // floorValue = 3.0
  ```

- **`std::round(x)`**: Round `x` to the nearest integer (rounds halfway cases to the nearest even integer)
  ```cpp
  double roundValue = std::round(3.5);  // roundValue = 4.0
  ```

### **2. Trigonometric Functions:**
These functions work with angles, where the angle is typically in radians.

- **`std::sin(x)`**: Sine of `x` (where `x` is in radians)
  ```cpp
  double sinValue = std::sin(M_PI / 2);  // sinValue = 1.0
  ```

- **`std::cos(x)`**: Cosine of `x` (where `x` is in radians)
  ```cpp
  double cosValue = std::cos(M_PI);  // cosValue = -1.0
  ```

- **`std::tan(x)`**: Tangent of `x` (where `x` is in radians)
  ```cpp
  double tanValue = std::tan(M_PI / 4);  // tanValue = 1.0
  ```

- **`std::asin(x)`**: Inverse sine (arcsine) of `x` (returns radians)
  ```cpp
  double asinValue = std::asin(1.0);  // asinValue = M_PI / 2
  ```

- **`std::acos(x)`**: Inverse cosine (arccosine) of `x` (returns radians)
  ```cpp
  double acosValue = std::acos(0.0);  // acosValue = M_PI / 2
  ```

- **`std::atan(x)`**: Inverse tangent (arctangent) of `x` (returns radians)
  ```cpp
  double atanValue = std::atan(1.0);  // atanValue = M_PI / 4
  ```

### **3. Logarithmic Functions:**
These functions are used for logarithms and exponentiation.

- **`std::log(x)`**: Natural logarithm (base `e`) of `x`
  ```cpp
  double logValue = std::log(10.0);  // logValue ≈ 2.3026
  ```

- **`std::log10(x)`**: Logarithm base 10 of `x`
  ```cpp
  double log10Value = std::log10(100.0);  // log10Value = 2.0
  ```

- **`std::exp(x)`**: Exponential function `e^x`
  ```cpp
  double expValue = std::exp(1.0);  // expValue ≈ 2.7183
  ```

### **4. Hyperbolic Functions:**
These functions are analogs of trigonometric functions, but for hyperbolic geometry.

- **`std::sinh(x)`**: Hyperbolic sine of `x`
  ```cpp
  double sinhValue = std::sinh(1.0);  // sinhValue ≈ 1.1752
  ```

- **`std::cosh(x)`**: Hyperbolic cosine of `x`
  ```cpp
  double coshValue = std::cosh(1.0);  // coshValue ≈ 1.5431
  ```

- **`std::tanh(x)`**: Hyperbolic tangent of `x`
  ```cpp
  double tanhValue = std::tanh(1.0);  // tanhValue ≈ 0.7616
  ```

### **5. Miscellaneous Functions:**

- **`std::modf(x, intPtr)`**: Breaks `x` into its fractional and integer parts. The integer part is returned, and the fractional part is stored in `intPtr`.
  ```cpp
  double integerPart;
  double fracPart = std::modf(3.14, &integerPart);
  // fracPart = 0.14, integerPart = 3.0
  ```

- **`std::isnan(x)`**: Checks if `x` is NaN (Not a Number)
  ```cpp
  bool isnanValue = std::isnan(NAN);  // isnanValue = true
  ```

- **`std::isinf(x)`**: Checks if `x` is infinite
  ```cpp
  bool isinfValue = std::isinf(INFINITY);  // isinfValue = true
  ```

- **`std::signbit(x)`**: Returns whether the sign of `x` is negative
  ```cpp
  bool isNegative = std::signbit(-5.0);  // isNegative = true
  ```

- **`std::gcd(x, y)`**: Computes the greatest common divisor of `x` and `y` (C++17 and later)
  ```cpp
  int gcdValue = std::gcd(56, 98);  // gcdValue = 14
  ```

### **6. Constants:**
The `<cmath>` header also provides several **mathematical constants**:

- **`M_PI`**: The mathematical constant π (approximately 3.141592653589793)
  ```cpp
  double pi = M_PI;  // pi ≈ 3.14159
  ```

- **`M_E`**: The mathematical constant e (approximately 2.718281828459045)
  ```cpp
  double e = M_E;  // e ≈ 2.71828
  ```

- **`M_LN2`**: The natural logarithm of 2 (approximately 0.6931471805599453)
  ```cpp
  double ln2 = M_LN2;  // ln2 ≈ 0.6931
  ```

- **`M_INFINITY`**: A representation of positive infinity
  ```cpp
  double inf = M_INFINITY;  // inf = inf (positive infinity)
  ```

---

### **Using `<cmath>` in C++**
To use these functions, include the `<cmath>` header and the appropriate namespace:

```cpp
#include <iostream>
#include <cmath>  // Include the cmath library

int main() {
    double a = 9.0;
    double b = 16.0;
    std::cout << "Square root of " << a << " is " << std::sqrt(a) << std::endl;
    std::cout << "Power: 2^3 = " << std::pow(2, 3) << std::endl;
    std::cout << "Cosine of PI/2: " << std::cos(M_PI / 2) << std::endl;
    return 0;
}
```

### **Summary**
The `<cmath>` header provides a rich set of mathematical functions that cover a wide range of operations including trigonometric, logarithmic, arithmetic, and more. You can use them by including the header and calling the functions directly.

Let me know if you need further details on any specific function!
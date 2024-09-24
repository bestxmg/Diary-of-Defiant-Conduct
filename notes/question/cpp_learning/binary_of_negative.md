## How to represent negative values in binary🐶

Negative values in binary are typically represented using the **two's complement** system, which is widely used in computer systems because it simplifies arithmetic operations like addition and subtraction. Here’s how two’s complement representation works:

### Steps to Represent Negative Values in Binary (Two’s Complement):

1. **Start with the binary representation of the positive number.**
   - For example, to represent `-5` using an 8-bit system, start with the binary representation of `5`: `00000101`.

2. **Invert the bits (one's complement).**
   - Change all `0`s to `1`s and all `1`s to `0`s.
   - For `5` (`00000101`), the one's complement is: `11111010`.

3. **Add 1 to the one's complement.**
   - Adding `1` to the one's complement gives you the two's complement representation.
   - For `11111010`, adding `1` results in: `11111011`.

### Example: Representing -5 in an 8-bit Binary

1. Start with `5`: 
   - Binary: `00000101`
2. Invert the bits:
   - One's complement: `11111010`
3. Add `1`:
   - Two's complement: `11111011`

Therefore, `-5` is represented as `11111011` in an 8-bit binary system.

### Why Two’s Complement is Useful:
- **Arithmetic Simplification**: It allows straightforward binary addition and subtraction without needing separate logic for negative numbers.
- **Unique Zero Representation**: Unlike other systems (like one's complement or sign-magnitude), two’s complement has only one representation for zero (`00000000`), avoiding ambiguities.
- **Range**: For an 8-bit signed integer, the range is from `-128` (`10000000`) to `127` (`01111111`), efficiently utilizing all available bit patterns.

This method is standard across most computer architectures due to its efficiency and simplicity in performing arithmetic operations.
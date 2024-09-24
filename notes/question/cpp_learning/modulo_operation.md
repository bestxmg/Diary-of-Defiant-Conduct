## modulo operation on negative number🐶

### Prerequisites
- [what's C++ standard, usage of it and how it affect the execution of our program](./cpp_standard.md)
- [what's unscoped enumeration and scoped enumeration](./enum.md)

### The interpretation from [C++ 11 standard](https://www.open-std.org/JTC1/SC22/WG21/docs/papers/2011/n3242.pdf)
The operands of * and / shall have arithmetic or unscoped enumeration type; **`the operands of % shall have
integral or unscoped enumeration type.`** The usual arithmetic conversions are performed on the operands
and determine the type of the result.
3 The binary * operator indicates multiplication.
4 The binary / operator yields the quotient, and the binary % operator yields the remainder from the division
of the first expression by the second. If the second operand of / or % is zero the behavior is undefined. **`For
integral operands the / operator yields the algebraic quotient with any fractional part discarded`**;80 if the
quotient a/b is representable in the type of the result, (a/b)*b + a%b is equal to a.


From the citation of C++ 11 standard, we can know that:
1 the operands of % have the type of integral or unscoped enumeration type (which can be implicitly converted int)

2 For integral operands the / operator yields the algebraic quotient with any fractional part discarded

3 if the quotient a/b is **`representable`** in the type of the result, (a/b)*b + a%b is equal to a.


So, let's go back to the original question: how to calculate modulo on negative number. Like a%b where a or b can be negative.
- Firstly, have a judgement on whether a and b meet the requirement of type of modulo operator.

- Secondly, judge whether a/b is **`representable`**, it means any one of a/b can be represent correctly with no wrap around and overflow. It make no sense to conduct the behavior that does't conform to C++ standard.

- Finally, use the equation **(a/b)*b + a%b = a** to get your result.
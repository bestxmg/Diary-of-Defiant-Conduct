## The difference between class and struct in C++🐶
Though `struct` and `class` are very similar in functional usage, they have some differences in aspects of `default access control` and `default inheritance visibility`.

   - In a **`struct`**, members (both variables and methods) are **public** by default.
   - In a **`class`**, members are **private** by default.
   
   &nbsp;

   - When a **`struct`** is used as a base class, inheritance is **public** by default.
   - When a **`class`** is used as a base class, inheritance is **private** by default.
---
### why it says "struct for simple data structures, and class for more complex, object-oriented designs."
`Everything you can do with a class in C++, you can also do with a struct.` 

Keep the above sentence in mind. On this basic, the reason why `"struct for simple data structures, and class for more complex, object-oriented designs."` for the following reasons:

- Historical Usage and Convention: 

    Struct originated from C and was used for plain data structures

- Class Is More Suitable For OOP
      
    Because of the `default access control` and `default inheritance visibility`. Class is more aligned with scenarios where data protection and encapsulation are needed.

- Higher Readability

    Programers are used to accept the implication that struct is a simple data holder while class is a complicate data holder.
    
---
finially, let's take an example to interpret how `struct` can perform Inheritance, Polymorphism and Encapsulation in object-orented-programing.


- Inheritance
```cpp
   struct Base {
       int baseValue;
       void baseFunction() {
           std::cout << "Base function\n";
       }
   };

   struct Derived : Base {
       void derivedFunction() {
           std::cout << "Derived function\n";
       }
   };

   int main() {
       Derived d;
       d.baseFunction();    // Accessing the inherited function from Base
       d.derivedFunction(); // Calling the function from Derived
   }
   ```

- Polymorphism

```cpp
struct Shape {
    virtual void draw() const {
        std::cout << "Drawing a shape\n";
    }
};

struct Circle : Shape {
    void draw() const override {
        std::cout << "Drawing a circle\n";
    }
};

struct Rectangle : Shape {
    void draw() const override {
        std::cout << "Drawing a rectangle\n";
    }
};

int main() {
    Shape* shape1 = new Circle();
    Shape* shape2 = new Rectangle();

    shape1->draw(); // Output: Drawing a circle
    shape2->draw(); // Output: Drawing a rectangle

    delete shape1;
    delete shape2;
}
```
- Encapsulation

```cpp
struct Person {
private:
    std::string name;
    int age;

public:
    void setName(const std::string& n) {
        name = n;
    }

    void setAge(int a) {
        if (a > 0) {
            age = a;
        }
    }

    std::string getName() const {
        return name;
    }

    int getAge() const {
        return age;
    }
};

int main() {
    Person p;
    p.setName("Alice");
    p.setAge(25);
    
    std::cout << p.getName() << ", " << p.getAge() << " years old\n";
}
```
    
    

    


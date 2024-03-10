- Enables objects of different types to be **treated as objects of a common super type**, enhancing flexibility and scalability in code.
- It allows a single interface or class to represent multiple underlying forms or types, facilitating code reuse and reducing complexity.

#### Types of Polymorphism:
---
1. **Compile-Time Polymorphism (Method Overloading):**
    - This type of polymorphism occurs when multiple **methods** have the **same name** but **differ in parameters**.
    - Example: In a `Calculator` class, there might be multiple versions of the `add` method, each accepting different types of arguments (e.g., `add(int, int)`, `add(double, double)`).
2. **Runtime Polymorphism (Method Overriding):**
    - Occurs when a subclass provides a specific **implementation** for a **method** that is **already** defined **in its superclass**.
    - Example: A `Bird` class defines a method `move()`. The subclass `Penguin` overrides this method to provide a specific implementation for how a penguin moves.
3. **Polymorphism through Interfaces:**
    - [[Programming Concepts/Object-oriented Programming (OOP)/Concepts/Interface|Interfaces]] allow for polymorphism by enabling classes to implement methods defined in the interface in their own ways.
    - Example: An interface `Shape` might define a method `draw()`. Different classes like `Circle`, `Square`, and `Triangle` implement the `draw` method in their unique style.

### Related Topics:
---
- [[Programming Concepts/Object-oriented Programming (OOP)/Concepts/Inheritance|Inheritance]]
- [[Programming Concepts/Object-oriented Programming (OOP)/Concepts/Interface|Interface]]
- [[Programming Concepts/Object-oriented Programming (OOP)/Concepts/Abstract Class|Abstract Class]]



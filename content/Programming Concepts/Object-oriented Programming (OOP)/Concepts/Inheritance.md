- Allows for code reuse and hierarchy by enabling a `subclass` to inherit behaviors and data from a `superclass`.
- This mechanism promotes a well-organized, hierarchical structuring of classes, facilitating the extension and modification of existing code.

#### Types of Inheritance:
---
1. **Single Inheritance:**
    - A subclass inherits from only one superclass.
    - Example: A `Mammal` class inherits from a ``Animal`` class.
2. **Multiple Inheritance:**
    - When a subclass inherits from more than one superclass. 
    - This is not supported in some languages.
    - Example: A `Bat` class could inherit from both `Mammal` and `FlyingAnimal` classes.
3. **Multilevel Inheritance:**
    - Chain of classes where one class inherits from a superclass, and then another class inherits from it, forming a multi-level hierarchy.
    - Example: A ``Dog`` class inherits from a `Mammal` class, which in turn inherits from an `Animal` class.

#### Implementation
---
- [[Programming Languages/Java/Object-Oriented Programming (OOP)/Inheritance|Java]]

### Related Topics:
---
- [[Polymorphism|Polymorphism]]
- [[Programming Concepts/Object-oriented Programming (OOP)/Concepts/Interface|Interface]]
- [[Programming Concepts/Object-oriented Programming (OOP)/Concepts/Abstract Class|Abstract Class]]
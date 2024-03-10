- **Classes defined within another class**. They enable logical grouping of classes that are only used in one place, **increasing encapsulation and readability**.
- There are two main types of nested classes: static and non-static (often called inner classes). Each type serves different purposes and has distinct characteristics.

#### Types of Nested Classes:

---

1. **Static Nested Classes:**
    - A static nested class is associated with its outer class, and like static class methods, it **can be accessed without instantiating the outer class**.
    - Example: `OuterClass.StaticNestedClass nestedObject = new OuterClass.StaticNestedClass();`
    - Useful for **helper or utility classes** that are closely related to the outer class but don't require access to its instance variables and methods.
2. **Non-Static Nested Classes (Inner Classes):**
    - Inner classes are **associated with an instance** of the outer class and **can access its attributes**, even if they are declared private.
    - Example: `OuterClass outer = new OuterClass(); OuterClass.InnerClass inner = outer.new InnerClass();`
    - Beneficial when the nested class **logically belongs to the outer class and needs to access its members.**

#### Implementation
---
- [[Programming Languages/Java/Object-Oriented Programming (OOP)/Nested Class|Java]]

### Related Topics:
---
- [[Encapsulation|Encapsulation]]
- [[Programming Concepts/Object-oriented Programming (OOP)/Concepts/Inheritance|Inheritance]]
- [[Polymorphism|Polymorphism]]
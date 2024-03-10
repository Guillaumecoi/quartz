- Refers to the process of converting an object of one type into another. This is typically done to access methods and properties specific to the target type.

#### Types of Casting:
---
1. **Upcasting:**
    - Upcasting is converting a subclass object to a superclass type. It's always safe and doesn't require an explicit cast.
    - Example: A `Dog` object can be upcast to an `Animal` type. This is useful when you want to use general `Animal` methods on a `Dog`.
2. **Downcasting:**
    - Downcasting involves converting an object from a superclass to a subclass type. It requires explicit casting and can lead to an `Exception` if not done carefully.
    - Example: An `Animal` object, which is actually a `Dog`, can be downcast to a `Dog` to access `Dog`-specific methods. This should be done cautiously, typically after checking the object's type.
3. **Casting with Interfaces:**
    - Objects can be cast to an [[Programming Concepts/Object-oriented Programming (OOP)/Concepts/Interface|Interface]] type if they implement that interface. This is common in polymorphic scenarios where different objects share a common interface.
    - Example: If `Dog` and `Cat` both implement an `AnimalBehavior` interface, an instance of `Dog` can be cast to `AnimalBehavior` to invoke interface methods.

### Related Topics:
---
- [[Polymorphism|Polymorphism]]
- [[Programming Concepts/Object-oriented Programming (OOP)/Concepts/Interface|Interface]]
- [[Programming Concepts/Object-oriented Programming (OOP)/Concepts/Inheritance|Inheritance]]
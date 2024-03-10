- Allow for the creation of classes and methods with a **placeholder for the type of data they operate on**. This promotes code reusability and type safety.
- They enable programmers to write **more generalized and flexible code**, which can work with any data type while still enforcing type constraints at compile time.

#### Characteristics:
---
- **Type Parameters:**
    - Generic classes and methods are defined with type parameters (usually denoted by single capital letters like E, T, K, V) that can be used as placeholders for any data type.
    - Example: A generic `List<T>` class can hold any type of object. When an instance is created, such as `List<Integer>`, T is replaced by `Integer`.
- **Compile-Time Type Safety:**
    - Generics enforce type safety at compile time, preventing runtime type errors. This allows errors to be caught earlier in the development process.
    - Example: A generic method `printArray(T[] array)` can accept any type of array. If you try to pass something that is not an array, the compiler will flag it as an error.
- **Elimination of Casts:**
    - Generics eliminate the need for explicit [[Casting]] when retrieving elements from a generic collection, making the code cleaner and more readable.
    - Example: With a `List<Integer>`, you don't need to cast list elements from `Object` to `Integer` when retrieving them.
- **Bounded Type Parameters:**
    - Generics can be restricted to accept certain types of data by using bounded type parameters, enhancing functionality and safety.
    - Example: A generic `List<T extends Number>` **can only accept types that are subclasses of `Number`**, like `Integer`, `Double`, etc.

#### Implementation
---
- [[Programming Languages/Java/Object-Oriented Programming (OOP)/Generics|Java]]

### Related Topics:
---
- [[Casting]]

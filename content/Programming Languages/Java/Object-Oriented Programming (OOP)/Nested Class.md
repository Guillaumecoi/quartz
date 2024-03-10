For general info see: [[Programming Concepts/Object-oriented Programming (OOP)/Concepts/Nested Class|Nested Class]]

### Java
---
In Java, nested classes are divided into two categories: static nested classes and non-static nested classes (inner classes). These allow for logical grouping of classes and enhanced encapsulation.

**Static Nested Class:**
```java
// Outer class
class OuterClass {
    static int outerStaticVariable = 100;
    int outerInstanceVariable = 200;

    // Static nested class
    static class StaticNestedClass {
        void display() {
            // Can access static variable of outer class
            System.out.println("Outer static variable: " + outerStaticVariable);
        }
    }
}

// Usage of static nested class
OuterClass.StaticNestedClass nestedObject = new OuterClass.StaticNestedClass();
nestedObject.display(); // Prints the value of outerStaticVariable

```

**Non-Static Nested Class (Inner Class):**
```java
// Outer class
class OuterClass {
    private int outerVariable = 30;

    // Non-static nested class (Inner class)
    class InnerClass {
        void display() {
            // Can access all variables of the outer class
            System.out.println("Outer variable: " + outerVariable);
        }
    }

    void createInnerInstance() {
        InnerClass inner = new InnerClass();
        inner.display();
    }
}

// Usage of non-static nested class
OuterClass outer = new OuterClass();
OuterClass.InnerClass inner = outer.new InnerClass();
inner.display(); // Prints the value of outerVariable

// Or using a method in OuterClass to create an instance of InnerClass
outer.createInnerInstance();

```
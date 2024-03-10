For general info see: [[Programming Concepts/Object-oriented Programming (OOP)/Concepts/Generics|Generics]]

### Java
---
In Java, generics allow you to create classes, interfaces, and methods where the type of data they operate on is specified as a parameter. This makes your code more flexible and reusable while maintaining type safety.

To define a generic class or method, use type parameters (typically denoted by single capital letters like E, T, K, V).

```java
// Generic class
class Box<T> {
    private T t; // T stands for "Type"

    public void set(T t) {
        this.t = t;
    }

    public T get() {
        return t;
    }
}

// Usage
Box<Integer> integerBox = new Box<Integer>();
integerBox.set(new Integer(10));
System.out.println("Integer Value : " + integerBox.get());

Box<String> stringBox = new Box<String>();
stringBox.set(new String("Hello World"));
System.out.println("String Value : " + stringBox.get());
```

```java
// Generic method
public class Util {
    public static <E> void printArray(E[] elements) {
        for (E element : elements) {
            System.out.println(element);
        }
    }
}

// Usage
Integer[] intArray = {1, 2, 3, 4, 5};
System.out.println("Printing Integer Array:");
Util.printArray(intArray);

String[] stringArray = {"Hello", "World"};
System.out.println("Printing String Array:");
Util.printArray(stringArray);
```
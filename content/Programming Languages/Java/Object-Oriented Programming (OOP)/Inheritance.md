For general info see: [[Programming Concepts/Object-oriented Programming (OOP)/Concepts/Inheritance|Inheritance]]

### Java
---
In `Java` only single inheritance is possible.
To inherit from a class, use the `extends` keyword.

```java
// Base class Animal
class Animal {
    protected String name;

    public Animal(String name) {
        this.name = name;
    }

    public void eat() {
        System.out.println(this.name + " is eating");
    }
}

// Mammal extends Animal
class Mammal extends Animal {
    public Mammal(String name) {
        super(name);
    }

    public void breathe() {
        System.out.println(this.name + " breathes air");
    }
}

// Dog extends Mammal
class Dog extends Mammal {
    public Dog(String name) {
        super(name);
    }

    // Overriding the eat method from Animal class
    @Override
    public void eat() {
        System.out.println(this.name + " eats dog food");
    }

    public void bark() {
        System.out.println(this.name + " says: Woof!");
    }
}

// Usage
Dog myDog = new Dog("Buddy");
myDog.eat();   // Outputs: Buddy eats dog food (Overridden method)
myDog.breathe(); // Inherited from Mammal
myDog.bark();    // Defined in Dog

}
```

If you try to access a `final` class, Java will generate an error:

```java
final class Animal {
    ...
}

class Mammal extends Animal { // Error: cannot inherit from final Animal
    ...
}

```

Returns: `error: cannot inherit from final`

### Related Topics:
---
- [[Programming Languages/Java/Object-Oriented Programming (OOP)/Interface|Interface]]
- [[Programming Languages/Java/Object-Oriented Programming (OOP)/Abstract Class|Abstract Class]]
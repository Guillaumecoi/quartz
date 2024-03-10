For general info see: [[Programming Concepts/Object-oriented Programming (OOP)/Concepts/Abstract Class|Abstract Class]]
### Java
---
In Java, an abstract class is a class that cannot be instantiated and may contain abstract methods. Abstract classes are used to provide a base for subclasses to extend and implement the abstract methods.

To define an abstract class, use the `abstract` keyword.

```java
// Define an abstract class GameCharacter
abstract class GameCharacter {
    protected int health;
    protected int experience;

    // Constructor to set initial state
    public GameCharacter(int health, int experience) {
        this.health = health;
        this.experience = experience;
    }

    // Abstract method to be implemented by subclasses
    public abstract void specialAbility();

    // Concrete method available to all subclasses
    public void gainExperience(int points) {
        this.experience += points;
        System.out.println("Gained " + points + " experience points.");
    }
}

// Subclass Wizard
class Wizard extends GameCharacter {
    public Wizard(int health, int experience) {
        super(health, experience);
    }

    // Implementing the special ability for Wizard
    @Override
    public void specialAbility() {
        System.out.println("Casting a magical spell");
    }
}

// Subclass Warrior
class Warrior extends GameCharacter {
    public Warrior(int health, int experience) {
        super(health, experience);
    }

    // Implementing the special ability for Warrior
    @Override
    public void specialAbility() {
        System.out.println("Performing a powerful attack");
    }
}

// Usage
Wizard wizard = new Wizard(100, 50);
Warrior warrior = new Warrior(150, 30);

wizard.specialAbility(); // Outputs: Casting a magical spell
warrior.specialAbility(); // Outputs: Performing a powerful attack
wizard.gainExperience(20); // Wizard now has 70 experience points
```

### Related Topics:
---
- [[Programming Languages/Java/Object-Oriented Programming (OOP)/Inheritance|Inheritance]]
- [[Programming Languages/Java/Object-Oriented Programming (OOP)/Interface|Interface]]
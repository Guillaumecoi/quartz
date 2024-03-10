For general info see: [[Programming Concepts/Object-oriented Programming (OOP)/Concepts/Interface|Interface]]

### Java
---

In Java, an interface is a completely abstract class that is used to group related methods with empty bodies.

To implement an interface, use the `implements` keyword.

```java
// Define the Sensor interface
interface Sensor {
    public void readValue();   // Interface method for reading sensor value
    public void reset();       // Interface method for resetting the sensor
}

// Implementing the Sensor interface in a TemperatureSensor class
class TemperatureSensor implements Sensor {

	// This method must be implemented
    public void readValue() { 
        System.out.println("Reading temperature...");
    }
    
	// This method must be implemented
    public void reset() {
        System.out.println("Temperature sensor resetting...");
    }
}

class PressureSensor implements Sensor {
    public void readValue() {
        System.out.println("Reading pressure...");
    }
    public void reset() {
        System.out.println("Pressure sensor resetting...");
    }
}

// Usage
TemperatureSensor tempSensor = new TemperatureSensor();
tempSensor.readValue();   // Outputs: Reading temperature...
tempSensor.reset();       // Outputs: Temperature sensor resetting...

PressureSensor pressSensor = new PressureSensor();
pressSensor.readValue();  // Outputs: Reading pressure...
pressSensor.reset();      // Outputs: Pressure sensor resetting...

```

### Related Topics:

---
- [[Programming Languages/Java/Object-Oriented Programming (OOP)/Abstract Class|Abstract Class]]
- [[Programming Languages/Java/Object-Oriented Programming (OOP)/Inheritance|Inheritance]]
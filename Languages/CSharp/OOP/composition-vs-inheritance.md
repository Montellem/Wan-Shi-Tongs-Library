# Composition vs Inheritance
### What is it?
These are two ways to build relationships between classes and reuse code. Inheritance means a class "is a" more specific
version of another class. Composition means a class "has a" relationship with another class, containing it as one of its parts, rather
than being a type of it.

### Example
A "Car" could inherit from "Vehicle" because a car genuinely is a type of vehicle. But a "Car" would use composition for its "Engine", since a car has an engine as one 
of its parts, rather than a car being a type of engine. The engine could even be swapped out for a different engine object without the car itself needing to change what
type it is.

```c#
class Engine
{
    public void Start() => Console.WriteLine("Engine started.");
}

class Vehicle
{
    public virtual void Move() => Console.WriteLine("Vehicle is moving.");
}

class Car : Vehicle // inheritance: Car "is a" Vehicle
{
    private Engine engine = new Engine(); // composition: Car "has an" Engine

    public void Start()
    {
        engine.Start(); // Car delegates to its Engine part
    }
}

Car car = new Car();
car.Start(); // "Engine started."
car.Move();  // "Vehicle is moving." (inherited)
```

### How does it work?
With inheritance, a derived class is locked into being a specific kind of its base class permanently, and the relationship is fixed once defined.
With composition, a class simply holds a reference to another object as one of its parts, and that part can often be changed, replaced, or reused 
independently, without affecting what the containing class fundamentally is.

### Common Mistakes
- Reaching for inheritance just to reuse code, even when the relationship isn't truly an "is a" relationship
- Building depp, rigid inheritance hierarchies when a simpler composition-based design would have been more flexible.
- Assuming composition and inheritance are interchangeable, when they actually represent fundamentally different relationships.


### Practice
**Task:** Think of a "house" that has a "Kitchen", a "Garage" and a "Roof". Explain why these relationships should 
use composition rather than inheritance, and contrast this with the earlier "Vehicle" and "Car" inheritance example.

**Goal:** I should be able to correctly decide, for any given relationship between two concepts, whether it calls for 
composition or inheritance

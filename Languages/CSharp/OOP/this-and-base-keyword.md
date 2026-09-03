# this and base Keyword
### What is it?
These are two special references a class can use to refer to itself and to its parent. "This" refers to the current object
itself, the very instance the code is currently running on. "Base" refers specifically to the parent class that the current class
inherits from, letting you reach up to its original behavior.

### Example
Inside a "Car" class that inherits from "Vehicle", using "this" might refer to the specific car object currently being worked with,
for example to distinguish a parameter from a property that happen to share a similar name. Using "base" inside "Car" could let it call
the original "move" action defined "Vehicle", even after "Car" has overridden that same action with its own version.

```c#
class Vehicle
{
    public virtual void Move()
    {
        Console.WriteLine("Vehicle is moving.");
    }
}

class Car : Vehicle
{
    public int Speed;

    public Car(int speed)
    {
        this.Speed = speed; // "this" distinguishes the field from the parameter
    }

    public override void Move()
    {
        base.Move(); // calls Vehicle's original Move() first
        Console.WriteLine($"Car is now driving at {Speed} km/h.");
    }
}

Car car = new Car(100);
car.Move();
// Output:
// Vehicle is moving.
// Car is now driving at 100 km/h.
```

### How does it work?
"This" is mainly useful for being explicit about which object you're referring to, especially when a parameter
and a class member could otherwise be confused. "Base" is mainly useful within inheritance: it lets a derived
class still reach back and use the original version of something from its parent class, even while also providing and running
its own overriding version on top of it.

### When should I use it?
- Use "this" when you need to clearly distinguish the object's own data from something else with similar name, like a constructor parameter
- Use "base" when a derived class wants to extend, rather than completely replace, behavior from its parent class
- Use "base" when calling the parent class's constructor is required to properly set up inherited data.

### Common Mistakes
- Overusing "this" everywhere it isn't actually needed, making code more cluttered than necessary
- Forgetting to use "base" when overriding a behavior that was supposed to add to the original, not fully replace it.
- Confusing "base" with simply calling the derived class's own overriding method again, causing unexpected repeated behavior.

### Pracitce
**Task:** Using the "Car" and "Vehicle" example from Inheritance, describe a situation where "Car" overrides the "move" action but still
wants to run "Vehicle's" original version of "move" first, before adding its own extra behaviour

**Goal:** I should be able to explain the difference between "this" and "base", and describe a realistic situation for using each one.

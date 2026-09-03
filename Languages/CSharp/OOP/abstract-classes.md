# Abstract Classes
### What is it?

An abstract class is a base class that can never be created as an object on its own. It exists purely as a foundation
for other classes to inherit from, often defining some shared behavior fully, while leaving other parts unfinished on purpose,
requiring derived classes to complete them.

### Example
A "Shape" class could be made abstract, since "just a shape" with no specific type doesn't really make sense on its own. It might
define that every shape must have a "calculate area" action, without saying how, and leave it to "Circle" and "Square" to actually
provide that specific logic when they inherit from it.

```c# 
abstract class Shape
{
    public abstract double CalculateArea(); // no implementation here

    public void Describe() // shared, fully implemented behavior
    {
        Console.WriteLine("This is a shape.");
    }
}

class Circle : Shape
{
    public double Radius;
    public override double CalculateArea() => Math.PI * Radius * Radius;
}

// Shape shape = new Shape(); // not allowed, Shape is abstract
Circle circle = new Circle { Radius = 3 };
Console.WriteLine(circle.CalculateArea());
```

### How does it work?
An abstract class can mix fully working, shared behavior with placeholder actions that have no implementation yet.
Any class that inherits from it is required to provide the missing pieces before it can be used to c reate actual objects. This 
forces every derived class to follow the same overall structure while still allowing each one to fill in its own specific defails.

### When should I use it?
- When a concept is too general to ever exist as a real, standalone object by itself
- When you want to gurantee that every derived class provides certain specific behavior
- When several related classes should share some common code while differing in other specific parts

### Common Mistakes
- Trying to create an object directly from an abstract class, which is not allowed.
- Making a class abstract when it ac tually makes sense to create real objects from it directly
- Leaving too many things unfinished, so derived classes end up doing almost all the work anyway

### Practice
**Task:** Revisit the "Shape" example. Explain why it makes sense for "Shape" to be abstract, but for "Circle" 
and "Square" to not be abstract themselves.
**Goal:** I should be able to explain why abstract classes cannot be used to create objects directly,
and recognize when a class is a good candidate to abstract.



# Polymorphism
### What is it?
Polymorphism means that different classes can be treated through the same shared interface or base type,
even though each one behaves in its own specific way when actually used. The world literally means "many forms."

### Example
Imagine you have a "Shape" base class with an action called "calculate area" and both "Circle" and "Square" inherit from it.
You can treat a list full of different shapes all as "Shape", and when you ask each one to calculate its area, a circle 
calculates it one way and a square calculates it a completely different way, even though you called the exact same action on all of them.

```c#
abstract class Shape
{
  public abstract double CalculateArea();
}

class Circle : Shape
{
  public double Radius;
  public override double CalculateArea() => Math.PI * Radius * Radius;
}

class Square : Shape
{
  public double Side;
  public override double CalculateArea() => Side * Side;
}
List<Shape> shapes = new List<Shape> { new Circle { Radius = 2 }, new Square { Side = 3 } };

foreach (Shape shape in shapes)
    Console.WriteLine(shape.CalculateArea()); // each runs its own version
```

### How does it work?
A derived class can provide its own specific version of a behavior that was originally defined in its base class.
When code refers to an object using the general base type, it still automatically runs whichever specific version
belongs to the actual object's real type. This allows you to write code that works with the general concept, while
still getting the correct specific behavior for each particular case.

### When should I use it?
- When you have several related classes that all need to perform a similar action, just in different ways
- When you want to write general code that works with a whole family of related types at once
- When you want to add new related classes later without having to rewrite the code that uses them

### Common Mistakes
- Using long chains of checks to figure out an object's exact type instead of letting polymorphism handle it naturally
- Forgetting to actually provide a specific version of the behavior in a derived class, leaving it stuck with the base behavior
- Confusing polymorphism with inheritance itself, when really it's about behavior varying across related types

### Pracite
**Task:** Using "Employee" example from Inheritance, imagine both "Manager" and "Intern" have an action called "decribe role."
Explain how you could through a list containing both types, calling "descripe role" on each one, and get a different appropriate
description back from each without checking their type first.

**Goal:**
I should be able to explain, in my own words, why polymorphism is useful and how it lets code stay simple even when handling
many different related types.

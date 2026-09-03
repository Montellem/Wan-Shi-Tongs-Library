# Method Overriding and Overloading
### What is it?
Overriding and overloading are two different ways methods can have multiple versions, and they are easy to confuse.
Overriding is when a derived class replaces the behavior of a method inherited from its base class. Overloading is
when a single class has multiple methods with the same name, but each one accepts different information.

### Example
Overriding a base "Animal" class has a "make sound" action, and a derived "Dog" class overrides it to bark instead
of making a generic sound. Overloading a "Calculator" class could have several "add" actions, one that adds to whole
numbers, and another that adds three whole number, all named "add" but each expceting different input.

```c#
class Animal
{
  public virtual void MakeSound() => Console.WriteLine("Some generic sound.");
}

class Dog: Animal
{
  public override void MakeSound() => Console.WriteLine("Bark!");
}

Animal animal = new Dog();
animal.MakeSound(); // "Bark!" - Dog's overriding version runs

// Overloading
class Calculator
{
  public int Add(int a, int b) => a + b;
  public int Add(int a, int b, int c) => a + b + c;
}

Calculator calc = new Calculator();
Console.WriteLine(calc.Add(2, 3));    // uses the two-parameter version
Console.WriteLine(calc.Add(2, 3, 4)); // uses the three-parameter version
```

### How does it work?
Overriding works within an inheritance relationship: the base class defines a behavior that is allowed to be replaced,
and he derived class provides its own version, which runs instead of the original whenever it's used on that specific type.
Overloading had nothing to do with inheritance at all: it simply means the same action name can exist multiple times in one class,
and the correct version is automatically chosen based on what information you actually provide when calling it.

### When should I use it?
- Use overriding when a derived class genuinely needs to behave differently than its base class for a specific action
- Use overloading when the same general action makes sense with different combinations of input information
- Use both when they genuinely simplify how your code reads and behaves, not just because they are available.

### Common Mistakes
- Mixing up the two concepts, since they sound similar but solve completely different problems
- Overriding a behavior in a way that breaks the expectations set by the base class
- Creating overloaded actions that behave in confusingly different or inconsistent ways from each other.

### Pracitce
**Task:** Explain, in your own words, whether the "calculate area" example from Abstract classes is an example of 
overriding or overloading, and why. Then invent a small overloading example of your own.

**Goal:** I should be able to clrealy distinguish overriding from overloading and explain when each one applies.

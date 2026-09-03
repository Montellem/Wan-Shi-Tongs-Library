# Sealed Classes
### What is it?
A sealed class is a class that explicity forbids any other class from inheriting from it. Once 
a class is sealed, it marks the end of that particular inheritance chain, and no derived classes can be created from it.

### Example
A "FinalReport" class mightbe sealed once it's considered complete and stable, to prevent anyone from creating a modified derived version
of it later that could behave in unexpected ways, since the class is meant to represent one final, fixed concept.

```c#
sealed class FinalReport
{
  public string Title;
  public DateTime CreatedAt;
}
```

### How does it work?
By default, classes can normally be inherited from unless something prevents it. Marking a class as sealed adds that restriction directly,
so any attempt to create a new class that inherits from it will simply not be allowed. This doesn't affect how the sealed class itself
works internally, only whether other classes are permitted to build on top of it.

### When should I use it?
- When you want to gurantee that a class's behavior can never be changed through inheritance later.
- When a class represents a very specific, final concept that shouldn't have variations
- When allowing inheritance could lead to fragile or unpredictable behavior in your program.

### Common Mistakes
- Sealing a class too early, before knowing whether future variations might genuinely be needed
- Sealing classes by habit everywhere, when open inheritance would have been perfectly reasonable
- Assuming sealing improves performance in a way that meaningfully matters for typical, everyday code.

### Practice
**Task:** Think back to the "Vehicle", "Car", and "Motorcycle" example from Inheritance. Explain whether it would make sense to seal
the "Car" class, and what the consequences of doing so would be.

**Goal:** I should be able to explain what sealing a class prevents, and judge when it is a reasonable design choice.

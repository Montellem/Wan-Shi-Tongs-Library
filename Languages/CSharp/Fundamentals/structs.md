# Structs
### What is it?
A struct is a balue type used to bundle several related values into a single unit, similar to a class,
but with one key difference in behavior: structs are ocpied on assignment and method calls,
while classes are passed by reference.

### Example
Picture a point in a coordinate system, made up of an X and a Y coordinate. Instead of managing
two separate variables, you bundle both values into a struct called "Point". If
you assign a Point variable to a second variable, a fully independent copy is created. If you then change the copy,
the original stays the same.

```c#
struct Point
{
  public int X
  public int Y
}

Point original = new Point { X = 1, Y = 2];
Point copy = original //full copy
copy.X = 99;

Console.WriteLine($"Original: {original.X}, {original.Y}"); // 1, 2
Console.WriteLine($"Copy: {copy.X}, {copy.Y}");              // 99, 2
```

### How does it work?
A struct is stored on the stack (or embedded within a surrounding object) rather than on the heap, which makes
structs more efficient than calsses for small, frequently used pieces of data. Because structs are value types, every assignment, 
every method call, and every return creates a full copy of all the contained values. This is fundamentally different from calsses,
where multiple variables can point tothe very same object in memory.

### When should I use it?
- For small, immutable bundles of data that logically represent a single value (e. g. coordinates, color values)
- When frequent copies of the data are desired instead of shared references
- When the data doesn't need a complex inheritance hierarchy

### Common Mistakes
- Making large, ocmplex data structures a struct when a class would be better fir
- Not considering that changing a copy doesnt affect the original, and being confused by "disappearing" changes.
- Using structs for objects that should actually have a shared, common identity.

### Practice
**Task:** Define a struct for a point with X and Y coordinates. Create a point, assign it to a second variable, change the copy
coordinates, and print both points to observe the difference between the original and the copy.

**Goal:** After this exercise you should be able to explain the fundamental difference between value types (struct) and reference types (class).

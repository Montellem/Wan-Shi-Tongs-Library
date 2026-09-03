# Records
### What is it?
A record is a modern kind of type designed specifically to represent data, where the values it holds matter more than the
specific object holding them. Two records containing exactly the same data are treated as equal to each other, unlike regular classes,
where two objects are only considered equal if they are literally the very same object in memory.

### Example
Imagine a "Coordinate" record holding a latitude and a longitude. Two separate coordinate records that happen to hold
the exact same latitude and longitude values would be considered euqal to each other, because what matters is the
data itself, not which specific object instance you're looking at.

```c#
record Coordinate(double Latitude, double Longitude);

Coordinate point1 = new Coordinate(52.5, 13.4);
Coordinate point2 = new Coordinate(52.5, 13.4);

Console.WriteLine(point1 == point2); // True, values are equal

Coordinate point3 = point1 with { Longitude = 9.9 }; // create a new record based on an old one
Console.WriteLine(point3); // Coordinate { Latitude = 52.5, Longitude = 9.9 }
```

### How does it work?
Records are built around the idea that once created, their data typically shouldn't change. Instead of modifying an existing record,
you usually create a new one based on an old one, changing only the specific values you need to update, while everything else carries over
unchanged. Comparisons between records automatically check whether all their values match, rather than checking whether they're the same 
object in memory.

### When should I use it?
- When you're modeling data that represents a value, like a coordinate, a price , or a date range, rather than a thing with its own identity.
- When you want built-in, automatic comparison based on the actual data a type holds
- When you want to strongly ecourage that a type's data stays unchanged once created.

### Common Mistakes
- Using a record for something that has a real identity beyond its data, like specific "Customer" that should stay the same entity even it their name changes.
- Expecting a record to behave exactly like a normal class in every situation, especially around equality and change
- Overusing records everywhere out of habit, instead of reserving them for genuinely data-focused concepts

### Practice
**Task:** Think about a "Money" concept holding an amount and a currency. Explain why this might be a good candidate for a record,
and contrast it with the "Person" example from Constructors, which likely represents a real, ongoing identity rather than just a value.

**Goal:** I should be able to explain the core difference between a record an a regular class, and recognize which one fits a given concept better.

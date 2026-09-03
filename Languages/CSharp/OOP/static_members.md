# Static Members
### What is it?
a static member belongs to the class itself, not to my individual object created from it. While
normal fields, properties, and methods exist separately for every object, a static member is shared
and exists only once, no matter how many objects are created.

### Example
Imagine a "Counter" class that tracks how many objects of a certain type have been created in total.
That total count doesn't belong to any single object, it belongs to the class as a whole. Every time
a new obejct is created, the shared count goes up by one, and every object sees the same, single shared number.

```c#
class Counter
{
  public static int TotalCreated; // shared by all objects

  public Counter()
  {
    TotalCreated++;
  }
}

Counter a = new Counter();
Counter b = new Counter();
Counter c = new Counter();

Console.WriteLine(Counter.TotalCreated); // 3, accessed through the class itself
```

### How does it work?
A static member lives at the class level and is loaded once, independent of how many objects exist,
even it non exist yet. You access it through the class name itself, not through and individuall object.
Because it is shared, changing it from one place affects everyone who looks at it, which is very different from 
regular object data that stays separate per object.

### When should I use it?
- When data or behavior truly belongs to the concept as a whole, not to one specific instance
- For utility actions that don't need any object-specific data wo work, like general helper calculations
- When you need a single shared value that all obejcts of a class should see and agree on

### Common Mistakes
- Using static members for data that should actually be different per object, causing values to bleed between unrelated objects
- Overusing static members as a shortcut to avoid creating objects properly, leading to tangled, hart-to-test code
- Forgetting that static data is shared everywhere it's used, which can cause unexpected side effects in larger programs

### Practice
**Task:** Think of a "Product" class where each product has its own individual price, but the store as a whole
has one shared tax rate that applies to everything, Explain which of there two pieces of data should be static and which should be not and why.

**Goal:** I should be able to correctly decide whether a given piece of data belongs on the object level or the class level.

  


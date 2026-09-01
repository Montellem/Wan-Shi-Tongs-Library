# Constans (const and readonly)
### What is it?
Constants are values that can't be changed once they're set. C# offers two keywords for this const,
for values known already at compile time, and readonly, for values that are set
once at runtine (e. g. in the cunstroctor) and stay unchangeable afterward.

### Example
Imagine you define a value for Pi as const, becaus the value never changes and is already
known when you write the code. Alongside that, a class might store a creation timestamp
as a readonly field: the exact value isn't known until an object is actually created, but it must not change afterward.

```c#
cpmst double Pi = 3.14159

class Event
{
  public readonly DateTime Created;

  public Event()
  {
    Created = DateTime.Now // set once, in the constructor
  }
}
```

### How does it work?
const values are inserted directly into the code at compile time and must therefore
already be known at compile time, they can only be assigned simple, fixed values. 
Readonly fields, on the other hand, may be computed at runtime, but only set inside the class's 
constructor or directly at declaration. Once Initializied, the compiler rejects any further asignment.

### When should I use it?
- For fixed, universal values that never change (e.g. mathematical constants, fixed configuration values)
- To prevent accidental changes to important values in the code.
- To make the intent in the code clear: "this value is deliberately unchangeable."

### Common Miistakes
- Trying to use const for values that are only computed at runtimme (this doesn't work, readonly is needed here)
- Trying to change a readonly field outside the constructor
- Hardcoding too many values as const when they should actually be configurable

### Practice
**Task:** Create a const variable for a fixed conversion factor (e. g. kilometers to miles) and use it in a small
calculation. Then think of an example from your everyday life that would be better suited to readonly, and explain whay.

**Goal:** After this exercise you should be able to explain when to use const and when to use readonly.
  #

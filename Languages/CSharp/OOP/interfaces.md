# Interfaces
### What is it?
An interface is a pure contract that lists actions a class promises to provide, without containing any actual implementation 
itself. Any class that agrees to follow an interface must supply its own working version of every action listed in it.

### Example
Imagine an interface called a "Printable" that requires a "print" action. A "Document" class and an "invoice" class could both agree
to follow "Printable", each providing their own version of what "print" actually means for them, even though the two classes
are otherwise completely unrelated.

```c#
interface IPrintable
{
    void Print();
}

class Document : IPrintable
{
    public void Print() => Console.WriteLine("Printing document...");
}

class Invoice : IPrintable
{
    public void Print() => Console.WriteLine("Printing invoice...");
}

List<IPrintable> items = new List<IPrintable> { new Document(), new Invoice() };
foreach (IPrintable item in items)
    item.Print(); // each type provides its own Print behavior
```

### How does it work?
Unlike an abstract ckass, an interface defines no shared behavior at all, only a list of required actions. A class can
agree to follow several different interfaces at once, even if those classes don't share a common base class. This allows
completely unrelated classes to still be treated the same way, as long as they all fulfill the same contract.

### When should I use it?
- When you want to define a capability that many unrelated classes could share, regardless of their type
- When a class needs to follow multiple different contracts at the same time
- When you want to describe what something can do, without caring at all how it's build interanally

### Common Mistakes
- Confusing an interface with an abstract class, since an interface has no shared implementation at all
- Creating interfaces with too many required actions, amking it a burden for classes to follow them
- Forgetting that a class must fully implement every single action promised by an interface it agrees to follow

### Practice
**Task:** Think of an int erface called "Comparable" that requires an action for comparing two things to see which
is bigger. Describe three completely unrelated classes, such as "Product", "Person" and "Task", that could each
implement "Comparable" in their own specific way.

**Goal:** I should be able to explain the difference between an interface and an abstract class, and know when to reach
for each one.

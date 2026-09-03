# Object Initializers
### What is it?
An object initializer is a shorthand way create a new object and immediately set several of its properties at the same time,
all in one clear, readable step, without needing a constructor that accpets every single value.

### Example
Instead of creating a new "Person" object and then setting its name, then separately setting its age, then separately
setting its city, on object initializer lets you create the person and set the name, age, and city all together in single, tidy block.

```c#
class Person
{
  public string Name;
  public int Age;
  public string City;
}

Person person = new Person
{
  Name = "Anna",
  Age = 28,
  City = "Nuremberg"
};

Consoel.WriteLine($"{person.Name}, {person.Age}, {person.City}");
```

### How does it work?
After an object is created, an object initializer sets a list of specified properties right away, before the object is considered
fully ready for use. This relies on those properties allowing outside code to set their values. It's essentially a convenient shortcut
that combines object creation and initial setup into one readable step, instead of writing several separate lines.

### When should I use it?
- When creating an object that has several properties you want to set right away, and a matching constructor doesn't exist or isn't convenient
- When you want your object creation code to be easy to read at a glance
- When the properties involved are meant to be freely settable from outside the class

### Common Mistakes
- Relying on object initializers for properties that should actually be protected and only changable through controlled logic
- Using an object initializer when required Information really should be enforced trhough a constructor instead
- Forgetting that object initializes only work with properties that allow outside code to set them

### Practice
**Task:** Take the "Person" example with a name, age, and city. Explain when it would make more sense to require a constructor
for this data instead of allowing an object initializer to set it freely.

**Goal:** I should be able to explain the trade-off between using a constructor and using an object initializer for setting up a new object.

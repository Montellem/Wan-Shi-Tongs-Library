# Constructors
### What is it?
A constructor is special logic that runs automatically when a new object is created from a class. Its job is 
to set the object up correctly from the very first moment it exists, usually by giving its fields or properties their starting values.

### Example
Imagine a "Person" class that requires a name and a birth date. A constructor for this class would demand that
both pieces of information be provided the moment a new person object is created, so it is impossible to end up
with a person who has no name at all.

```c#
class Person
{
  public string Name;
  public DateTime BirthDate;

  public Person(string name, DateTime birdhDate)
  {
    Name = name;
    BirthDate = birthDate;
  }
}

Person person = new Person("Anna", new DateTime(1996, 4, 12));
Console.WriteLine(person.Name);
```

### How does it work?
When you create an object, the constructor runs before anything else can use that object. You can require certain information to be passed in at creation time, and the constructor takes that information and stores it in the object's fields or properties. A class can also have several different constructors, offering different ways to create the same kind of object depending on what information is available.

When should I use it?
When an object should never exist in an incomplete or invalid state
When certain data absolutely must be provided at the moment of creation
When you want to offer multiple convenient ways to create the same type of object
Common Mistakes
Leaving important data unset, allowing objects to exist with missing or invalid information
Putting too much unrelated logic inside a constructor instead of just basic setup
Forgetting that if you don't define any constructor, a class gets an automatic empty one, which may not properly initialize everything
Practice

**Task:** Describe a "Book" class that must always have a title and an author. Explain what the constructor should require, and what should happen if someone tries to create a book without providing a title.

**Goal:** I should be able to explain why constructors help prevent objects from ending up in a broken or incomplete state.

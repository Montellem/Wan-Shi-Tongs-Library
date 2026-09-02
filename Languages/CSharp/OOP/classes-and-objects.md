# Classes and Objects
### What is it?
A class is a blueprint that describes what data and behaviour for something should have. An object
is a concrete instance created from that blueprint. If the class is the plan for a "Car", the objects is an actual
car built from that plan, with its own specific color, speed, and fuel level.

### Example
Imagine a class called "Customer" that defines a name, an email address, and an action called "place order". Every
time a new customer signs up, a new object is created from that class. Each customer object has its own name and email, 
but they all sahre the same structure and the same ability to place an order.

```c#
class Customer
{
  public string Name;
  public string Email;

  public void PlaceOrder()
  {
    Console.WriteLine($"{Name} placed an order.");
  }
}

// Two separate objects created from the same class
Customer customer1 = new Customer { Name = "Anna", Email = "anna@mail.com"}
Customer customer2 = new Customer { Name = "Ben", Email = "ben@mail.com"}

customer1.PlaceOrder() // Anna placed an order.
customer2.PlaceOrder() // Ben placed an order.
```

### How does it work?
The class only exists once in your code, as a definition. Objects are created ("instantiated") from that
definition as many times as needed, each one living separately in memory. Changing the data of one object does not affect 
any other object created from the same class, even though they share the same blueprint.


### When should I use it?
- When you need to represent a real-world thing or concept with both data and behaviour
- When you expect to create many similar items that share the same structure.
- When you want to group related data and actions together instead of keeping them scattered.

### Common Mistakes
- Confusing the class (the blueprint) with the objects (the actual thing built from it).
- Putting unrelated data and behavior into a single class instead of splitting responsibilities.
- Creating a class for something tha is really jnust a single, one-off value.

### Practice
**Task:** Think of three real-world things you can use daily (for example, a phone, a book, a cup). For each one,
describe what a class for it would contain: what data it would hold and what actions it could perform. Then describe
what two different objects created from one of these classes might look like.

**Goal:** I should be able to cleary explain, in my own words, the difference between a class and an object, and recognize which one
I am talking about in a given example.

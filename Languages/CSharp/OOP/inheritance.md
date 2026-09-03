# Inheritance
### What is it?
Inheritance lets one class take over the data and behavior of another class, and then add or change things
on top of it. The class being built upon is called the base or parent class, and the new class is called the 
derived or child class.

### Example
Imagine a general "Vehicle" class that defines a speed and an action to move. A "Car" class and a
"Motorcycle" class could both inherit from "Vehicle", automatically getting the speed and movement
behavior, while each adding their own specific details, like a car having four doors and a motorcycle having a kickstand.

```c#
class Vehicle
{  
  public int Speed;

  public void Move()
  {
    Console.WriteLine($"Moving at {Speed} km/h);
  }
}

class Car : Vehicle // Car inhertis from Vehicle
{
  public int NumberOfDoors;
}

Car car = new Car {Speed = 100, NumerOfDoors = 4};
car.Move(); // inherited from Vehicle: "Moving at 100 km/h."
```

### How does it work?
The derived class automatically has access to everything the base class defines, without
having to rewrite it. It can then add completely new data and behavior of its own, and it can also
change how some of the inherited behavior works to better fit its specific case. This creates
a hierarchy, where general, shared concepts sit at the top and more specific variations sit below.

### When should I use it?
- When multiple classes clearly share common data and behavior, and one is a more specific version of another.
- When you want to avoid duplicating the same code across several similar classes
- When there is a genuine "is a" relationsship, such as a car "is a" vehicle


### Common Mistakes
- Using inheritance just to reuse code, even when there isn't a real "is a" relationship between the classes
- Creating very deep chains of inheritance that become hard to follow and understand
- Forcing a derived class to inherit behavior that doesn't actually makes sense for it

### Practice
**Task:** Think of a general "Employee" class with a name and a salary. Describe two more 
specific classes that could inherit from it, such as "Manager" and "Intern", and explain
what each one would add or change compared to the base class.

**Goal:** I should be able to recognize when inheritance is a good fit, and describe the relationship between
a base class and a derived class clearly.

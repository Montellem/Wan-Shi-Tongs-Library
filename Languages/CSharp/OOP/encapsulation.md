# Encapsulation
### What is it?
Encapsulation is the principle of hiding an object's internal details and only exposing a controlled,
well-defined way to interact with it. The obejct protects its own data instead of letting outside code
reach in and change things freely.

### Example
A "Thermostat" object might hide the exact internal temperature sensor readings and calculations.
From the outside, you can only ask it to set a target temperature or read the current one, 
using clearly defined actions. You cannot directly tamper with its internal writing or sensor values,
you can only interact through the controls it offers.

```c#
class Thermostat
{
  private double currentTemperature = 20.0 // hidden internal detail

  public double TargetTemperature {get; private set}

  public void SetTarget(double target)
  {
    if (target >= 5 && target <= 30) // validation rule
        TargetTemperature = target;
  }

  public double ReadCurrentTemperature()
  {
    return currentTemperature // controlled read-only access
  }
}
```

### How does it work?
This principle is achieved by combining hidden fields with controlled properties an methods as covered in earlier topics.
The object decides exactly what can be read, what can be changed, and under what conditions. This way, the obejct is always
responsible for keeping its own data valid and consistent, rather than trusting every piece of outside code to behave 
correctly.

### When should I use it?
- Whenever an object has internal data that could become invalid if changed carelessly from outside
- When you want changes to an object's state to always go through validation or specific rules
- When you want to be free to change how something works internally without breaking other code that uses it.

### Common Mistakes
- Exposing raw internal data directly, which defeats the purpose of encapsulation entirely
- Adding controlled access points but forgetting to actually add any validation or rules inside them
- Making a class so locked down that it becomes impossible to use in legitimate, necessary ways

### Practice
**Task:** Look back at the "BankAccount" example. Explain, using the term encapsulation why hiding the raw
balance field and only allowing deposits and withdrawals through specific actions protects the account from
ending up in an invalid state.

**Goal:** I should be able to explain encapsulation as a concept, not just as fields and properties, and
connect it to why it matters in real programms.

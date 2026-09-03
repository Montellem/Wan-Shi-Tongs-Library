# Abstraction
### What is it?
Abstraction means focusing on what something does it. It Lets you work with a simplified idea of a thing,
ignoring the complicated details that aren't necessary for using it.

### Example
When you drive a car, you use the steering wheel, pedals and gear shift. You don't need to understand exactly
how the engine converts fuel into motion internally. The car gives you an abstract, simplified way to control it,
hiding all of the complex mechanical detail happendin underneath.

```c#
interface IPayment
{
  void Process(decimal amount); // simplified, abstract action
}

class CreditCarPayment : IPayment
{
  public void Process(decimal amount)
  {
    // complex card-network logic hidden here
    Console.WriteLine($"Processed {amount} via credit card.");
  }
}
IPayment payment = new CreditCardPayment();
payment.Process(50); // caller doesn't need to know how it works internally
```

### How does it work?
In code, abstraction is often archieved by defining what actions something should be able to perform, without
specifying excatly how each one is carried out internally. Different classes can then implement those actions in whatever
way makes sense for them, while anyone using them only needs to know about the simplified, high-level actions available,
not the internal complexity behind them.

### When should I use it?
- When the internal details of how something works are not relevant to the code that simply wants to use it
- When you want to define a common, simplified way of interacting with several different, more complex things
- Wheny o uwant to reduce complexity for anyone reading or using your code.

### Common Mistakes
- Exposing too much internal detail, forcing users of your class to undersstand things they shouldn't need to
- Making something so abstract and vague that it becomes unclear what it actually does
- Confusing abstraction with encapsulation, when they solve related but different problems one hides complexity, the oder protects data.

### Practice
**Task:** Think about using a "Payment" concept in an application, where the actual payment could be made by creditcard, bank transfer,
or a mobile wallet. Describe the simplified, abstract actions someone using "Payment" should be able to call, without needing to know
the specific details of how each payment method processes the transaction internally.

**Goal:** I should be able to explain, in my own words, the difference between abstraction and encapsulation.

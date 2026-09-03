# Access Modifiers
### What is it?
Access modifiers control who is allowed to see or use a piece of code, such as a field, property, method, or entire class. 
They define the boundary between what is meant to be used from outside a class and what should stay hidden as an internal detail.

### Example

```c#
class BankAccount
{
  private decimal balance; // hidden: only usable inside the class
  private decimal Balance => balance; // open: readable from outside

  public void Deposit(decimal amount) //open: usable from outside
  {
    if (amount > 0)
        balance += amount;
  }

  public bool IsValidAmount(decimal amount) // hidden: internal helper only
  {
    return amount > 0;
  }
}
```

### How does it work?
Somethind marked as fully open can be used by any other code, anywhere. Something marked
as hidden can only be used inside the same class where it was defined. There are also in-between
levels, such as allowing access within the same family of related classes, or only within the same project. 
Choosing the right level of access is about deciding what other developers, or your future self, should and should
not be allowed to touch directly.

### When should I use it?
- Keep internal details hidden whenever outside code has no legitimate reason to use them directly
- Open up only the parts of a class that are meant to be used as its public interface
- Use restricted access to protect data that should only be modified through controlled logic, like a property

### Common Mistakes
- Making everything fully open "just in case", which removes the protection that access control provides
- Hiding something that other parts of the program genuinely need to use, forcing awkward workarounds
- Not thinking about access levels at all and leaving everything at whatever the default happens to be

### Practice
**Task:** Take the "Bank Account" example from the Fields and Properties topic. Decide which parts 
(the balance field, the deposit action, the withdrawal action) should be hidden and which should be open
outside code, and explain why for each one.

**Goal:** I should be able to justify, for any piece of a class, whether it should be hidden or exposed,
and explain the risk of getting that choice wrong.

# Fields and Properties
### Fields and properties are both ways a class stores its data. A field is the raw storage
location itself, like a private box inside the object. A property is a controlled entry point to that data,
deciding how the value can be read or changed from outside the class.

### Example
Think of a "Bank Account" class. It might have a hidden field that stores the actual balance number.
Instead of letting anyone reach in and change that number directly, the class offers a property called 
"Balance" that lets others read the current amount, but only allows it to change through
specific rules, such as masking a deposit or withdrawal.

```c#
class BankAccount
{
  private decimal balance; // field: raw internal storage

  public decimal Balance // property: controlled access point
  {
    get {return balance; }
    private set { balance = value; }
  }
  public void Deposit(decimal amount)
  {
    if (amount > 0)
      Balance += amount;
  }
}

Bankaccount account = new Bankaccount();

account.Deposit(100);
Console.WriteLine(account.Balance); // 100
// account.Balance = -50; // not allowed, setter is private
```

### How does it work?
A field simply holds a value in memory. A property looks like a field from the outside, but
internally it can run logic every time it is read or written, for example checking that a new value is valid
before accepting it. This lets a class protect its internal data from being set to something nonsensical, like a negative account balance.

### When should I use it?
. Use fields for internal, private storage that only the class itself needs to manage directly
- Use properties whenever you want to expose data to the outside world in a safe, controlled way.
- Use properties when you need validation, computed values, or read-only access to data

### Common Mistakes
- Making fields public so any code can change them without any checks
- Adding a property that does nothing except pass a value through, when a simple field would work internally
- Forgetting to validate incoming values inside a property, defeating the purpose of controlling access.

### Practice
**Task:** Describe a class for a "Product" with a price. Explain how you would a field and a property
together so that the price can never be set to a negative number from outside the class.

**Goal:** I should be able to explain why direct access to raw data is often risky, and how properties help protect an object's internal state.



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

}
```

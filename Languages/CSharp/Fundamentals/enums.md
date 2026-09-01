# Enums

### What is it?

An enum (enumeration) is its own data type made up of a fixed, named list of possible values. Instead of representing states or categories with arbitrary numbers or text, you give them meaningful names, which makes the code more readable and safer.

### Example

Imagine you want to represent the status of an order: open, in progress, shipped, cancelled. Instead of using numbers like 0, 1, 2, 3, whose meaning you'd have to remember, you define an enum with exactly these four named values. In the code, an assignment then reads like "Status is Shipped" instead of "Status is 2" – much clearer.

```csharp
enum OrderStatus
{
    Open,
    InProgress,
    Shipped,
    Cancelled
}

OrderStatus status = OrderStatus.Shipped;

switch (status)
{
    case OrderStatus.Shipped:
        Console.WriteLine("The order is on its way.");
        break;
    case OrderStatus.Cancelled:
        Console.WriteLine("The order was cancelled.");
        break;
    default:
        Console.WriteLine("The order is being processed.");
        break;
}
```

### How does it work?

Internally, an enum stores each named value as an integer, starting at 0 for the first entry by default, with each subsequent value automatically increasing by 1. You can also set these underlying numbers yourself if needed. A variable of an enum type can only ever hold exactly one of the defined values, which rules out invalid states from the start – unlike a plain number or text, where theoretically any value would be possible.

### When should I use it?

* For a fixed, known set of possible states or categories
* To avoid "magic numbers" or text constants in the code
* To distinguish clearly and readably between cases in switch structures

### Common Mistakes

* Continuing to use plain numbers or strings for fixed categories instead of an enum
* Forgetting that every enum value has an underlying number, which can lead to unintended comparisons
* Defining too many, overly generic enums that actually mix up different concepts

### Practice

**Task:**
Define an enum for the four seasons. Then write a method that prints a fitting activity depending on the season passed in.

**Goal:**
After this exercise you should be able to explain why enums are more readable and safer than plain numbers for fixed categories.

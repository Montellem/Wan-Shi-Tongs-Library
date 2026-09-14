# Implicit Typing (var)
### What is it?

`var` lets the compiler infer the type of a local variable from the value assigned to it. The variable
is statically typed, the type is fixed at compile time, it just isn't written out explicity.

### Example
```c#
var accountNumber = ""DE89370400440532013000"; // inferred as string
var balance = 1259.75m                         // inferred as decimal
var account = new BankAccount(accountNumber, balance) // inferred as BankAccount

// The compiler locks in the type, this will not compile:
// balance = "not a number";
```

### How does it work?
The compiler looks at the right-hand side of the assignment and determines the type at compile time. From that point on,
`balance` behaves exactly like a `decimal` variable, `var` is purely a shorthand for the developer, not a dynamic or loosely typed variable
(that would be `dynamic`, a completely different feature).

`var` requires an initializer, since the compiler needs something to infer the type from:

```c#
// var x; // does not compile - no initializer to infer from
```

### When should I use it?
- When the type is obvious from the right-hand side (`var account = new BankAccount(..)`)
- With LINQ queries, where the result type can be long or anonymous (`var results = accounts.Where(...)`)
- To reduce repetition when the type name already appears in the `new` expression

### Common Mistakes
- Using `var` when the type is not obvious from context (e.g. `var result = ImportRow(line);`, what does this return?`Prefer an explicit type here for readability)
- Assuming `var` means "dynamic" or "loosely typed", it is fully static, just inferred
- Overusing `var` for numeric literals, where the exact type matters (`var x = 5` is `int`, but you may have needed `long` or `decimal`)

### Practice
**Task:** Write three local variable declarations using `var`: one for a `string`, one for a `decimal`, and one for a new `BankAccount` object. Then try 
assigning a value of the wrong type to one of them and observe the compiler error.

**Goal:** Understand that `var` is resolved at compile time and that the resulting variable is just as strongly typed as if you had written the type 
explicity.

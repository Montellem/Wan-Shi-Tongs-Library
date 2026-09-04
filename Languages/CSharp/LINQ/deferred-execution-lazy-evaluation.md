# Deferred Execution and Lazy Evaluation

## What is it?

Deferred execution means most LINQ queries are not actually run when you write them — they only execute when the result is enumerated (e.g., with `foreach`, `.ToList()`, or `.Count()`).

## Example

```csharp
List<BankAccount> accounts = new List<BankAccount>
{
    new BankAccount("Alice", 1500),
    new BankAccount("Bob", 300)
};

// No filtering happens yet — this just builds a query definition
var richAccounts = accounts.Where(a => a.Balance > 1000);

// Modify the source AFTER defining the query, but BEFORE enumerating it
accounts.Add(new BankAccount("Charlie", 4200));

// Only now does the query actually run — and it sees Charlie too!
foreach (var account in richAccounts)
{
    Console.WriteLine(account.Owner); // prints Alice AND Charlie
}
```

## How does it work?

Methods like `Where`, `Select`, and `OrderBy` return an object that stores the query definition (the source and the lambda expressions) rather than a computed result. The actual filtering/sorting/projecting logic only runs when something iterates over that object — a `foreach` loop, or a method that forces immediate evaluation like `.ToList()`, `.ToArray()`, `.Count()`, `.First()`, or `.Sum()`. Because of this, the same query variable can produce different results each time it's enumerated if the underlying source data changes in between.

## When should I use it?

* Understand this concept for every LINQ query you write — it's not something you opt into
* Use `.ToList()` or `.ToArray()` deliberately when you want to "snapshot" the results at a specific point in time, before the source might change
* Rely on deferred execution to build efficient query chains that only run once, at the very end, instead of materializing intermediate lists

## Common Mistakes

* Not realizing that a query re-runs every time it's enumerated — this can cause bugs (e.g., different results each `foreach`) and performance issues (e.g., re-querying a database each time)
* Modifying a collection while a query built from it is still being enumerated, causing an `InvalidOperationException` ("Collection was modified")
* Calling `.ToList()` too eagerly on every step of a chain, defeating the performance benefits of deferred execution
* Forgetting that with EF Core, deferred execution means the actual SQL query only runs when enumerated — logging/debugging tools that "peek" at a query can trigger unexpected database calls

## Practice

**Task:**
Write a LINQ query on a `List<Car>` using `Where`, then add a new car to the list before enumerating the query with `foreach`. Confirm whether the new car appears in the results. Then repeat the experiment, but call `.ToList()` immediately after defining the query, and add the new car afterward — compare the outcome.

**Goal:**
Be able to predict when a LINQ query actually executes, and use `.ToList()` deliberately to control that timing.

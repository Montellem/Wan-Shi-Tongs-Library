# Where (Filtering)
### What is it?
`Where` is a LINQ method that filters a sequence, returning only the elements that satisfy a given condition (a predicate).

### Example
```c#
List<BankAccount> accounts = new List<BankAccount>
{
  new BankAccount("Alice", 1500);
  new BankAccount("Bob", 300);
  new BankAccount("Charlie", 4200);
  new BankAccount("Dana", 15);
}

var activeAccounts = accounts.Where(a => a.Balance > 100);

// Multiple conditions combined
var richActiveAccounts = accounts.Where(a => a.Balance > 100 && a.Owner.StartsWith("A"));
```

### How does it work?
`Where` takes a `Func<T, bool>` a lambda expression that return `true` or `false` for each element. It walks through the source 
sequence one element at a time and yields only the elements for which the predicate return `true`. Because it uses deferred execution,
no filtering actually happens until the result is enumerated.

### When should I use it?
- Selecting a subset of collection based on a condition
- Replacing an `if` check-inside a manual `foreach` loop
- As the first step in a longer LINQ chain (filter, then sort, then select, etc.)
- Filtering imported data rows before further processing (e.g., skipping invalid rows from a `.txt` import)

### Common Mistakes
- Writing complex, unreadable multi-condition lambdas instead of extracting a names method or breaking the query into steps
- Forgetting that `Where` returns a new sequence, it does not modify the original collection
- Calling `.Where(...).First()` when `.First(predicate)` alone would be simpler and cleaner
- Not handling `null` values inside the predicate, causing a `NullReferenceException`

### Practice
**Task:** Given a `List<Car`, use `Where` to find all cars manufactured after 2015 that are not a "Ford". Print the results
**Goal:** Be comfortable writing predicates with multiple combined condistions insie `Where`.

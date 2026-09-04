# First, Single and ElementAt

## What is it?

These methods retrieve a single element from a sequence: `First`/`FirstOrDefault` get the first matching element, `Single`/`SingleOrDefault` require exactly one match, and `ElementAt` gets the element at a specific index.

## Example

```csharp
List<BankAccount> accounts = new List<BankAccount>
{
    new BankAccount("Alice", 1500),
    new BankAccount("Bob", 300),
    new BankAccount("Charlie", 4200)
};

BankAccount firstAccount = accounts.First();
BankAccount firstRich = accounts.First(a => a.Balance > 1000);
BankAccount? maybeAccount = accounts.FirstOrDefault(a => a.Owner == "Dana"); // null, no exception

BankAccount uniqueOwner = accounts.Single(a => a.Owner == "Bob"); // throws if 0 or 2+ matches
BankAccount thirdAccount = accounts.ElementAt(2);
```

## How does it work?

`First`/`FirstOrDefault` scan the sequence and stop as soon as they find a matching element (or the first element, if no predicate is given), making them efficient even on large sequences. `Single`/`SingleOrDefault` scan the entire sequence to guarantee there is exactly one match, throwing an exception if there are zero or more than one. The `OrDefault` variants return `default(T)` (typically `null` for reference types) instead of throwing when nothing matches. `ElementAt` retrieves by numeric position.

## When should I use it?

* `First`/`FirstOrDefault`: retrieving the top result of a sorted query, or safely checking whether something exists
* `Single`/`SingleOrDefault`: enforcing that a lookup (e.g., by unique ID) should return exactly one record — useful for catching data integrity bugs early
* `ElementAt`: rare, mainly when working with indexed access on a sequence that isn't already a `List<T>` or array

## Common Mistakes

* Using `First()` when the sequence could be empty — it throws an `InvalidOperationException`; use `FirstOrDefault()` and check for `null` instead
* Using `Single()` on a sequence that could realistically have duplicates, causing unexpected crashes in production
* Using `ElementAt()` on a large `IQueryable` (e.g., an EF Core query), which can be inefficient — prefer `Skip().Take()` for paging
* Forgetting to null-check the result of an `OrDefault` method before using it

## Practice

**Task:**
Given a `List<BankAccount>`, safely retrieve the account owned by "Dana" using `FirstOrDefault`, and print a friendly message if not found instead of crashing. Then use `Single` to retrieve the one account with a balance of exactly 300, and explain what would happen if two accounts had that same balance.

**Goal:**
Know which single-element method to use in which situation, and how to handle the "not found" case safely.

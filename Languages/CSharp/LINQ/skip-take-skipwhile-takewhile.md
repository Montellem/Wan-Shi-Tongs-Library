# Skip, Take, SkipWhile and TakeWhile

## What is it?

These methods partition a sequence by position or condition: `Skip`/`Take` work by a fixed count (useful for paging), while `SkipWhile`/`TakeWhile` work by a condition that's evaluated until it stops being true.

## Example

```csharp
List<BankAccount> accounts = new List<BankAccount>
{
    new BankAccount("Alice", 1500),
    new BankAccount("Bob", 300),
    new BankAccount("Charlie", 4200),
    new BankAccount("Dana", 50),
    new BankAccount("Eve", 900)
};

// Paging: skip the first 2, then take the next 2 (page 2 of a 2-item page size)
var page2 = accounts.Skip(2).Take(2);

var sortedByBalance = accounts.OrderByDescending(a => a.Balance).ToList();

// TakeWhile: take elements while balance stays above 1000 (stops at first failure)
var topSpenders = sortedByBalance.TakeWhile(a => a.Balance > 1000);

// SkipWhile: skip elements while balance stays above 1000, then take the rest
var restOfAccounts = sortedByBalance.SkipWhile(a => a.Balance > 1000);
```

## How does it work?

`Skip(n)` bypasses the first `n` elements and returns the rest; `Take(n)` returns only the first `n` elements. Both work purely by position, regardless of the elements' values. `TakeWhile` and `SkipWhile` instead evaluate a predicate against each element in order and stop as soon as the predicate returns `false` for the first time — they do **not** continue scanning to check later elements, even if some of them would also match.

## When should I use it?

* Paging results in a UI (e.g., a Blazor table with page size 25: `Skip((page-1) * 25).Take(25)`)
* Getting a "top N" slice from an already-sorted sequence with `Take`
* Processing a sequence only until a certain condition breaks (e.g., reading rows until an empty line is found) with `TakeWhile`
* Skipping a header/known-invalid prefix in imported data with `SkipWhile`

## Common Mistakes

* Confusing `TakeWhile`/`SkipWhile` (condition-based, stops at first failure) with `Where` (checks every element independently) — they are not interchangeable
* Using `Skip`/`Take` for paging directly on an `IQueryable` from EF Core without an `OrderBy` first — paging without a defined order gives inconsistent results
* Assuming `TakeWhile` scans the whole sequence — it stops immediately once the condition fails, even if later elements would have matched again

## Practice

**Task:**
Given a sorted `List<BankAccount>` (by balance descending), use `Take` to get the top 3 richest accounts. Then implement simple paging: given a page number and page size, return the correct slice using `Skip` and `Take`.

**Goal:**
Understand the difference between position-based partitioning (`Skip`/`Take`) and condition-based partitioning (`SkipWhile`/`TakeWhile`), and be able to implement paging.

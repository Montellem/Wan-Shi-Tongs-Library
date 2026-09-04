# Aggregation Methods (Sum, Count, Average, Min, Max)
### What is it?
Aggegation methods reduce a sequence down to a single value, a total, a count, an average, or an extreme value.

### Example

```c#
List<BankAccount> accounts = new List<BankAccount>
{
    new BankAccount("Alice", 1500),
    new BankAccount("Bob", 300),
    new BankAccount("Charlie", 4200)
};

decimal totalBalance = accounts.Sum(a => a.Balance);
int accountCount = accounts.Count();
int richCount = accounts.Count(a => a.Balance > 1000);
decimal averageBalance = accounts.Average(a => a.Balance);
decimal highestBalance = accounts.Max(a => a.Balance);
decimal lowestBalance = accounts.Min(a => a.Balance);
```

### How does it work?
Unlike `Where` or `Select`, aggregation methods do not return a sequence, they immediately execute and return a single value
(and `int`, `decimal`, etc.). This means they trigger execution right away, breaking deferred execution. `Sum`, `Average`, `Min` and `Max`
each accept an optional selector to specify which property to aggregate; `Count` can take an optional predicate to count only matching elements.

### When should I use it?
- Computing KPIs for a dashboard (total balance, average order value, number of active accounts)
- Validating data during import (e.g., checking that a total in a file matches the sum of its rows)
- Quick summary statistics without writing manual loops with accumulator variables

### Common Mistakes
- Calling `Average()`, `Min()`, or `Max()` on an empty sequence, which thrwos an `InvalidOperationException`, check `Any()` first, or use the nullable overloads where available
- Using `.Where(...).Count()` instead of the more efficient `.Count(predicate)`
- Summming over a very large EF Core query in memory instead of letting the aggregation translate to SQL on the database side.
- Confusing `Count()` (number of elemets) with `Sum()` (total of numeric property)

 ### Practice
 **Task:** Given a `List<BankAccount>`, compute and print: the total balance across all accounts, the number of accounts with a balance over 1000,
 and the average balance. Handle the case where the list might be empty.

**Goal:** Be comfortable using aggregation methods directly for common dashboard-style KPI calculations

- 

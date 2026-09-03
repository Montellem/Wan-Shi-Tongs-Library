# LINQ (Language Integrated Query)
### What is it?
LINQ is a set of features built into C# that lets you query, filter, and transform data, from collections, arrays, databases, or XML
using a consistent, readable syntax directly in your code, similar to SQL.

### Example
```c#
List<BankAccount> accounts = new List<BankAccount>
{
    new BankAccount("Alice", 1500),
    new BankAccount("Bob", 300),
    new BankAccount("Charlie", 4200)
};

// LINQ query: find all accounts with a balance over 1000
IEnumerable<BankAccount> richAccounts = accounts.Where(a => a.Balance > 1000);

foreach (var account in richAccounts)
{
    Console.WriteLine($"{account.Owner}: {account.Balance}");
}
```

### How does it work?
LINQ works through extension methods (like `Where`, `Select`, `OrderBy`) defined on `Enumerable<T>` in the `System.Linq` namespace. These methods take a 
lambda expression (a small inline function) and apply it to each element in the sequence. The result is itsel an `IEnumerable<T>`, so you can chain multiple
LINQ methods together. Nothing runs until you actually iterate over the result (e. g. with `foreach` or `.ToList()`) this is called deferred execution and is covered
in its own life.

### When should I use it?
- Filtering, sorting, or transforming collections instead of writing manual `for` / `foreach` loops
- Querying data from Entity Framework Core (e.g., your dashboard's database entities)
- Combining, grouping, or aggregating data (sums, counts, averages)
- Making data-processing code more declarative and readable

### Common Mistakes
- Forgetting to add `using System.Linq;` at the top of the file
- Assuming a LINQ query executes immediately, when it actually runs lazily on enumeration
- Enumerating the same query multiple times, causing it to re-run (and re-query the databse, if used with EF Core)
- Overusing LINQ for very simple loops where a plain `foreach` would be clearer

### Common Mistakes
- Forgetting to add `using System.Linq;` at the top of the file
- Assuming a LINQ query executes immediately, when it actually runs lazily on enumeration
- Enumerating the same query multiple times, causing it to re-run (and re-query the database, if used with EF Core)
- Overusing LINQ for very simple loops where a plain `foreach` would be clearer

### Practice
**Task:** Create a `List<BankAccount>` with at least five accounts of varying balances. Use LINQs `Where` method to find all
accounts with a balance below 500, and print the owner's name for each.

**Goal:** Unterstand the basic mental model of LINQ: aplling a method with a lambda expression to filter a sequence,
and iterating over the result.

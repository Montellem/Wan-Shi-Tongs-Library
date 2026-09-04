# IEnumerable vs. IQueryable

## What is it?

`IEnumerable<T>` represents a sequence that is queried in memory, one element at a time. `IQueryable<T>` represents a sequence whose query can be translated and executed elsewhere — most commonly, translated into SQL and executed by a database, as with Entity Framework Core.

## Example

```csharp
// IEnumerable: works on data already in memory (e.g., a List<T>)
IEnumerable<BankAccount> inMemoryAccounts = accounts; // accounts is a List<BankAccount>
var richInMemory = inMemoryAccounts.Where(a => a.Balance > 1000); // filtered in C#, in memory

// IQueryable: works on a data source that can translate the query (e.g., EF Core DbSet)
IQueryable<BankAccount> dbAccounts = dbContext.BankAccounts; // DbSet<T> implements IQueryable<T>
var richInDb = dbAccounts.Where(a => a.Balance > 1000); // translated into a SQL WHERE clause

// Executing (enumerating) triggers the actual SQL query:
var results = richInDb.ToList(); // SELECT * FROM BankAccounts WHERE Balance > 1000
```

## How does it work?

`IQueryable<T>` builds an *expression tree* instead of directly running your lambda code — it represents the query as data, which a query provider (like EF Core's SQL provider) can translate into another language such as SQL. `IEnumerable<T>`, in contrast, always executes lambdas as ordinary compiled C# code, in memory, on whatever has already been loaded. Both support the same LINQ methods (`Where`, `Select`, `OrderBy`, etc.) and both use deferred execution, but the crucial difference is *where* the filtering logic actually runs.

## When should I use it?

* Keep queries as `IQueryable` for as long as possible when working with EF Core, so filtering/sorting/paging happens in the database — this is far more efficient than loading everything into memory first
* Switch to `IEnumerable` (e.g., after `.ToList()` or `.AsEnumerable()`) only once you need C#-specific logic that can't be translated to SQL (custom methods, complex string formatting, etc.)
* Understand this distinction when designing the dashboard's data-access layer, especially for KPI queries that should be computed by SQLite, not by loading full tables into Blazor Server memory

## Common Mistakes

* Calling `.ToList()` too early on an EF Core query, then applying `Where`/`OrderBy` afterward — this forces the entire table to load into memory before filtering, instead of letting the database do the work
* Using a C# method or property inside a `Where` clause on an `IQueryable` that EF Core cannot translate to SQL, causing a runtime exception (or, in older EF versions, a silent full in-memory evaluation)
* Assuming `IQueryable` and `IEnumerable` always behave identically — the same-looking code can produce different performance characteristics, and occasionally different results, depending on which one is used
* Not being aware that once you call `.ToList()`, you've left `IQueryable` behind and any further chained methods now run in memory

## Practice

**Task:**
Write a method that accepts an `IQueryable<BankAccount>` and filters it by minimum balance. Then write a second version using `IEnumerable<BankAccount>` with a `List<BankAccount>` as input. Explain, in a comment, where the filtering logic actually executes in each case, and why this matters for a database-backed dashboard with potentially thousands of rows.

**Goal:**
Be able to explain the practical difference between `IEnumerable` and `IQueryable`, and make deliberate choices about where filtering logic should run in a database-backed application.

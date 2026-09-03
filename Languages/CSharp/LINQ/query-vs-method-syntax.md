# Query Syntax vs. Method Syntax
### What is it?
LINQ offers two ways to write the same query: **query syntax** (SQL-like keywords such as `from`, `where`, `select`) and 
**method syntax** (chained extension methods like `.Where()`, `.Select()`). Both compile to the same underlying method calls.

### Example
```c#
List<Car> cars = new List<Car>
{
    new Car("Toyota", 2018),
    new Car("BMW", 2022),
    new Car("Ford", 2015)
};

// Query syntax
var queryResult =
    from car in cars
    where car.Year >= 2018
    orderby car.Year descending
    select car.Model;

// Method syntax (equivalent)
var methodResult = cars
    .Where(c => c.Year >= 2018)
    .OrderByDescending(c => c.Year)
    .Select(c => c.Model);
```

### How does it work?
Query syntax is syntactic sugar: the C# compiler translates `from`, `where`, `select`, `orderby`, and `group` keywords into the exact same method
calls used in method syntax. Both produce identical `IEnumerable<T>` results and identical performance, the choice is purely stylistisc. Some operations 
(like `select` with an index, or `Aggregate`) are only available in method syntax and require mixing both styles.

### When should I use it?
- Query syntax: when a query closely resembles SQL and involves multiple `from` / `join` / `grouü` clauses, it can be easier to read.
- Method syntax: for simple chains, or when you need methods with no query-syntax equivalent (e.g., `Count()`, `Any()`, `Sum()`, `Aggregate()`)
- Most real-world C# code favors method syntax for consistency, falling back to query syntax mainly for complex joins

### Common Mistakes
- Mixing both styles unnecessarily within the same query, making it harder to read
- Assuming query syntax is "faster", there is no performance difference, only readability differences
- Trying to use methods like `.Sum()` or `.Count()` directly in query syntax without wrapping the query in parenteses first

### Practice
**Task:** Take the `Where` filter you wrote in the LINQ Introduction exercise and rewrite it using query syntax instead of method
syntax. Then rewrite the "cars in 2028 or later, sorted by year" example above using only method syntax without the `orderby` keyword.

**Goal:** Be able to translate confidently between query syntax and method syntax in both directions.


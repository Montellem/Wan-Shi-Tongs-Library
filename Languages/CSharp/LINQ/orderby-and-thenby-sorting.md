# OrderBy and ThenBy (Sorting)
### What is it?
`OrderBy` and `OrderByDescending` sort a sequence by a key. `ThenBy` and `ThenByDescending` add secondary sort levels for elements that share
the same primary key.

### Example
```c#
List<Car> cars = new List<Car>
{
    new Car("Toyota", 2018),
    new Car("BMW", 2022),
    new Car("Ford", 2018),
    new Car("Audi", 2015)
};

// Sort by year ascending, then by model name alphabetically
var sorted = cars
    .OrderBy(c => c.Year)
    .ThenBy(c => c.Model);

// Sort by year descending
var newestFirst = cars.OrderByDescending(c => c.Year);
```

### How does it work?
`OrderBy` takes a key selector (a lambda that returns the value to sort by) and returns an `IOrderedEnumerable<T>`. This special
return type is what allows `ThenBy` to be chained afterward, `ThenBy` only makes sense after an initial `OrderBy`. Internally, LINQ 
performs a stable sort, meaning elements with equal keys keep their original relative order unless a `ThenBy` breaks the tie.

### When should I use it?
- Displaying data in a specific order (e.g. accounts sorted by balance for a dashboard table)
- Multi-level-sorting, such as sorting cars by year, then by model within the same year.
- Preparing data before pagination (`Skip`/ `Take`) or before showing top-N results

### Common Mistakes
- Calling `.OrderBy(...).OrderBy(...)` instead of `.OrderBy(...).ThenBy(...)`, the second `OrderBy` overrides the first sort instead of adding a secondary level
- Forgetting `OrderByDescending` exists and manually reversing a list with `.Reverse()` afterward instead.
- Sorting a large collection multiple times in a loop instead of sorting once and reusing the result.

### Practice
**Task:** Given a `List<BankAccount>`, sort the accounts by balance descending. Then, given a `List<Car>` with several cars sharing the same year, sort
them by year ascending and, for cars in the same year, by model name alphabetically.

**Goal:** Be able to build multi-level sorts using `OrderBy` combined with `ThenBy`.

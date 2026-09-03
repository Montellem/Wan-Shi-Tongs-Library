# GroupBy
### What is it?
`GroupBy` organizes the elements of a sequence into groups based on a key, similar to a SQL `GROUP BY` clause. Each group is itself a sequence of the elements 
that share that key.

### Example
```c#
List<Car> cars = new List<Car>
{
    new Car("Toyota", 2018),
    new Car("Toyota", 2020),
    new Car("BMW", 2022),
    new Car("Ford", 2018)
};

var groupedByBrand = cars.GroupBy(c => c.Model);

foreach (var group in groupedByBrand)
{
    Console.WriteLine($"Brand: {group.Key}, Count: {group.Count()}");
    foreach (var car in group)
    {
        Console.WriteLine($"  - {car.Year}");
    }
}
```

### How does it work?
`GroupBy` takes a key selector and returns an `IEnumerable<IGrouping<Tkey,TElement>>`. Each `IGrouping?` has a `key` propterty (the grouping value)
and behaves like an `IEnumerable<IElement>` containing all elements that share that key. LINQ builds these groups by iterating the source once 
and bucketing elements by their key.

### When should I use it?
- Summarizing or aggregating data by category (e.g., total balance per branch, car count per brand)
- Building grouped views for a dashboard (KPI breakdowns per group)
- Preparing data for charts that need categorized series (e.g., Radzen.Blazor charts grouped by product group)

### Common Mistakes
- Forgetting that the result of `GroupBy` is a sequence of groups, not a flat list, you often need a further `Select` to reshape it
- Calling `.ToList()` on the source before grouping unnecessarily, adding overhead for large collections
- Using `GroupBy` with Entity Framework Core queries in ways that f orce the query to run in memory instead of translating to SQL - always verify complex grouped queries against the database
- Confusing `group.key` with `group.First()`


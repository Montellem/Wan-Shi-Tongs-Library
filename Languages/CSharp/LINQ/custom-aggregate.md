# Aggregate (Custom Aggregation)
### What is it?
`Aggregate` is a genera-purpose LINQ Method that applies an accumulator function over a sequence, building up a single result
step by step, useful when built-in methods like `Sum` or `Count` aren't enough.

### Example
```c#
List<Car> cars = new List<Car>
{
    new Car("Toyota", 2018),
    new Car("BMW", 2022),
    new Car("Ford", 2015)
};

// Build a comma-separated string of all model names
string modelList = cars.Aggregate(
    "",
    (accumulated, car) => accumulated == "" ? car.Model : accumulated + ", " + car.Model
);

// Find the newest car manually using Aggregate instead of MaxBy
Car newestCar = cars.Aggregate((newest, current) => current.Year > newest.Year ? current : newest);
```

### How does it work?
`Aggregate` takes an accumulator function that receives the running result so far and the current element, and returns the new running result.
Optionally, you can provide a seed value (the starting accumulator) as the first argument. Without a seed, the first element of the sequence
is used as the starting value. LINQ calls the accumulator function once per remaining element, carrying the result forward each time.

### When should I use it?
- Building a custom aggregation that has no dedicated LINQ method (e.g., concatenating strings, computing a product, building a custom summary object)
- Reducing a sequence to a single complex object step by step
- As a learning tool to understand how `Sum`, `Count`, and similar methods work internally

### Common Mistakes
- Reaching for `Aggregate` when a simpler, dedicated method (`Sum`, `Max`, `Count`) already does the job, those are clearer and often faster
- Forgetting to provide a seed value on a sequence that might be empty, which throws an exception (there is no "first element" to start from)
- Writing an accumulator function with side effects instead of a pure calculation, making the code harder to reason about.

### Practice
**Task:** Given a `List<BankAccount>`, use `Aggregate` (with a seed of `0m`) to manually compute the total balance, without using
`Sum`. Then use `Aggregate` to find the account with the highes balance without using `Max` or `OrderByDescending`.

**Goal:** Understand how `Aggregate` works as the general building block behind many other LINQ aggregation methods.

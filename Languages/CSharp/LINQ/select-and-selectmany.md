# Select and SelectMany (Projection)
### What is it?
`Select` transforms (projects) each element of a sequence into a new form. `SelectMany` does the same, but flattens a sequence
of sequences into a single, flat sequence.

### Example
```c#
List<BankAccount> accounts = new List<BankAccount>
{
  new BankAccount("Alice", 1500),
  new BankAccount("Bob", 300)

};

// Select: project each account to just its owner name
IEnumerable<string> owners = accounts.Select(a => a.Owner);

// Select: project into an anonymous type with computed data
var sumamries = accounts.Select(a =A new { a.Owner, isRich = a.Balance > 1000});

// SelectMany: flatten a list of lists into a single list
List<List<Car>> fleetsByBranch = new List<List<Car>>
{
  new List<Car> { new Car("Toyota", 2018) },
  new List<Car> { new Car("BMW", 2022), new Car("Ford", 2015) }
};

IEnumerable<Car> allCars = fleetsByBranch.SelectMany(fleet => fleet);
```

### How does it work?
`Select` takes a `Func<T, TResult>` and applies it to every element, producing a new sequence of `TResult`. The number of output elements always matches
the number of input elements. `SelectMany` instead excepts the lambda to return a sequence for each element, then concatenates all those sequences into one flat
result, useful when each source item contains a nested collection

### When should I use it?
- Transforming objects into a different shape (e.g., extracting a single property, or building a DTO/ anonymous type)
- Preparing data for display(e.g., mapping entities to view models for a Blazor component)
- Flattening nested collections, such as a list of orders each containing a list of items
- Combining with `Where` to filter and reshape data in one chain

### Common Mistakes
- Using `Select` when you actually have nested collections and need `SelectMany` this results in a collection of collections instead of a flat list.
- Doing heavy computation inside `Select` that would be beeter placed in a separate, named method for readability
- Forgetting that `Select` produces a new sequence and does not mutate the source objects

### Pracitce
**Task:** Given `List<BankAccount>`, use `Select` to project each account into an anonymous object containing `Owner` and a `Status` ("Active" if balance > 0,
otherwise "Empty"). Then create a `List<List<BankAccount>>` (grouped by branch) amd use `SelectMany` to flatten it into one list.

**Goal:** Understand the difference between one-to-one projection (`Select`) and flattening nested sequences (`SelectMany`).

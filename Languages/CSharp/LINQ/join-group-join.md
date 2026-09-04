# Join and GroupJoin
### What is it?
`Join` combines two sequences based on matching keys, similar to a SQL inner join, producing one outpot row per
mactching par. `GoupJoin` is similar but groups all matches from the second sequence under each element of the first,
similar to a SQL leftjoint with grouping.

### Example
```c#
List<BankAccount> accounts = new List<BankAccount>
{
    new BankAccount("Alice", 1500) { BranchId = 1 },
    new BankAccount("Bob", 300) { BranchId = 2 }
};

List<Branch> branches = new List<Branch>
{
    new Branch(1, "Nuremberg"),
    new Branch(2, "Munich")
};

// Join: one flat row per matching pair
var joined = accounts.Join(
    branches,
    account => account.BranchId,
    branch => branch.Id,
    (account, branch) => new { account.Owner, BranchName = branch.Name }
);

// GroupJoin: each branch with its list of accounts
var grouped = branches.GroupJoin(
    accounts,
    branch => branch.Id,
    account => account.BranchId,
    (branch, accountsInBranch) => new { branch.Name, Accounts = accountsInBranch }
);
```

### How does it work?
`Join` takes the outer sequence, the inner sequence, a key selector for each side, and a result selector.
It matches elements where the outer key equals the inner key and produces one result per match, elements
with no match are excluded entirely, like an inner join. `GroupJoin` instead produces one result per outer element,
with a nested sequence of all matching inner elements (which may be empty), similar to a left join followed by grouping.

### When should I use it?
- Comgining data from two related in-memory collections (e.g., accounts and branches, or imported rows and lookup tables)
- Replicating relational joins when not querying dircetly through EF Core navigation properties
- Building nested view models where each parent needs its related children grouped underneath it

### Common Mistakes
- Using `Join` / `GroupJoin` on in-memory collections when EF Core navigation properties (`.Include()`) would already provide the related data more efficently
- Forgetting that `Join` silently drops outer elements with no match, use `GroupJoin` (or a `DefaultIfEmpty`) if unmatched elements should still appear.
- Mismatched key types (e.g., comparing an `int` key to a `string` key) causing no matches at all

### Practice
**Task:** Given a `List<Car>` and a `List<Owner>` (each car has an `OwnerId`), use `Join` to produce a flat list of "Owner drives Car" strings.
Then use `GroupJoin` ro produce, for each owner, a list of all cars they own (including owners with zero cars).

**Goal:** Understand when to use `Join` for flat matched paris versus `GroupJoin` for grouped, one-to-many relationships.

# Dictionary<TKey, TValue>

### What is it?

A Dictionary<TKey, TValue> is a collection of key-value pairs, where each key is unique and maps to exactly one value. Instead of looking up an element by a numeric index like in an array or list, you look it up by its key, which makes retrieval very fast and intuitive when data naturally has a unique identifier.

### Example

```csharp
var ages = new Dictionary<string, int>
{
    { "Anna", 25 },
    { "Ben", 30 }
};

ages["Clara"] = 28; // add a new entry
ages["Anna"] = 26;  // update an existing entry

if (ages.TryGetValue("Ben", out int bensAge))
{
    Console.WriteLine($"Ben is {bensAge} years old.");
}

foreach (var pair in ages)
{
    Console.WriteLine($"{pair.Key}: {pair.Value}");
}
```

### How does it work?

Internally, a Dictionary uses a hash table: each key is converted into a hash code that determines where its value is stored, which is what makes lookups, insertions, and deletions very fast on average, regardless of how many entries the dictionary holds. Keys must be unique — assigning a value to an existing key overwrites the old value rather than creating a duplicate entry. Trying to access a key that doesn't exist throws an exception, which is why TryGetValue is the safer way to check for a key's presence and retrieve its value in one step.

### When should I use it?

* When you need to look up values by a unique identifier (e.g. username, product ID)
* When you want fast lookups regardless of collection size
* When your data is naturally structured as pairs of related information

### Common Mistakes

* Accessing a key directly with the indexer without checking whether it exists first, causing a crash
* Assuming dictionary entries keep insertion order (they generally don't guarantee it)
* Using a mutable object as a key, which can break lookups if the object changes after being added

### Practice

**Task:**
Create a dictionary that maps three product names to their prices. Look up one product's price safely using TryGetValue, then print all products and prices.

**Goal:**
After this exercise you should be able to confidently add, update, and safely look up values in a Dictionary<TKey, TValue>.

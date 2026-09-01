# List<T>
### What is it?

A List<T> is a dynamically sized, ordered collection of elements of the same type. Unlike an array,
its size isn't fixed. It grows and shrinks automatically as you add or remove elements.
It's part of C#'s generic collections, meaning you specify the element type once
(e.g. List<string>) and the compiler enforces it everywhere.

### Example
```c#
var names = new List<string> { "Anna", "Ben", "Clara" };
names.Add("David");
names.Remove("Ben");

foreach (var name in name)
{
  Console.WriteLine(name);
}

Console.WriteLine($"Count: {count.Count}");
```

### How does it work?
Internally, a List<T> is backed by an array. When you add an element and the internal array is full,
the list automatically allocates a larger array behind the scenes and copies the existing elements over,
you never have to manage this yourself. Elements can be accessed by index, just like an array, but you also get 
built-in methods for adding, removing, searching, and sorting. Because it's generic, only elements of the declared type
can be stored, which avoids the type-casting, issues older non-generic collections had.

### When should I use it?
- When you need an ordered collection whose size isn't known in advance
- When you need to frequently add or remove elements
- When you want index-based access combined with convernient built-in operations (sorting, searching, filtering)

### Common Mistakes
- Modifying a list while iterating over it with foreach, which throws a runtime error
- Using a List<T> when a Dictionary would be a better fit for key-based lookups
- Repeatedly checking ```Contains``` on a large list in a loop, which is slow a HashSet is often better for that.

### Practice
**Task:** Create a list of five favorite movies. Add one more movie, remove one, then print the final list along with its count.

**Goal:** After the exercise you should be able to confidently add, remove, and iterate over a List<T>, and understand how it differs froma  fixed-size array.

# HashSet<T>
### What is it?
A HashSet<T> is a collection that stores unique elements only, no duplicates are allowed. Unlike
a List, it doesn't preserve insertion order and doensn't support index-based access, but it offers
very fast membership checks (does this element exist in the collection?) regardless of how many elements it contains.

### Example
```c#
var uniqueTags = new HashSet<string> {"csharp", "beginner", "tutorial"};

bool added = uniqueTags.Add("csharp"); //false, already exists
Console.WriteLine(added); // false

uniqueTags.Add("dotnet"); // true, gets added

bool hasTag = uniqueTags.Contains("beginner"); // very fast check
Console.WriteLine(hasTag);

var setA = new HashSet<int> {1, 2, 3};
var setB = new HashSet<int> {2, 3, 4];
setA.IntersactWith(setB); // setA now contains {2, 3}
```

### How does it work?
Like a Dictionary, a HashSet uses a ahash table internally: each element's hash code determines its storagfe
location, which is what makes checking whether an element already exists extremely fast, without having to ocmpare it against every other 
element one by one. Trying to add an element that's already present simply does nothing and return false,
rather than adding a duplicate. HashSet also provides built-in set operations like union, intersection, and difference, which mirror mathematical set theory.

### When should I use it?
- When you need to gurantee that a collection contains a duplicates
- When you frequently need to check whether an element is already present
- When you need mathematical set operations like union, intersection,, or difference

### Common Mistakes
- Relying on any particular order when iterating a HashSet, since order isn't guranteed
- Trying to access elements by index, which HashSet doesn't support
- Using a HashSet when you actually need to track how many times each element occurs (a Dictionary<T,int> would fit better there)

### Practice
**Task:** Build a HashSet of tags from a list of blog post tags that contains duplicates, then print the resulting unique set and its count.
**Goal:** After this exercise you should be able to explain when a HashSet is a better fit than a List, and use basic set operations Like IntersectWith or UnionWith.

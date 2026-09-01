# Arrays

### What is it?

An array is a fixed, ordered collection of values of the same data type, stored under one shared name. Each element in the array has a fixed position, addressed via an index. An array's size is fixed when it's created and can't be changed afterward.

### Example

Imagine you want to store the days of the week. Instead of creating seven separate variables, you create an array with seven slots and fill each slot with a day of the week. Using the index (starting at 0), you can access a specific day directly, such as the first entry for "Monday".

```csharp
string[] weekdays = { "Monday", "Tuesday", "Wednesday", "Thursday", "Friday" };

Console.WriteLine(weekdays[0]); // "Monday"

int[] numbers = { 4, 8, 15, 16, 23 };
int sum = 0;
foreach (var number in numbers)
{
    sum += number;
}
Console.WriteLine($"Sum: {sum}");
```

### How does it work?

When an array is created, it reserves one contiguous block of memory for exactly as many elements as specified. Accessing an element by index is therefore very fast, since the program can jump directly to the right memory location. The first index is always 0, and the last one equals the number of elements minus 1. Accessing an index outside this valid range throws a runtime error. Because the size is fixed, you need to know (or at least reasonably estimate) how many elements you'll need when creating an array.

### When should I use it?

* When you want to store a fixed, known number of values of the same type
* When fast index-based access matters
* As a foundation before moving on to more flexible collections like lists

### Common Mistakes

* Accessing an index outside the valid bounds (off-by-one errors)
* Trying to change an array's size afterward, even though arrays have a fixed length
* Forgetting that the first index is 0, not 1

### Practice

**Task:**
Create an array of five numbers, then calculate their sum and average by looping through the array.

**Goal:**
After this exercise you should be able to create arrays, loop through them, and access individual elements by index.****

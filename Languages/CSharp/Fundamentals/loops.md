# Loops (for, while, do-while, foreach)

### What is it?

Loops repeat a block of code until a certain condition is no longer met, or once for each element of a collection. C# offers four variants: for, while, do-while, and foreach, each suited to different situations.

### Example

Imagine you want to print the numbers from 1 to 10. With a for loop, you set up a counter that starts at 1, increases by 1 after each pass, and stops the loop once it exceeds 10. If instead you want to print every name in a list without worrying about a counter, a foreach loop fits better: it automatically walks through each element of the list.

```csharp
for (int i = 1; i <= 10; i++)
{
    Console.WriteLine(i);
}

var names = new List<string> { "Anna", "Ben", "Clara" };
foreach (var name in names)
{
    Console.WriteLine(name);
}

int counter = 0;
while (counter < 5)
{
    Console.WriteLine(counter);
    counter++;
}
```

### How does it work?

The for loop is suited when the number of iterations is known in advance or controlled by a counter. The while loop checks its condition before each iteration and is suited when it's unclear how many times the loop needs to run. The do-while loop works similarly, but checks its condition only after the first iteration, so the code block always runs at least once. The foreach loop automatically walks through each element of a collection like a list or an array, without you having to manage a counter manually.

### When should I use it?

* for, when the number of repetitions is known in advance
* while, when the repetition depends on a condition that changes at runtime
* do-while, when the code block must run at least once no matter what the condition says
* foreach, to process every element of a collection

### Common Mistakes

* Creating an infinite loop because the stopping condition is never met
* Initializing or incrementing the counter in a for loop incorrectly (off-by-one errors)
* Trying to modify the collection being iterated inside a foreach loop

### Practice

**Task:**
Write a small program that prints the numbers from 1 to 20, but only shows the even numbers. Solve it first with a for loop, then with a while loop.

**Goal:**
After this exercise you should be able to explain which loop type fits best in which situation, and avoid common mistakes like infinite loops.

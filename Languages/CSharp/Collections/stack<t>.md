# Stack<T>

### What is it?

A Stack<T> is a collection that follows the LIFO principle — Last In, First Out. The last element you add is the first one you get back out, like a stack of plates: you take the top plate off first, which is also the one that was placed there most recently.

### Example

```csharp
var browserHistory = new Stack<string>();

browserHistory.Push("home.html");
browserHistory.Push("products.html");
browserHistory.Push("checkout.html");

string lastPage = browserHistory.Pop(); // "checkout.html"
Console.WriteLine($"Going back from: {lastPage}");

string current = browserHistory.Peek(); // "products.html"
Console.WriteLine($"Current page: {current}");
```

### How does it work?

New elements are added to the top of the stack with Push, and elements are removed from the top with Pop, which also returns the removed element. Peek lets you check the top element without removing it. Because only the top of the stack is accessible, you can't reach into the middle or bottom without first removing everything above it.

### When should I use it?

* When you need to reverse the order of processing (last added, first handled)
* For undo/redo functionality or browser back-navigation
* For algorithms that naturally involve backtracking, like parsing nested expressions

### Common Mistakes

* Calling Pop or Peek on an empty stack, which throws an exception
* Using a Stack when the actual requirement is first-in-first-out order (that calls for a Queue instead)
* Assuming you can access an element in the middle of the stack directly

### Practice

**Task:**
Simulate an undo feature for a text editor: push four actions onto a stack, then pop and print them one by one to show the order they'd be undone in.

**Goal:**
After this exercise you should be able to explain the LIFO principle and confidently use Push, Pop, and Peek.

# Queue<T>

### What is it?

A Queue<T> is a collection that follows the FIFO principle — First In, First Out. Elements are added at one end and removed from the other, meaning the first element you add is always the first one you get back out, just like a real-world line of people waiting.

### Example

```csharp
var printJobs = new Queue<string>();

printJobs.Enqueue("Document1.pdf");
printJobs.Enqueue("Document2.pdf");
printJobs.Enqueue("Document3.pdf");

string nextJob = printJobs.Dequeue(); // "Document1.pdf"
Console.WriteLine($"Now printing: {nextJob}");

string upNext = printJobs.Peek(); // look without removing
Console.WriteLine($"Up next: {upNext}");
```

### How does it work?

New elements are added to the back of the queue with Enqueue, and elements are removed from the front with Dequeue, which also returns the removed element. Peek lets you look at the next element without removing it. Because the queue strictly enforces first-in-first-out order, you can never grab an element out of order or access one in the middle directly — you can only process elements as they reach the front.

### When should I use it?

* When you need to process items in the exact order they arrived
* For task queues, print queues, or message queues
* When simulating waiting lines or buffering incoming work

### Common Mistakes

* Calling Dequeue or Peek on an empty queue, which throws an exception
* Expecting random or index-based access, which a queue doesn't support
* Using a Queue when you actually need last-in-first-out behavior (that's what a Stack is for)

### Practice

**Task:**
Simulate a customer service line: enqueue four customer names, then dequeue and print them one by one in the order they'll be served.

**Goal:**
After this exercise you should be able to explain the FIFO principle and confidently use Enqueue, Dequeue, and Peek.****

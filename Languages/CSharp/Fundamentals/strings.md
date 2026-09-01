# Strings

### What is it?

A string is a sequence of characters, i.e. a chain of letters, numbers, and special characters. Strings are among the most commonly used data types, since almost every piece of text output or processing relies on them. Important to know: strings in C# are immutable – every "change" actually creates a new string.

### Example

Picture a variable holding the text "Hello World". If you want to pull out just the word "Hello", convert the text to uppercase, or join two texts together, the string type provides dedicated built-in methods for each of these, and each one produces a new string as the result instead of altering the original text.

```csharp
string text = "Hello World";

string firstWord = text.Substring(0, 5);   // "Hello"
string uppercase = text.ToUpper();         // "HELLO WORLD"
string joined = text + "!";                // a new string

bool equal = "Hello".Equals("hello", StringComparison.OrdinalIgnoreCase);
```

### How does it work?

A string internally consists of a sequence of individual char values. Because strings are immutable, every method that appears to modify the text (e.g. replacing, trimming, changing case) actually produces an entirely new string in memory – the original stays untouched unless you overwrite it. For comparing text, you should use the dedicated comparison methods rather than a simple equality check, especially if case should be ignored. For joining many pieces of text together in a loop, there are also more efficient tools than plain concatenation, since the latter creates unnecessary intermediate objects when repeated many times.

### When should I use it?

* For any kind of text handling: names, messages, user input
* To format, search, or split text
* To build readable output for the user

### Common Mistakes

* Comparing strings with the equality operator without considering case sensitivity and edge cases
* Assuming a "modifying" method actually changes the original string, instead of assigning the result to a new variable
* Inefficiently concatenating many pieces of text in a loop instead of using a tool designed for that

### Practice

**Task:**
Take a full name (first and last name as one piece of text) and print the first and last name separately, in uppercase.

**Goal:**
After this exercise you should be able to confidently apply basic string operations like splitting, converting, and joining, and understand why strings are immutable.

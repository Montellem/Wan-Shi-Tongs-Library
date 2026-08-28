# Variables and Data Types
### What is it?

A variable is a names storage location in memory that holds a value. C# is a strongly typed language,
meaning every variable is assigned to a fixed data type when it's created, and that type determines
what kind of values it can hold and how much memory it takes up.

The most important built-in data types are:
- **int** - whole numbers (e.g. 5,-12,1000)
- **double** - decimal numbers with high precision
- **bool** - truth values (true of false)
- **char** - a single character
- **string** - a sequence of characters (text)

### Example 
Imagine a program that asks the user for their name. It first prints a prompt to the console,
then waits until the user types something and confirms it with Ente, and finally prints a 
personal greeting containing the entered name.

```c#
Console.Write("What's your name? ")
string name = Console.ReadLine()

Console.Write("How old are you? ")
int age = int.Parse(Console.ReadLine());

Console.WriteLine($"Hello {name}, you are {age} years old!");
```

### How does it work?
Output to the console happens through a method that displays the given test on screen,
either with or without a trailling line break. Input is captured through a method that waits until the user types a line and
confirms it, always returning that input as text (string), even if the user typed a number, it must be converted to a numeric-type
first if needed. For formatted output, where variable values need to be embedded into a piece of text, there's a special
syntax that makes the text more readable than plain concatenation.

### When should I use it?
- While learning and testing, to quickly make results visible
- For simple command-line programs without a graphical interface
- To print intermediate values for debugging during development

### Common Mistakes
- Forgetting that console input always arrives as text, and trying to calculate with it directly without converting it.
- Not validating input at all, even though the user could type invalid text instead of the expected number
- Assembling output and embedded values messily with many separate pieces of text instead of using the dedicated formatting syntax

### Practice
**Task:** Write a small program that asks the user for their name and age, then prints a formatted greeting containing both values.
**Goal:** After this exercise you should be able to confidently print text, accept user input and convert it to the appropriate data type.


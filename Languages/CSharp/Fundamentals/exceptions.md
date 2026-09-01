# Exceptions (Error Handling)

### What is it?

An exception is a signal that an unexpected error occurred while a program was running, interrupting its normal flow. With try/catch/finally, you can catch and handle such errors deliberately instead of letting the whole program crash.

### Example

Imagine a program that's supposed to divide a number by a second number entered by the user. If the user enters 0 as the divisor, the program would crash without error handling. If you wrap the division in a try block and catch the corresponding error in a catch block, you can instead print an understandable error message and let the program keep running normally.

```csharp
try
{
    Console.Write("Please enter a number: ");
    string input = Console.ReadLine();
    int divisor = int.Parse(input);
    int result = 100 / divisor;
    Console.WriteLine($"Result: {result}");
}
catch (FormatException)
{
    Console.WriteLine("That wasn't a valid number.");
}
catch (DivideByZeroException)
{
    Console.WriteLine("Division by zero isn't allowed.");
}
finally
{
    Console.WriteLine("Processing complete.");
}

// Custom exception
class InvalidAgeException : Exception
{
    public InvalidAgeException(string message) : base(message) { }
}
```

### How does it work?

Code that might produce an error goes inside the try block. If an error occurs there, the rest of the try block is immediately abandoned and control jumps to the matching catch block that handles that particular kind of error. An optional finally block always runs, regardless of whether an error occurred or not – ideal for cleanup work. You can also define your own exception types by inheriting from the built-in base exception class, to clearly name application-specific error kinds, and trigger these errors yourself with throw whenever your own code detects an unexpected situation.

## When should I use it?

* For operations that depend on outside factors and can fail (user input, file access, network connections)
* To let the program respond to an error in a controlled way instead of crashing
* Custom exceptions, to clearly distinguish business-logic errors in your own code from technical errors

### Common Mistakes

* Using try/catch to simply "swallow" errors without handling or logging them in any meaningful way
* Misusing exceptions for normal, expected control flow instead of limiting them to real error cases
* Using an overly broad catch block that also catches errors that should actually stay unnoticed

### Practice

**Task:**
Write a small program that reads two numbers from the user and divides the first by the second. Catch both the error that occurs on invalid numeric input and the error that occurs on division by zero, printing a fitting message for each.

**Goal:**
After this exercise you should be able to confidently use try/catch/finally and understand when a custom exception class is worthwhile.

# Type Conversion
### What is it?
Type conversion means turning a valie pf one data type into another. This is necessary because
C# is strongly typed and doesn't automatically switch between all types. There's a distinction
between implicit (automatic) and explicit (manual) conversion.

### Example
Picture an int variable holding the value 10. If you assign this avlue to a double variable, it
happens automatically (implicitly), because no information is lost, 10 simply becomes 10.0.
Conversely, if you want to assign a dobule variable holding 9.7 to ayn int variable, you have
to do it explicitly via a cast, because the decimal part would be lost and you must confirm
to the compiler that you accept this loss of information.

```c#
int number = 10;
double asDouble = number; //implicit, no data loss

double decimalValue = 9.7;
int asInt = (int)decimalValue; //explicit, decimal part is lost

string input = "42";
bool success = int.TryParse(input, out int result)

if (success)
{
  Console.WriteLine($"Converted: {result}");
}
```

### How does it work?
Implicit conversions happen automatically whenever no data can be lost (e.g. from int to double). Explicit
conversions (casting) must be requested by the developer whenever data loss is possible (e.g. from double to int), the compiler 
requires this as a safety measure. There are also dedicated methods for converting between text and numbers,
turning a string into a number or vice versa, as well as safe variants that return an error value
instead of crashing if the conversion isn't possible.

### When should I use it?
- When you need to turn user input (which always arrives as text) into numbers
- When you need to switch between numeric types, e.g. for calculations
- When you want to turn numbers into text for display

### Common Mistakes
- Trying to convert a string into a number without first checking whether the text is actually a valid number
- Forgetting that converting from double to int simply truncates the decimal places instead of rounding
- Using explicit casting where a safe conversion method would actually be needed, which can crash the program

## Practice
**Task:** Read a number as text from the console and convert it into an int variable. Check whether the conversion succeeded before doing further calculations with the value.

**Goal:** After this exercise you should be able to explain the difference between implicit and explicit conversion, and know how to safely convert user input into numbers.

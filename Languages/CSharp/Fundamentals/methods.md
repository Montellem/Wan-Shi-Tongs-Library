# Methods

### What is it?

A method is a named, reusable block of code that performs a specific task. Methods can accept input values (parameters) and optionally return a value. They help break code into manageable, reusable pieces instead of writing everything in one large block.

### Example

Imagine a method called "AddNumbers" that takes two numbers as parameters and returns their sum. Instead of writing that calculation everywhere in your program, you simply call the method with the numbers you want and get the result back.

Two methods are allowed to share the same name as long as they differ in the number or type of their parameters – this is called overloading. So there could be an additional "AddNumbers" method that takes three numbers instead of two.

Normally, calling a method passes along a copy of the given value. With the keywords ref and out, a method can instead access and modify the caller's original variable directly. With params, you can also pass an unspecified number of values to a method without having to build an array beforehand.

```csharp
static int AddNumbers(int a, int b)
{
    return a + b;
}

// Overload: same name, different parameters
static int AddNumbers(int a, int b, int c)
{
    return a + b + c;
}

// ref: variable must be initialized beforehand
static void Double(ref int value)
{
    value *= 2;
}

// out: value is assigned inside the method
static bool TryDivide(int number, int divisor, out int result)
{
    if (divisor == 0)
    {
        result = 0;
        return false;
    }
    result = number / divisor;
    return true;
}

// params: any number of values
static int Sum(params int[] numbers)
{
    int sum = 0;
    foreach (var n in numbers) sum += n;
    return sum;
}
```

### How does it work?

A method consists of a return type (or void, if nothing is returned), a name, a parameter list in parentheses, and the actual code block. When called, the program jumps into the method, runs its code, and then jumps back to the call site, possibly bringing a return value along. With overloading, the compiler decides which of the same-named methods is meant based on the parameters passed. ref requires the variable to already have a value before the call, while out doesn't require that, but forces the method to assign it a value inside the method.

### When should I use it?

* Whenever you have code that's needed in more than one place
* To break complex tasks into smaller, named steps
* Overloading, when the same basic operation makes sense with different inputs
* ref/out, when a method needs to "return" more than one value or directly modify an existing variable
* params, when the number of input values isn't known in advance

### Common Mistakes

* Writing methods that are too large and handle several unrelated tasks at once
* Forgetting that with ref the variable must already be initialized beforehand
* Using out parameters where a normal return value would be clearer
* Creating ambiguous overloads that the compiler can no longer distinguish cleanly

### Practice

**Task:**
Write a method that calculates and returns the area of a rectangle. Then create a second, overloaded version that instead calculates the area of a circle.

**Goal:**
After this exercise you should be able to write your own methods with parameters and return values, and explain the purpose of overloading.

# Nullable Types
### What is it?
Regular value types like int, double, or bool can never hold the value null in C#. They always
have a concrete value. Nullable types allow these value types to additionally take on the state
"no value present" (null). This matters whenever a missing value needs to be distinguished from a actual value (e.g. 0).

### Example
Imagine a form field for user's age. If the user leaves the field empty, the value isn't 0, it's simply not present.
A regular int variable can't represent that, because it must always contain a number. A nullable int variable, however,
can hold either a number or "no value".

```c#
int? age = null;

if (age.HasValue)
{
  Console.WriteLine($"Age: {age.Value}"):
}
else
{
  Console.WriteLine("No age provided.");
}

int actualAge = age ?? 0; //fallback value if null
```

### How does that work?
A nullable value type is marked by placing a question mark after the t ype name. Internally, a nullable type
is essentially a combination of the actual value and extra information about whether a value is present at all.
Before workling with the value, you should check whether it's actually set, otherwise accessing it can cause a runtime error.
There's also an operator that supplies a fallback value in case the variable is null.

### When should I use it?
- When a value is optional, e.g. for database fields that my be empty
- When "no value" has a different meaning than "0" or "false".
- For forms or interfaces where input might be missing.

### Common Mistakes
- Accessing the value of a nullable variable without first checking whether it actually holds value.
- Using nullable types everywhere "just to be safe", even though a value should always be present
- Ignoring the difference between "value is 0" and "value is not present"

### Pracite
**Task:** Create a nullable int variable for an optional age. Check whether a value is present
and print a different message to the console depending on the result.

**Goal:** After this exercise you should be able to explain why regular value types don't allow
null, and when nullable types make sense.

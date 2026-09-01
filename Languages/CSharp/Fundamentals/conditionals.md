# Conditionals (if/else, switch)

### What is it?

Conditionals let a program execute different code paths depending on a situation. The two main tools for this are the if/else structure, for simple to moderate decisions, and the switch structure, for many possible fixed values.

### Example

Picture a traffic light simulation: if the color is red, print "Stop"; if yellow, print "Get ready"; if green, print "Go". With if/else you check the color step by step. With switch you instead directly check which of the possible values the color matches, and each case gets its own output text – this is clearer once there are more than two or three possible values.

```csharp
string trafficLight = "yellow";

if (trafficLight == "red")
{
    Console.WriteLine("Stop");
}
else if (trafficLight == "yellow")
{
    Console.WriteLine("Get ready");
}
else
{
    Console.WriteLine("Go");
}

switch (trafficLight)
{
    case "red":
        Console.WriteLine("Stop");
        break;
    case "yellow":
        Console.WriteLine("Get ready");
        break;
    default:
        Console.WriteLine("Go");
        break;
}
```

### How does it work?

An if condition evaluates an expression that is either true or false. If it's true, the associated code block runs; otherwise, the program checks whether an else-if condition applies, or finally runs the else block if no condition matched. A switch structure compares a single value against several possible fixed cases and runs the matching block; a final default case handles anything that didn't match another case.

### When should I use it?

* if/else for conditions involving comparisons, ranges, or only a few cases
* switch when a single value is being compared against many concrete possible values
* Nested conditionals when several criteria need to be checked at the same time

### Common Mistakes

* Using a single equals sign instead of a comparison operator
* Deeply nested if structures that make the code hard to read
* Forgetting to handle the default case in a switch structure

### Practice

**Task:**
Write a small grade evaluator: depending on an entered score, output an appropriate grade ("Excellent", "Good", "Satisfactory", etc.). Solve it first with if/else, then consider whether the task could also reasonably be solved with switch.

**Goal:**
After this exercise you should be able to decide when if/else and when switch is the better choice.

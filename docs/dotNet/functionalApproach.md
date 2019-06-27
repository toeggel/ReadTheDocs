# Functional approach

Can improve:

* Predictability
* Maintainability
* Testability

## Taming side effects

Side effects make the code more difficult to test and reason about

We can reduce side effects by enforcing immutability 

```csharp
public class NoSideEffects {
    
    // no setter => value cannot change
    public int Result { get; }

    constructor(int value) 
    {
        Result = value;
    }

    public NoSideEffects Add(int value)
    {
        // return a new object to prevent side effects
        return new NoSideEffects(Result + value);
    }
}
```

## Emphasizing expressions
Can simplify code by always returning a value

Allows _piping_ by method chaining

### Statements
Have side effects

```csharp
string result;

if(number >= 0)
{
    result = "positiv"
}
else 
{
    result = "negative"
}
```

### Expressions
Always return a value and have not side effects

Expressions can be called once or any number of times and they will produce the same result, for a given input.

Expressions are easier to test

```csharp
var result = number >= 0 ? "positiv" : "negative"
```

## Expression Methods

```csharp
public static partial class FuncExtensions
{
    public static TResult Map<T, TResult>(this T value, Func<T, TResult> function) =>
        function(value);
}

public static partial class ActionExtensions
{
    public static void Do<T>(this T value, Action<T> function) =>
        function(value);
}

internal static void Calculate()
{
    "-2".Map(int.Parse) // string -> int
        .Map(Math.Abs) // int -> int
        .Map(Convert.ToDouble) // int -> double
        .Map(Math.Sqrt) // double -> double
        .Do(Console.WriteLine); // double -> void

    // Equivalent to:
    Console.WriteLine(Math.Sqrt(Convert.ToDouble(Math.Abs(int.Parse("-2")))));

    // or
    string input = "-2.0";
    int output1 = int.Parse(input); // string -> int
    int output2 = Math.Abs(output1); // int -> int
    double output3 = Convert.ToDouble(output2); // int -> double
    double output4 = Math.Sqrt(output3); // double -> double
    Console.WriteLine(output4); // double -> void
}
```
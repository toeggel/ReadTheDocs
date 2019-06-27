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

# Enum Handling
## Enum grouping

For groupings in enums use custom attributes and do some (slightly sophisticated) mapping when providing to the frontend.

**Example:**
```cs
public enum WorkGroup
{
    Publications = 0,
    Conference = 1,
}

public enum WorkType
{
   [WorkGroup(WorkGroup.Publications)]
   Book = 0,  
   
   [WorkGroup(WorkGroup.Conference)]
   ConferencePaper = 1,
}

public class WorkGroupAttribute : Attribute { /* .. store workgroup in property */ }

public class WorkGroupDto
{
	public WorkGroup WorkGroup { get; set; }
	public List<WorkType> WorkTypes { get; set; }
}

// Controller Action
// Create a Dto by using reflection which works on the Attribute
WorkGroupHelper.ToDto();
```

 ## Enum Class

 Doesn't work well with [EF](entityFramework.md).

```cs
public abstract class Enumeration : IComparable
{
    public string Name { get; private set; }
    public int Id { get; private set; }

    protected Enumeration(int id, string name) => (Id, Name) = (id, name);

    // Utility methods ...

    // public override string ToString() => Name;
    // public static IEnumerable<T> GetAll<T>() where T : Enumeration { /* .. code */ }
    // public override bool Equals(object obj) { /* .. code */ }
    // public int CompareTo(object other) => Id.CompareTo(((Enumeration)other).Id);
	// ...
} 

public class CardType : Enumeration
{
    public static CardType Visa = new(1, nameof(Visa));
    public static CardType MasterCard = new(2, nameof(MasterCard));

    public CardType(int id, string name) : base(id, name) { }
}
```
See: [Microsoft: enum class over enum type](https://docs.microsoft.com/en-us/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/enumeration-classes-over-enum-types)

---

Tags: #dotNet #design 

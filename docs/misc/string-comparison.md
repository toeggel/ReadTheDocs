# String Comparison in .NET

## Ordinal Comparison

Compares strings by raw Unicode values (binary comparison).  
Is faster, culture independent and the same on every machine.

Usually used for:

- File names  
- Identifiers, keys, IDs  
- Cache keys  
- Machine-readable values  
- Sorting data where determinism matters  

Example:

- "ä" != "ae"   ("U+00E4" != "U+0061" + "U+0065")
- "ä" > "a"     ("U+00E4" > "U+0061")
- Results are the same on every machine and every culture.

## Culture-Sensitive Comparison

Compares strings using linguistic rules of a specific culture and maches therefore user expectations in UI.  
This `CurrentCulture` overload is used by default but is dangerous because it can differ between servers and cause unpredictable behavior.

Usually used for:

- Displaying or sorting human-readable text  
- UI lists, menus, names  
- Searches intended for end users

Example (de-DE"):

- "ä" may compare equal to "ae"
- Sorting order matches German dictionary rules

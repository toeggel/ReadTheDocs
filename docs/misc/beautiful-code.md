# Beautiful Code

> The ratio between reading code and writing code is roughly 10:1!    

## Simplicity

> Simplicity is the best way to measure code quality  

Before introducing a new framework or library (which probably does some magic), ask yourself what problem this new tool solves, and whether we can change the problem so that we don't need the tool at all.

> If you don’t actively fight for simplicity in software, complexity will win.
> 
> …and it will suck.

### Code Traversal  

> When the code traversal is easy, the code is simple to follow.

How easy it is to navigate through the code? Is it easy to spot where the API functions are written? Is it easy to understand call flows, for example which methods are calling others (and why)- are there good state machines implemented or cleanly identified algorithms?

### Make the Simplest Thing that could possibly work.

1. Implement a new feature in the simplest way you can think of that "could possibly work". Make the code pass the Unit Tests.
2. Refactor the system to be the simplest possible code including all the features it now has.

### YAGNI

> Always implement things when you actually need them, never when you just foresee that you need them.

## Cohesion

> Stuff that changes together should live together (e.g.: achieved with vertical slicing)

## Modularity

Enforce modularity where possible (don't leave it to the discipline of the devs).

## Release Early, Release Often and You'll Start to Write Better Code

Or briefly put: shorten your release cycles!

This way:
your team will handle priorities much better than if you released only one time a year, for instance
as for you, you'll get to learn more about your code and your users
… as time spent on development tools, on scripts, on your build, is never a wasted time: it leads to high quality, clean and usable code

##  System Quality

> The Quality of a System is Defined by Our Ability to Change it!

## Write Pure Functions

> Makes your code easier to read and easier to test.

## Treat it like literature

It has forms, header, paragraphs, ..

> [!EXAMPLE]+ Before
> ```csharp
> var userIdList = userIds.ToList();  
>
> var persons = GetCachedPersons(userIdList);  
>   
> var remainingPersonUserIds = GetRemainingUserIds(userIdList, persons);
>   
> if (!remainingPersonUserIds.Any())  
> {  
>     return persons;  
> }
>   
> var personsFromPm = GetValidPersonsFromPersonManagement(remainingPersonUserIds);
>   
> persons.AddRange(personsFromPm)  
>   
> var remainingUserIds = GetRemainingUserIds(userIdList, persons);
>   
> if (!remainingUserIds.Any())  
> {  
>     return persons;  
> } 
> 
> var users = GetUsers(remainingUserIds); 
> 
> persons.AddRange(users.MapToPersons())  
>   
> return persons.DistinctBy(p => p.UserId);
> ```

> [!EXAMPLE]+ After
> ```csharp
> var userIdList = userIds.ToList();  
>
> var persons = GetCachedPersons(userIdList);  
>   
> var remainingPersonUserIds = GetRemainingUserIds(userIdList, persons);  
> if (!remainingPersonUserIds.Any())  
> {  
>     return persons;  
> }  
> var personsFromPm = GetValidPersonsFromPersonManagement(remainingPersonUserIds);  
> persons.AddRange(personsFromPm)  
>   
> var remainingUserIds = GetRemainingUserIds(userIdList, persons);  
> if (!remainingUserIds.Any())  
> {  
>     return persons;  
> }  
> var users = GetUsers(remainingUserIds);  
> persons.AddRange(users.MapToPersons())  
>   
> return persons.DistinctBy(p => p.UserId);
> ```
## Comments

Usually we write comments when the intent of the code is not clear. Instead of writing comments we should ask ourselves => `Can I write the code better?`

> Comments are often lies.

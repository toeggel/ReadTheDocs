# Programming Practices
## Simplicity
> Simplicity is the best way to meassure code quality  

__Code Traversal__:  
> When the code traversal is easy, the code is simple to follow.

How easy it is to navigate through the code? Is it easy to spot where the API functions are written? Is it easy to understand call flows, for example which methods are calling others (and why)- are there good state machines implemented or cleanly identified algorithms?

### Make the Simplest Thing that could possibly work.
1. Implement a new feature in the simplest way you can think of that "could possibly work". Make the code pass the Unit Tests.
2. Refactor the system to be the simplest possible code including all the features it now has.
### YAGNI
> "Always implement things when you actually need them, never when you just foresee that you need them."

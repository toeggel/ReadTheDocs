# Writing Beatiful Code
<Tip>
    
    The ratio between reading code and writing code is roughly 10:1! 
</Tip>

---

## Simplicity
> Simplicity is the best way to meassure code quality  

__Code Traversal__:  
> When the code traversal is easy, the code is simple to follow.

How easy it is to navigate through the code? Is it easy to spot where the API functions are written? Is it easy to understand call flows, for example which methods are calling others (and why)- are there good state machines implemented or cleanly identified algorithms?

### Make the Simplest Thing that could possibly work.
1. Implement a new feature in the simplest way you can think of that "could possibly work". Make the code pass the Unit Tests.
2. Refactor the system to be the simplest possible code including all the features it now has.
### YAGNI
> Always implement things when you actually need them, never when you just foresee that you need them.

## Cohesion
> Stuff that changes together should live together (e.g.: achieved with layering)

## Release Early, Release Often and You'll Start to Write Better Code
Or briefly put: shorten your release cycles!

This way:

your team will handle priorities much better than if you released only one time a year, for instance
as for you, you'll get to learn more about your code and your users
… as time spent on development tools, on scripts, on your build, is never a wasted time: it leads to high quality, clean and usable code

## Write Pure Functions
> Makes your code easier to read and easier to test.

## Comments
Usually we write comments when the intent of the code is not clear. Instead of writing comments we should ask ourselves => `Can I write the code better?`
> Comments are often a lies.

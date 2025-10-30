## Example
If you have code like this:

```csharp
Task<Toast> toastTask = this.StartToasterAsync();
Toast toast = await Task.FromResult(toastTask.Result);
```

**This workflow is completely wrong.** Let's translate it into English. Here's my to-do list for today:

- Put some bread in the toaster.
- While the bread is toasting I could be doing other work, but instead, **stare at the toaster doing nothing else until it is done**.
- Get the toast from the toaster, and start a new to-do list.
- The new to-do list is: _Obtain the piece of toast that I am now holding._
- Execute that to-do list. While I'm waiting for the to-do list to complete, go do other work, **but the to-do list is always already complete because the job is to obtain a result that I have already obtained**. So don't do other work. Just check that yes, I am in fact holding the piece of toast I just wrote a to-do list about.
- Now I have a piece of toast.

This workflow is an insane way to make toast. It works -- you end up with a piece of toast at the end -- but no sensible person would do this, and you should not write the equivalent computer program:

- It is an "asynchronous" workflow where **every possible asynchronous advantage has been removed**.
- The first step -- waiting for the toaster to pop -- has been synchronously waited.
- The second step -- asynchronously wait for a task that has already completed -- is never asynchronous!

Never never never write asynchronous code this way.

The right workflow for making a piece of toast is:

- Put the bread in the toaster and start it toasting.
- Do other work until the toast pops.
- Fetch the toast.

And as we'd expect, the correct way to write your program is much simpler:

```csharp
Toast toast = await this.StartToasterAsync(...);
```
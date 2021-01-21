# Angular

## Structoring Components

### Smart (Container) Components 
A Smart Component has external dependencies or causes side effects (but still might or might not have a local state).

* Knows stuff about the use-case (feature)

### Dumb (Presentational) Components
 A Dumb Component has no external dependencies and causes no side effects (but still might or might not have a local state).

* Doesn't care about a specific use-case (feature) but it supports it anyway (e.g.: displaying an adress. This component might support multiple use-cases)

Guidelines for dumb components:

* __Should not be dependant on external services__ — if it requires some data to work, it should be injected via ```@Input()```;
* __Should not produce any side effects__ — if it needs to emit something, it should be emitted with ```@Output()``` instead;
* __Should not mutate its’ inputs__ — because if it does, it actually produces a side effect that causes a change in the parent component’s data. 
 
Try to use dumb components as much as possible! They make your application less complex and easier to reason about. 

> If it can be Dumb, make it Dumb

## Async as
use __async as__ syntax as much as possible (reduces subscriptions / stream calls / complexity)
```html
<div *ngIf="(user$ | async) as user">
	{user.name}}
</div>
```

## NgIf Else
```*ngIf="value"; else notValue``` as an easy alternative to ```*ngIf="!value"```
```html
<div *ngIf="isLoggedIn; else loggedOut">
	Welcome back, friend.
</div>
<ng-template #loggedOut>
	Please friend, login.
</ng-template>
```
## Input with observables
Pass values to components instead of observables to reduce coupling

If observables are passed to a component a child component might trigger something in the parent component. Imagine a parent component defining an observable like this
```typescript
users$ = this.http.get(...);
```
When the ```user$``` gets passed to a child component which then subscribes to it
```typescript
this.user$.subscribe(u => this.user = u);
```
The child triggers (unknowingly / unwanted) HTTP requests

Same is valid for service calls. Instead of
```typescript
filteredusers$ = this.fooService.filterUsers(this.users$);
```
Better do
```typescript
filteredusers$ = this.users$.pipe(switchMap(users => this.fooService.filterUsers(users)));
```

## Performance issues in Angular
Debugging Performance Problems in Angular:

1.	Add debug() to html template
a.	Log something like ‘..rendering..’
2.	If too many renderings happen (some might happen) => Add Breakpoint
3.	Go down the StackTrace and look for “OnInvokeTask” => Add Breakpoint
4.	Take a look at the “task”-Property it might contain some infos about the function which lead to the re-rendering (e.g.: see callbackFun)
5.	???
6.	Profit
 
# Best Practices

## Angular
__Do not__  use myfunc.bind(this) in HTML-Template.  
__Why?__ It creates a new function for every rendering.  

__Try__ to minimize the use of functions in HTML-Template.  
__Why?__ They get  executed for every rendering.

__Do__ replace functions (in template) with (pure) pipes.  
__Why?__ Function calls made from a template are invoked every time a change occures (no caching) => getting called very often.  
__Why?__ Pipes are only called when inputs (to pipe function) are changed.  
__Consider__ Using Memo Decorator (npm package) to cache pipe outputs.

__Do__ use trackBy along with ngFor.  
__Why?__ When an array changes, Angular re-renders the whole DOM tree. But when you use trackBy, Angular will know which element has changed and will only make DOM changes only for that element.  

__Do__ use aliases for importing modules or libraries.

## Typescript
__Do__ define DTOs as interfaces instead of classes.  
__Why?__ A class generates code since it is primarily syntactical sugar over JavaScript’s existing prototype-based inheritance.   
__Why?__ An interface does not generate code since it is a virtual structures that only exist within the context of TypeScript.  
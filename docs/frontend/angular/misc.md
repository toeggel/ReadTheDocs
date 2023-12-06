# Misc

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

1. Add debug() to html template
	a.	Log something like ‘..rendering..’
2. If too many renderings happen (some might happen) => Add Breakpoint
3. Go down the StackTrace and look for “OnInvokeTask” => Add Breakpoint
4. Take a look at the “task”-Property it might contain some infos about the function which lead to the re-rendering (e.g.: see callbackFun)
5. ???
6. Profit
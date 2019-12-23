# Angular
## Smart Components
A Smart Component has external dependencies or causes side effects (but still might or might not have a local state).

## Dumb Components
 A Dumb Component has no external dependencies and causes no side effects (but still might or might not have a local state).
 - __Should not be dependant on external services__ — if it requires some data to work, it should be injected via ```@Input()```;
 - __Should not produce any side effects__ — if it needs to emit something, it should be emitted with ```@Output()``` instead;
 - __Should not mutate its’ inputs__ — because if it does, it actually produces a side effect that causes a change in the parent component’s data. 
 
Try to use dumb components as much as possible! They make your application less complex and easier to reason about. 
> If it can be Dumb, make it Dumb

## Async as
use as __async as__ syntax as much as possible (reduces subscriptions / stream calls / complexity)
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
```javascript
users$ = this.http.get(...);
```
When the ```user$``` gets passed to a child component which then subscribes to it
```javascript
this.user$.subscribe(u => this.user = u);
```
The child triggers (unknowingly / unwanted) HTTP requests

Same is valid for service calls. Instead of
```javascript
filteredusers$ = this.fooService.filterUsers(this.users$);
```
Better do
```javascript
filteredusers$ = this.users$.pipe(switchMap(users => this.fooService.filterUsers(users)));
```

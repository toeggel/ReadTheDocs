# Angular / rxjs / ngrx / observables tips & tricks, best practices and more
## Angular
### Smart Components
A Smart Component has external dependencies or causes side effects (but still might or might not have a local state).

### Dumb Components
 A Dumb Component has no external dependencies and causes no side effects (but still might or might not have a local state).
 - __Should not be dependant on external services__ — if it requires some data to work, it should be injected via ```@Input()```;
 - __Should not produce any side effects__ — if it needs to emit something, it should be emitted with ```@Output()``` instead;
 - __Should not mutate its’ inputs__ — because if it does, it actually produces a side effect that causes a change in the parent component’s data. 
 
Try to use dumb components as much as possible! They make your application less complex and easier to reason about. 
> If it can be Dumb, make it Dumb

### Async as
use as __async as__ syntax as much as possible (reduces subscriptions / stream calls / complexity)
```html
<div *ngIf="(user$ | async) as user">
	{user.name}}
</div>
```

### NgIf Else
```*ngIf="value"; else notValue``` as an easy alternative to ```*ngIf="!value"```
```html
<div *ngIf="isLoggedIn; else loggedOut">
	Welcome back, friend.
</div>
<ng-template #loggedOut>
	Please friend, login.
</ng-template>
```
### Input with observables
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

## Rxjs

### Reusable pipes
```javascript
export const selectFilteredValues = pipe(
	select(selectValues),
	filter(val => val !== undefined)
);
store.pipe(selectFilteredValues).subscribe(/* .. */);
```

### Cold Observables
- Imagine watching a movie on Netflix. You decide when to watch (subscribe) and what to watch. Every person gets its own 'verion' of the movie
- every subscription triggers the producer of the stream
- ```.share()``` makes the observable hot
- ```.shareReplay(1)``` same as ```.share()``` but the last value is kept and can therefore be accessed by late subscribers

### Hot Observables
- Imagine watching a movie in a cinema. The movie runs with or without you. When you join the cinema (subscribe) the movie might already be runnin and you missed the beginning. Every person gets the same 'version' of the movie.

## NgRx
- Only use it when (and where) you need it.
- Do not duplicate the same information all over the place (e.g.: if you already have items stored you don't store the selected items but only the ids of the selected items and mereg them together)
- There should not be many nested levels of data
- Make everything readonly
  ```javascript
  type User = {
    readonly firstName: string;
    readonly lastName: string;
  }
  ```
- Don’t use the store all over the place. Dumb components should not be aware of any state or how to fetch data
- Use selectors
- ```selector``` properties can be initialized directly when defining them instead of in the constructor

  ```javascript
  export class DocumentContainer {
      companyName$ = this.store.select(detailsSelector.getDocumentCompanyName);
      documentStatus$ = this.store.select(detailsSelector.getDocumentStatus);

      constructor(private store: Store<AppStore.AppState>) {
        // no need to do the initialization in here
      }
  }
  ```

### What do we put in the store
When...
- state needs to be shared between different root components (rendered inside a router-outlet)
- state that needs to be kept when navigating. e.g.:
	- Sidebar state
	- Panel state
- complex state
- the state gets updated from different sources (forntend and backend (e.g. with sockets))

We shouldn’t put things in the store just because we can
- If that component state does not affect anything from the application state, it does not need to be on the application state or touch redux.
- State that is being shared between components can sometimes be kept in the parent component for instance

### Reducers
Reducers should be very simple (think of refactoring otherwise)

### Effects
__Always handle errors__

The actions stream (effects) is an Observable, this means that once an error occurs it’s done. This means making requests on a different stream that we then merge with operators like switchMap and always handle errors there.
```javascript
loadDocuments$ = this.actions$.pipe(
  ofType<documentActions.Fetch>(documentActions.FETCH)
  switchMap(() =>
    this.documentsService.getDocuments().pipe(
      map(docs => new documentActions.FetchSuccess(docs)),
      // handle error here so the actions$ stream will not be broken
      catchError(err => of(new documentActions.FetchFailed())) 
    )
  )
)
```
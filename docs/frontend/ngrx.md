# NgRx
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
  - Don't use rxjs stuff like  ```combineLatest``` to combine data from different states __use selectors__ instead. Selectors are aware on which data they rely and can there for optimize there recalculation. Often Facades are used to abstract the store but they often lead to the lack of selectors (e.g.: Combining data from two facades)
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
- Actions should be unique and should be used for one specific purpose onl. Hiding action dipatching behind Facades leads to reuse of Actions which is usually a bad thing since it gets more difficult to follow the data stream (which call did update the store?).

## What do we put in the store
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

## Reducers
Reducers should be very simple (think of refactoring otherwise)

## Effects
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
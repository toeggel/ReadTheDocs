# Best Practices

## Angular

__Avoid__ myfunc.bind(this) in HTML-Template.  
__Why?__ It creates a new function for every rendering.  

__Do__ minimize the use of functions in HTML-Template.  
__Why?__ They get  executed for every rendering.

__Do__ replace functions in template with (pure) pipes.  
__Why?__ Function calls made from a template are invoked every time a change occures (no caching) => getting called very often.  
__Why?__ Pipes are only called when inputs (to pipe function) are changed.  
__Consider__ Using Memo Decorator (npm package) to cache pipe outputs.

__Do__ use trackBy along with ngFor.  
__Why?__ When an array changes, Angular re-renders the whole DOM tree. But when you use trackBy, Angular will know which element has changed and will only make DOM changes only for that element.  

__Do__ use aliases for importing modules or libraries.

__Do__ use async-pipe in view and pass value to action instead of directly working on the stream within the action.

## Typescript
__Avoid__ using any.
__Why?__ It creates enormous bug opportunity.

__Do__ define DTOs as interfaces instead of classes.  
__Why?__ A class generates code since it is primarily syntactical sugar over JavaScript’s existing prototype-based inheritance.   
__Why?__ An interface does not generate code since it is a virtual structures that only exist within the context of TypeScript.  

## rxjs
__Do__ use Marble Diagrams to understand rxjs (e.g. https://rxmarbles.com/, https://rxjs-dev.firebaseapp.com/api).

__Do__ unsubscribe from observables (e.g. by calling unsubscribe(), using an operator that completes the stream, using the async pipe).  
__Why?__ It prevents memory leak.

__Do__ use async pipe.  
__Why?__ It simplifies code by automatically un-/subscribing from the observable.  
__Why?__ It allows OnPush change detection strategy.
Consider *ngIf “as” or hot observables to prevent multiple execution of observables.

__Avoid__ nested subscriptions.  
__Why?__  It makes the code unreadable, complex, and introduces side effects.

__Avoid__ logic inside the subscribe function.  
__Why?__ The reactive workflow and its benefits ends by subscribing to an Observable.

__Do__ pass values to components and services instead of observables.  
__Why?__ It reduces coupling.  
__Why?__ It prevents unwanted side-effects.
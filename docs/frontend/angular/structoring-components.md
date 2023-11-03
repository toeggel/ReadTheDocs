# Components - Smart vs. Dumb

## Smart (Container) Components 
A Smart Component has external dependencies or causes side effects (but still might or might not have a local state).

* Knows stuff about the use-case (feature)

## Dumb (Presentational) Components
 A Dumb Component has no external dependencies and causes no side effects (but still might or might not have a local state).

* Doesn't care about a specific use-case (feature) but it supports it anyway (e.g.: displaying an adress. This component might support multiple use-cases)
* Injecting services into dumb component might be ok as long as they only handle view logic (e.g. translation service). Never inject services which handle business logic.


Guidelines for dumb components:

* __Should not be dependant on external services__ — if it requires some data to work, it should be injected via ```@Input()```;
* __Should not produce any side effects__ — if it needs to emit something, it should be emitted with ```@Output()``` instead;
* __Should not mutate its’ inputs__ — because if it does, it actually produces a side effect that causes a change in the parent component’s data. 
 
Try to use dumb components as much as possible! They make your application less complex and easier to reason about. 

> [!quote] If it can be Dumb, make it Dumb
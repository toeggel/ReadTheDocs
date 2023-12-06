# When to initiate data load

* When the app starts.
* When a container component is initialised.
* When the app navigates to a route.
* When the user performs an action.

See: https://dev.to/jonrimmer/where-to-initiate-data-load-in-ngrx-358l

## When the app starts

__Pros:__

* The data is guaranteed to load.

__Cons:__

* Memory / performance concerns if there's a lot of data to load.

## When a container component is initialised

__Pros:__  

* You only load data as and when it's needed.
* It's clear from looking at the component what data it's relying on.

__Cons:__

* You either need lots of actions, or to dispatch the same action in several places.
* The component is less pure, as it has the side effect of loading data.
* You might forget to dispatch the action from a component that needs the data. This bug could be obscured if you normally reach the component through another component that does initiate the data load. E.g. you normally open a list page before opening a details page. Then, one day, you navigate directly to the details page and it breaks.

## When the app navigates to a route

__Pros:__

* Less duplication. A single guard at the root of a route hierarchy can load the data for all child routes, even if they're navigated to directly.
* Components are more pure, as they only map from selected state to their template output.

__Cons:__

* Quite blunt: A guard will trigger data load for any child route, even if its component doesn't need it.
* Less obvious from looking at a component what data it needs to work. If it gets moved somewhere else in the router hierarchy, it'll break.
* Less useful if routes requiring some particular data are spread out throughout the router hierarchy, as you'll need to include the guard in different places.

### Why not Resolvers?

* Resolvers are synchronous (and do not integrate well with observable streams).

"Imagine a long running HTTP request. After clicking a link in our application, the HTTP request starts. The routing will not be finished before the HTTP response comes back. Thus, if the HTTP takes 5 seconds, it will also take 5 seconds for the routing to complete. If you are like me, you will have hit the button another 3 times within that time. 😉"

"This behavior completely breaks the idea of a Single-Page Application: An SPA should always react fast and load the necessary data asynchronously at runtime. With the behavior described – click, wait, continue – we are back to the user experience of a classical server-only rendered page like 15 years ago. Not good. And here we are with the problematic UX resolvers bring us. Try this out in the demo!"

## When the user performs an action

* When the user clicks a button to explicitly load or reload some data.
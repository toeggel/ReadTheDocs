# Rxjs

```javascript
// Following 3 obserable creations are equal 
const appleStream = new Observable(appleObserver => {
  appleObserver.next('Apple 1');
  appleObserver.next('Apple 2');
  appleObserver.complete();
});

// Equivalent to...
const appleStream = of('Apple 1', 'Apple 2'); // this stream get completed too

// And equivalent to...
const appleStream = from(['Apple 1', 'Apple 2']); // this stream get completed too
```

## Reusable pipes
```javascript
export const selectFilteredValues = pipe(
	select(selectValues),
	filter(val => val !== undefined)
);
store.pipe(selectFilteredValues).subscribe(/* .. */);
```

## Cold Observables
- Imagine watching a movie on Netflix. You decide when to watch (subscribe) and what to watch. Every person gets its own 'verion' of the movie
- every subscription triggers the producer of the stream
- ```.share()``` makes the observable hot
- ```.shareReplay(1)``` same as ```.share()``` but the last value is kept and can therefore be accessed by late subscribers

## Hot Observables
- Imagine watching a movie in a cinema. The movie runs with or without you. When you join the cinema (subscribe) the movie might already be runnin and you missed the beginning. Every person gets the same 'version' of the movie.

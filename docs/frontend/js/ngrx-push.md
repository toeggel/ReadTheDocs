# ngrxPush

There are two key differences compared to the `async` pipe

* The `ngrxPush` pipe will not mark the host component as dirty when an observable emits the same values in a row.
* The `ngrxPush` pipe will not mark the host component as dirty when an observable emits values synchronously.
* The `ngrxPush` pipe will trigger change detection when an observable emits a new value in zone-less mode.
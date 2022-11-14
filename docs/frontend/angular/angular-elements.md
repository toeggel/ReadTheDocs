# Angular Elements

* ✔ Easy to use.
    * use https://angular-extensions.github.io/elements/#/home for lazy loading and single loading
* ✔ Angular stack (If the whole stack is already on angular)
* ❌ All elements of an app getting bundled together.
    * load one => load all (no tree-shaking on component level)
* ❌ To load elements individually one needs to create multiple apps where each needs to load the angular framework (size overhead)
    * Dependency sharing is difficult (e.g. angular/core). Module federation can help.
    * we can exclude dependency with `ngx-build-plus` but then we might end up in a dependency hell.

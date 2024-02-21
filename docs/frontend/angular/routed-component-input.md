---
tags:
  - angular
  - ng16
---
# Routed component input

Angular v16 has introduced a powerful new feature that enables the automatic binding of router information, such as query parameters, path parameters, static data, and resolver data to a routed component’s inputs.

This feature currently needs to be activated in the app bootstrap. See: `withComponentInputBinding()`.

```typescript
@Component({
    template: `<div *ngIf="data$ | async as data">{{ data }}</div>`
})
export class SearchComponent implements OnInit {
    private dataService = inject(DataService);

    id$ = new BehaviorSubject<string | null>(null);
    query$ = new BehaviorSubject<string | null>(null);

    // This is an example how we could convert the param to an observable. If we just need a single value we can use a basic @Input() field instead.
    @Input() set id(id: string) { this.id$.next(id); }
    @Input() set query(query: string) { this.query$.next(query); }

    data$ = combineLatest([
        this.id$.pipe(filter(id => id !== null)), 
        this.query$.pipe(filter(query => query !== null))
    ]).pipe(
        switchMap(([id, query]) => this.dataService.getData(id, query))
    );
}
```

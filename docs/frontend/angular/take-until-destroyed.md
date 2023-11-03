---
tags:
  - angular
  - ng16
---
# Take Until Destroyed
For takeUntilDestroyed to work it needs the DestroyRef which is only available within the injection context (e.g constructor, field initializer). If run outside of the injection context the DestroyRef needs to be passed as a parameter.

```typeScript

export class FooCmp implements OnInit {
    params$ = of(1).pipe(takeUntilDestroyed())

    ngOnInit() {
        this.params$.subscribe(res => {/* some operation */})
    }
}

export class BarCmp {
    constructor() {
        of(1)
        .pipe(takeUntilDestroyed())
        .subscribe(res => {
            // some operation
        })
    }
}

export class BazCmp implements OnInit {
    destroyRef = inject(DestroyRef)

    ngOnInit() {
        of(1)
        .pipe(takeUntilDestroyed(this.destroyRef))
        .subscribe(res => {/* some operation */})
    }

}

```


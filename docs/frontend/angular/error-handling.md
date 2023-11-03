---
tags:
  - angular
---
# Error Handling

## Pattern

```typescript
<ng-container *ngIf="(isLoading$ | async) === false; else loading">
    <ng-container *ngIf="!(error$ | async); error">
        <!-- Content -->
    </ng-container>

    <ng-template #error>
        <ng-container [ngSwitch]="error$ | async">
            <ng-container *ngSwitchCase="someError1">
                <!-- Error message -->
            </ng-container>
            <ng-container *ngSwitchCase="someError2">
                <!-- Error message -->
            </ng-container>
    </ng-template>
</ng-container>

<ng-template #loading>
    <!-- Loading indicator -->
</ng-template>
```
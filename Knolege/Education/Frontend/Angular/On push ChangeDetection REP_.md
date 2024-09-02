#angular

`OnPush` change detection strategy in angular is designed to optimize performance by reducing the number of change detection cycles.
This strategy instruct angular to detect changes only when specific conditions are meet
- changed input property `@Input`
- triggered manually via using `ChangeDetectorRef`
- An event is emitted within the component (include its children)

Example
```ts
import { Component, ChangeDetectionStrategy, Input } from '@angular/core';

@Component({
  selector: 'app-on-push-strategy',
  template: `<div>{{ data }}</div>`,
  changeDetection: ChangeDetectionStrategy.OnPush
})
export class OnPushStrategyComponent {
  @Input() data: string;
}
```
there is an input property that means that we wan to use this component inside the other components
and if in that place where we use our `OnPushStrategyComponent` we change its input parameter somehow then the change detection event is triggered.

**Pros/Cons**
**Pros**
- **Performance Optimization**: By reducing the number of change detection cycles, the `OnPush` strategy can significantly improve the performance of your application, especially in large applications with many components.
- **Predictable State Management**: Since change detection is only triggered by specific conditions, it becomes easier to predict and manage the component state.

**Cons** 
- Change detection is not triggered if you change just a property of an object because obj res stay the same 

**Use cases**
- **Static Data**: Components that render data that does not change frequently or at all.
- **Pure Components**: Components that only depend on their input properties and do not have internal state changes that affect the view.
- **Optimized Performance**: Applications or parts of applications that require optimized performance and where unnecessary change detection cycles should be minimized.
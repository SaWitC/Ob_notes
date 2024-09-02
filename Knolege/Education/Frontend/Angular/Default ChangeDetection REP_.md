#angular
The `Default` change detection strategy in Angular is the standard mode of operation for Angular's change detection mechanism. When using this strategy, Angular checks every component and its children during each change detection cycle to determine if any changes have occurred that require the DOM to be updated.

**How it works**
- Change detection is triggered by an angular when certain event occurs, such as: 
	- click
	- input
	- Asynchronous operation (timer ,http request)
	- explicit call call to method that change data

**Propagation**:

- When a change detection cycle begins, Angular starts checking from the root component and traverses the entire component tree, checking each component for changes.
- Angular compares the current state of component properties with their previous state. If a change is detected, the corresponding part of the DOM is updated.

**Example of Default Change Detection in Action**
```ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-default-strategy',
  template: `<div>{{ data }}</div>`
})
export class DefaultStrategyComponent {
  data = 'Initial data';

  constructor() {
    setTimeout(() => {
      this.data = 'Updated data'; // This change will be detected automatically
    }, 2000);
  }
}
```
**Pros/Cons**

**Pros**
- simplicity :you do not have to change change detection strategy and it will wor and detect all changes automaticly

**Cons**
- performance overhead : default change detection strategy may be not a good idea for large application because even if change just an input it will triger change detection for all components even for that that was not changed.
- Checks unchanged components.


**Performance Optimization Techniques**
1. Avoid unnecessary bindings in your templates. Complex expressions or bindings that change frequently can increase the number of checks Angular performs.
2. Use `TrackBy` [angular doc](https://v17.angular.io/api/core/TrackByFunction) to track items more efficiently
``` html
<div *ngFor="let item of items; trackBy: trackByFn">{{ item.name }}</div>
```
```ts
trackByFn(index, item) {
  return item.id; // or a unique identifier
}
```
3. Debounce and Throttle Events
   Debounce or throttle events such as scroll, resize, or input to limit the frequency of change detection cycles.
4. Use pure pipes Angular pipes can transform data in the template. pure pipes are only change data when the input data changes 

### extras
- even if you change data that are not reflected on the UI change detection event still occur just to keep application consistent because sometimes data in one component may affect other components
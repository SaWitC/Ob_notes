#angular
## Sources
https://blog.angular-university.io/how-does-angular-2-change-detection-really-work/
https://www.youtube.com/watch?v=-tB-QDrPmuI&ab_channel=MonsterlessonsAcademy
https://blog.angular-university.io/onpush-change-detection-how-it-works/
## Key Concepts of Change Detection in Angular
1. Zones 
   Angular uses a library called zone.js to manage change detection. Zones are execution context allow angular to track asynchronous operations and run change detection
2. Change detection strategy
   angular provides two change detection strategis
   - Default it is a strategy that is used by default [[Default ChangeDetection REP_]]
   - OnPush Angular only check component and its children if an input property changes or an event is emitted within the component [[On push ChangeDetection REP_]]
3. Change detection cycle When an asynchronous event  (like http response) occurs Angular's zone triggers a change detection cycle.
   During this cycle angular check each component to see if any data has changed and updates the DOM accordingly
4. Detecting changes manually
   Sometimes automatic change detection might not be sufficient and you might need to trigger change detection manually using `ChangeDetectorRef` service
### Using ChangeDetectorRef

`ChangeDetectorRef` provides methods to manually trigger change detection:

- `markForCheck()`: Marks the component and its ancestors as needing change detection.
- `detectChanges()`: Performs change detection immediately on the component and its children.
- `detach()`: Detaches the change detector from the change detection tree.
- `reattach()`: Reattaches the change detector to the change detection tree.



What happens is that Angular at startup time will patch several low-level browser APIs, such as for example `addEventListener`, which is the browser function used to register all browser events, including click handlers. Angular will replace `addEventListener` with a new version that does the equivalent of this:
```ts
// this is the new version of addEventListener
function addEventListener(eventName, callback) {
     // call the real addEventListener
     callRealAddEventListener(eventName, function() {
        // first call the original callback
        callback(...);     
        // and then run Angular-specific functionality
        var changed = angular.runChangeDetection();
         if (changed) {
             angular.reRenderUIPart();
         }
     });
}
```
The new version of `addEventListener` adds more functionality to any event handler: not only the registered callback is called, but Angular is given a chance to run change detection and update the UI.

### The change detection tree
Each Angular component has an associated change detector, which is created at application startup time. For example, take the following  
`TodoItem` component:

```ts
@Component({
    selector: 'todo-item',
    template: `<span class="todo noselect" 
       (click)="onToggle()">{{todo.owner.firstname}} - {{todo.description}}
       - completed: {{todo.completed}}</span>`
})
export class TodoItem {
    @Input()
    todo:Todo;

    @Output()
    toggle = new EventEmitter<Object>();

    onToggle() {
        this.toggle.emit(this.todo);
    }
}

export class Todo {
    constructor(public id: number, 
        public description: string, 
        public completed: boolean, 
        public owner: Owner) {
    }
}
```
This component will receive a Todo object as input and emit an event if the todo status is toggled. To make the example more interesting, the Todo Class contains a nested object:
#### What does the Todo Item change detector look like?

We can actually see at runtime what the change detector looks like! To see it lets just add some code in the Todo class to [trigger a breakpoint](https://github.com/jhades/blog.angular-university.io/blob/master/ng2-change-detection/src/todo.ts?ref=blog.angular-university.io#L11) when a certain property is accessed.

When the breakpoint hits, we can walk through the stack trace and see change detection in action:
![[Pasted image 20240805103530.png]]
## Summary
### Optimizing Performance with Change Detection

- Use `OnPush` strategy wherever possible to minimize the number of checks Angular performs.
- Avoid unnecessary bindings in templates that can trigger frequent change detection.
- Use `async` pipes in templates for observables to handle subscriptions and unsubscriptions automatically.
- Detach change detection for components that do not need frequent updates and reattach only when necessary.
#angular
https://luukgruijs.medium.com/understanding-hot-vs-cold-observables-62d04cf92e03
Cold observables

When the data is produced by the Observable itself, we call it a cold Observable. When the data is produced outside the Observable, we call it a hot Observable.

```ts
//example cold

var observable = of(1,2,3)
observable.subscribe(x=>console.log(x))//every time return the same data 1,2,3

//Example hot
//in this exampl i difine simle synchronization service with method setDateSuggestion() that emit data to the observable from outside
//Subject
 private dateSuggestionSubject: Subject<FormlyDateSuggestion> = new Subject();
  //Data emiter (from outside)
  public setDateSuggestion(suggestion: FormlyDateSuggestion) {
    this.dateSuggestionSubject.next(suggestion);
  }
  //Observable
  public getDateSuggestionObservable$(): Observable<FormlyDateSuggestion> {
    return this.dateSuggestionSubject.asObservable();
  }
```
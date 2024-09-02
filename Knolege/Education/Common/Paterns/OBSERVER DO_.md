#paterns
Useful pattern especially in case you want to synchronize some data

Situation
You have an application with UI where you display a lot of data some charts and etc
and when user change **company** you have to reload all related data 

to implement such logic you have to 
- create synchronization service
- subscribe to observer and emit event

 example
```ts
//Service
@Injectable({
  providedIn: 'root'
})

export class TenantCompanyChangedSynchronizationService {
  private TenantSubject$ = new Subject<void>()
  private CompanySubject$ = new Subject<void>()

  public getTenantObservable$():Observable<any>{
    return this.TenantSubject$.asObservable();
  }

  public getCompanyObservable$():Observable<any>{
    return this.CompanySubject$.asObservable();
  }

  public emitTenantChangedEvent(){
    this.TenantSubject$.next();
  }

  public emitCompanyChangedEvent(){
    this.CompanySubject$.next();
  }
}

// subscribe to changes
    this.TenantCompanySynchronizationService.getCompanyObservable$().subscribe(()
    {
	    this.loadDasbordChartData();
    });

//Emit event
  this.tenantCompanySynchronizationService.emitCompanyChangedEvent();
```
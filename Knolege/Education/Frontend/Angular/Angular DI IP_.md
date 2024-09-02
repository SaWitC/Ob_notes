[[DI Tokens NE_]] #angular
## Sources
https://www.youtube.com/watch?v=GvA7xnBmEto&ab_channel=MonsterlessonsAcademy

**Main Concepts**
- Dependency injection it is a mechanism that returns an instance of an object automatically



`ProvidedIn :'Root'` means that our Service created only once for an entire application and registered via root injector
```ts
platformBrowserDynamic()
  .bootstrapModule(AppModule) //root injector
  .catch((err) => console.error(err));
```

variants of @Injectable()
``` ts
    providedIn?: Type<any> | 'root' | 'platform' | 'any' | null;
```
- root default value means that we register our service only once as a singleton
- any - Deprecated

Instead of jus a service we can pass an object:
`useClass`
```ts
//Before
providers:[someService]
//After
Providers:[{provide:someService,useClass:someService}]//it can be useful in case you want to replace an old instance to a new one just like in code below
Providers:[{provide:someService,useClass:newSomeService}]


```

- useClass (means every time use newSomeService class and in case we register services like below ) it create newSomeService twice once for newSomeService and once for someService.
  to solve it we can replace it to `useExisting`

**`useClass`  `useExisting`**
```ts
//Old
Providers:[
newSomeService,
{provide:someService,useClass:newSomeService}
]
//new
Providers:[
newSomeService,
{provide:someService,useExisting:newSomeService}
]
```
- useValue (you can pass some value/obj )

`useFactory
```ts
export const heroServiceProvider = {
  provide: HeroService,
  useFactory: heroServiceFactory,
  deps: [Logger, UserService]
};
```
- The `useFactory` field specifies that the provider is a factory function whose implementation is `heroServiceFactory`.
- The `deps` property is an array of provider tokens. The `Logger` and `UserService` classes serve as tokens for their own class providers. The injector resolves these tokens and injects the corresponding services into the matching `heroServiceFactory` factory function parameters, based on the order specified.

InjectionTokens
[[DI Tokens NE_]]

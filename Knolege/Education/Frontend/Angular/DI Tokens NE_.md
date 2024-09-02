#angular
https://medium.com/ngconf/configure-your-angular-apps-with-an-injection-token-be16eee59c40

It is unique token that can be used to mark some kind of services but also we can use it just to define different configuration 
Example (shared package)
```ts
_//color.service.ts (SharedLibrary)_public constructor(  
   @Inject(COLOR_CONFIG_TOKEN) private config: ColorConfig,  
) {}public getProductInfo(){     
   return `Please visit   
           ${this.config.productGeneralConditions}   
           for more information about our   
           ${this.config.productColor} product`;  
}
```
in the example above we use configuration that can be different in every application 
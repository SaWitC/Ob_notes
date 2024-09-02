#net
https://github.com/dotnet/AspNetCore.Docs/blob/main/aspnetcore/performance/memory.md

In .net we have two different GC modes
The first one **Work station mode** and the second one **Server mode**
When you create a new project API your application use **Server mode** by default
to Change it you can use following command
```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```
Differences 

| Server Mode                                                            | WorkStation Mode                                                                   |
| ---------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| Is better in case you use a separate machine just for your application | Is better to use in case you run several different application on the same machine |
| Trigger garbage collection only on low memory                          | Trigger Garbage collection much more often compare to server mode                  |
| **Can not be used on a machine with a single logical core**            | Can be used                                                                        |
|                                                                        |                                                                                    |



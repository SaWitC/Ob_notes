#net
[[GC Modes DO_]]
#questions
GC it is a mechanism that is used to automatically cleanup unused resources
https://medium.com/c-programming/c-memory-management-part-3-garbage-collection-18faf118cbf1
https://medium.com/c-programming/c-memory-management-part-2-finalizer-dispose-d3b3e43c08d1
https://medium.com/c-programming/c-memory-management-part-3-garbage-collection-18faf118cbf1
## GC 
GC consist of three generation
**0 Generaten** stores newes objets that was created and was not cleaned yet
**1 generation** store objects that survived generateion 0 
2 Generation store elements that survived generation 0 and 1 and still in use

----
## GC phases
1. marking (finds and creates list of all living objects)
2. moving (updates the references to objects that will be compacted)
3. Compacting (Reclaims the space ocupied by the dead objects and compact the survived objects)
## Finalization & Dispose
**Garbage Collector** handles memory management in .NET framework and conducts the allocation and reclaiming of memory for the applications . However, when we create objects that include unmanaged resources such as windows, files, network and database connections, we must explicitly release those resources after using them in our applications. This can be done by :
- using finalizers
- implementing _Dispose_ method from the _IDisposable_ interface
### Finalization
Finalizer (also known as destructor in c++) are used to perform any necessary final clean-up when class when class instance is being collected by GC
**Important information**
1. A class can have only one destructor
2. A finalizer does not have modifiers or parameters
3. Destructors can not be called explicitly they are called by GC when object is ready for finalization or when we stop the application

Finalizer overrides the _Finalize_ method of the base class. So the call to the finalizer is implicitly translated to the following code:
```c#
protected override void Finalize()
{
try
{
//cleanup statements|
}
finally
{

base.Finalize();
}
}
```
### Dispose Method
It is an approach to cleanup resources by calling method Dispose()/Clean() or by using **using** statement.

## Dispose pattern
```C#
using System; public class BaseClassWithFinalizer : IDisposable { 
// To detect redundant calls 
	private bool disposedValue;
	~BaseClassWithFinalizer() => Dispose(false); 
	// Public implementation of Dispose pattern callable by consumers. 
	public void Dispose()
	{
		Dispose(true);
		GC.SuppressFinalize(this);
	} 
	// Protected implementation of Dispose pattern. 
	protected virtual void Dispose(bool disposing) 
	{ 
		if (!disposedValue) 
		{
			if (disposing) 
			{ 
			// TODO: dispose managed state (managed objects) } 
			// TODO: free unmanaged resources (unmanaged objects) and override finalizer 
			// TODO: set large fields to null 
			disposedValue = true; 
			} 
		}
	}
}
```
explanation
<span style="color:#44bbff">bool disposedValue;</span> - (boolean variable provides that clients can call the method multiple times without getting an exception.)
<span style="color:#4499ff">public void Dispose()</span> - Clent called method
when client call Dispose() it runs disposing by calling **Dispose(true);**  and disable finalization by calling **GC.SuppressFinalize(this);**
<span style="color:4499ff">protected virtual void Dispose(bool disposing)</span> - under the hoot implementation of the read dispose method


## GC triggers and Modes
### Triggers
1. low system physical memory
2. The memory that is used by allocated objects on the managed heap surpasses an acceptable threshold.
3. The [GC.Collect](https://docs.microsoft.com/en-us/dotnet/api/system.gc.collect) method is called. _(In almost all cases, you do not have to call this method, because the garbage collector runs continuously. This method is primarily used for unique situations and testing.)
### GC modes
1. Work station mode
2. Server mode

## Unmanaged Resources
- Unmanaged resources include (streams except(MemmoryStream), different network Connection)
- To Cleanup this resources you have to use Finalizer or Disposer


# <span style="color:#caa641">Question</span>
### Tell about generation GC 
1. What is the number of generations that exist in GC
2. how objects move between generations
### Tell about phases GC
### Finalization and Dispose
1. What is the difference between finalization and Dispose method\
2. Can we create multiple destructors for a single class
3. Can we apply access modifiers to **Destructor** or pass some parameters
4. will this code trigger Finalization for base class
```	c#
|   |
|---|
|class Person|
||{|
||~Person() //finalizer (destructor)|
||{|
||//cleanup statements|
||Console.WriteLine("Person's finalizer is called.");|
||}|
||}|
|||
||class Employee : Person|
||{|
||~Employee()|
||{|
||//cleanup statements|
||Console.WriteLine("Employee's finalizer is called.");|
||}|
||}|
|||
||class Manager : Employee|
||{|
||~Manager()|
||{|
||//cleanup statements|
||Console.WriteLine("Manager's finalizer is called.");|
||}|
||}|
|||
||class Program|
||{|
||static void Main(string[] args)|
||{|
||var manager = new Manager();|
||}|
||}|
```
YES
### Extra
1. tell about GC modes
2. tell about Dispose pater and how to implement it
3. what for we use method gc.SuppressFinalize
4. do we have any differences in how GC cleanup object with and without Destructor
5. What is the managed resources
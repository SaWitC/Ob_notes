#paterns
The basic idea of this pattern is to create some system element called mediator, which receives some data and performs operations related to this data. 

mostly when we talk about mediator we use it with [[CQRS DO_]] pattern

Example
```c#
//Commands
public interface ISomeComand{}

public class SomeComandA{}
public class SomeComandB{}
//command handlers
public class SomeComandHandlerA{
	public SomeType HandleAsync(){
	
	}
}

public class SomeComandHandlerB{
	public SomeType HandleAsync(){
	
	}
}

//Mediator class
public class Mediator{
	public Execute(ISomeComand command){
		switch(command){
		case SomeCommandA:
			var handler = new SomeComandHandlerA()
			handler.HandleAsync();
			break;
		}
		//...
	}
}
```

Also you can use two popular libraries
such ass 
1)**Mediatr** (commonly used library based on reflection)
https://github.com/jbogard/MediatR
2)alternate package **Mediator** (the main concept is usage of source generators)
https://github.com/martinothamar/Mediator
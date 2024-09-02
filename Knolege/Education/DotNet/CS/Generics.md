#cs 
Generics it is ability to use some specific common types In classes
Example
```c#
class Command<TResponse>{


	public TRespomse SampleMethod()
	{
		//some logic
		return ...
	}
}

//Usage

public class SomeResponse{
//...
}

Var command = new Command<SomeResponse>();

```

also we can specify the generic type somehow by using `In` `out` `where`
`In` allow you to specify Generic type that can be used as an argument but can not be used as a return type
```c#
class Command<In TData>{
	public void SampleMethod(TData data)
	{
		//some logic
		return ...
	}
}
```

`Out` allow you to specify Generic type that can be used as return type but can not be used as an argument
```c#
class Command<Out TData>{
	public TData SampleMethod()
	{
		//some logic
		return ...
	}
}
```
`where` can be used to specify type of your Generic 
Examples

```c#
//TData shoud be a class
class Command<Out TData> where TData:class
```

```c#
//TData shoud be a struct
class Command<Out TData> where TData:struct
```

```c#
//TData shoud implemtnt IInterface
class Command<Out TData> where TData:IInterface
```


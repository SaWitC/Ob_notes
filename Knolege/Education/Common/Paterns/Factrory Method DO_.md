#paterns
https://refactoring.guru/design-patterns/factory-method
Factory method is a creational design pattern that provides an interface for creating objects in a superclass but allows subclasses to alter the type of object that will be created 


To implement pattern you have to create 
- Interface IFactory (use valid factory name)
- Class or classes that implement IFactory (or Your interface)
- specific product for each factory
- Define factoryCreator
```c#
//Factory interface
public interface IFactory{
	public IProduct Create();
}

//product interface
public interface IProduct{}

// Concreate factory
public class FactoryA:IFactory{
	public ProductA Create();
}
//concrete Product
public class ProductA:IProduct{}

//Factory method
//someDefenition it is a variable that we use to define whish factory we wan to use it cvan be some KEY|ID|TYPE|...
public IFactory GetFactory(someDefenition){
	switch(someDefenition){
		case ProductA:
		break;
	}
}
```
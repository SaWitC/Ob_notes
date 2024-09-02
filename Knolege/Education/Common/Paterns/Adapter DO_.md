#paterns 
Example
you have a car **class** with `drive()` method 
and horse **class** with `ride()` method

and for some reason you want to use horse instead of car but you can not replace car to a horse directly because they have different methods and properties

so in that case you can create an adapter
```c#
public interface ICar{
	void Drive();
}

public interface IRidingAnimal{
	void Drive();
}

public class SimpleCar:ICar{
	public void Drive(){
	//some logic
	}
}

public class Horse:IRidingAnimal{
	public void Ride(){
	//some logic
	}
}
//Adapter
public class RidingAnimalCarAdapter :ICar{
	private readonly IRidingAnimal ridingAnimal;
	public RidingAnimalCarAdapter(IRidingAnimal ridingAnimal)
	{
		this.ridingAnimal = ridingAnimal;
	}
	
	void Drive(){
		//some logic
		this.ridingAnimal.Ride();
		//some logic
	}
}
//USAGE
//Some method that get Icar as an argument
public void MethodThatUseCar(ICar car){
	car.Drive()
}

var horse = new Horse();
var adapter =new RidingAnimalCarAdapter(horse)

MethodThatUseCar(adapter);
```
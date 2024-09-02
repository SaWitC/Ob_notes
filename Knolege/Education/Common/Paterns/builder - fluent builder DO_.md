#paterns 
https://refactoring.guru/design-patterns/builder

Imagine a complex object that requires laborious, step-by-step initialization of many fields and nested objects. Such initialization code is usually buried inside a monstrous constructor with lots of parameters. Or even worse: scattered all over the client code.


Patter structure
![[Pasted image 20240816092629.png]]

Example :
```c#
//builder interface
public interface ISandwichBuilder{
	public void Reset();
	public void AddTomate();
	public void AddCucumber();
	public void AddBread();
	public void AddChees();
	//...
}
//Concrete builder
public class SmalSandwichBuilder : ISandwichBuilder
{
    private Product _product = new Product();

    public SmalSandwichBuilder()
    {
        this._product = new Product();
    }

    public void Reset() { this._product = new Product(); }
    public void AddTomate() { this._product.Add("tomate"); }
    public void AddCucumber() { this._product.Add("cucumber"); }
    public void AddBread() { this._product.Add("bread"); }
    public void AddChees() { this._product.Add("Chees"); }
    
    public Product GetProduct()
    {
        return _product;
    }
}
//Product class
public class Product
{
	private List<object> _parts = new List<object>();
	
	public void Add(string part)
	{
		this._parts.Add(part);
	}
	
	public string ListParts()
	{
		string str = string.Empty;
		for (int i = 0; i < this._parts.Count; i++)
		{
			str += this._parts[i] + ", ";
		}
		str = str.Remove(str.Length - 2); // removing last ",c"
		return "Product parts: " + str + "\n";
	}
}

//Director class (this class is used just to describe logic that need to create difficult objct)
public class Director
{
	private ISandwichBuilder _builder;
	
	public ISandwichBuilder Builder
	{
		set { _builder = value; } 
	}
	
	// The Director can construct several product variations using the same
	// building steps.
	public void BuildMinimalViableProduct()//object type 1
	{
		this._builder.AddBread();
	}
	
	public void BuildFullFeaturedProduct()//object type2
	{
		this._builder.AddChees();
		this._builder.AddBread();
		this._builder.AddTomate();
	}
	//...
}


//USAGE
static void Main(string[] args)
{
	// The client code creates a builder object, passes it to the
	// director and then initiates the construction process. The end
	// result is retrieved from the builder object.
	var director = new Director();
	var builder = new ConcreteBuilder();
	director.Builder = builder;
	
	Console.WriteLine("Standard basic product:");
	director.BuildMinimalViableProduct();
	Console.WriteLine(builder.GetProduct().ListParts());

	Console.WriteLine("Standard full featured product:");
	director.BuildFullFeaturedProduct();
	Console.WriteLine(builder.GetProduct().ListParts());

	// Remember, the Builder pattern can be used without a Director
	// class.
	Console.WriteLine("Custom product:");
	builder.AddChees();
	builder.AddBread();
	Console.Write(builder.GetProduct().ListParts());
}

```

**Fluent builder** example

```c#

public interface ISandwichBuilder
{
    public void Reset();
    public ISandwichBuilder AddTomate();
    public ISandwichBuilder AddCucumber();
    public ISandwichBuilder AddBread();
    public ISandwichBuilder AddChees();
}
public class SmalSandwichBuilder : ISandwichBuilder
{
    private Product _product = new Product();

    public SmalSandwichBuilder()
    {
        this._product = new Product();
    }

    public void Reset() { this._product = new Product(); }
    public ISandwichBuilder AddTomate() { this._product.Add("tomate");
        return this;
    }
    public ISandwichBuilder AddCucumber() { this._product.Add("cucumber"); return this; }
    public ISandwichBuilder AddBread() { this._product.Add("bread"); return this; }
    public ISandwichBuilder AddChees() { this._product.Add("Chees"); return this; }

    public Product GetProduct()
    {
        return _product;
    }
}
public class Product
{
    private List<object> _parts = new List<object>();

    public void Add(string part)
    {
        this._parts.Add(part);
    }

    public string ListParts()
    {
        string str = string.Empty;
        for(int i = 0; i < this._parts.Count; i++)
        {
            str += this._parts[i] + ", ";
        }
        str = str.Remove(str.Length - 2);
        return "Product parts: " + str + "\n";
    }
}
public class Director
{
    private ISandwichBuilder _builder;

    public ISandwichBuilder Builder
    {
        set { _builder = value; }
    }
    public void BuildMinimalViableProduct()//object type 1
    {
        this._builder.AddBread();
    }

    public void BuildFullFeaturedProduct()//object type2
    {
        this._builder.AddCucumber().AddBread().AddCucumber().AddTomate();
    }
}
```


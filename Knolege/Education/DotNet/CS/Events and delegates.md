#cs 
**Delegate** it is an object that represent a reference to the method and useing delegates we can run this mehods

to create delegate we have to use a keyWord **delagate** and return type
```cs
//Example
delegate void SomeMethod()
delegate bool IsTrue()
//sample method
void Hello(string text) =>Console.WriteLine(text)

//create object
SomeMethod somMethodVar;
//set value
somMethodVar = Hello

//use 
somMethodVar("hello text")
```
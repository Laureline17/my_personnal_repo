# Code review

The pratical work in week 4 it is to show our skills in code review. So we had to choose a code and to review it.<br> 

### The code that I had choose
```
class Car
{
  public string model;

  // Class constructor
  public Car()
  {
    model = "Mustang"; // Set the initial value for model
  }

  static void Main(string[] args)
  {
    Car Ford = new Car();
    Console.WriteLine(Ford.model);
  }
}
```

This code violate the general principe of the standard C# coding conventions.
In fact, it uses an uppercase property name "model" which should typically be in PascalCase.  
So, it violates this principle in terms of naming conventions.<br>

This code also violate some best practice rules. 
The code doesn't use recognised commenting conventions. In fact there is any comments on the code.
It also doesn't use appropriate name for variables. For example "model" should be written "Model" and "Ford" should be written "ford".

And to finish, the code exhibit one code smells : Primitive Obsession.
This code uses a primitive data type (integer) for representing the model property of the Car class.
Which could potentially lead to issues or limitations if more complex behavior or validation is needed for the model. 
In such cases, it's often better to use a dedicated class or enumeration to represent this concept.

```
using System;

class Car
{

    /// Gets or sets the model of the car.
    public string Model { get; set; }


    /// Initializes a new instance of the <see cref="Car"/> class with a default model.
    public Car()
    {
        Model = "Mustang"; // Set the initial value for the model
    }


    /// Main method to demonstrate the Car class.

    static void Main(string[] args)
    {
        Car fordCar = new Car();
        Console.WriteLine("Car Model: " + fordCar.Model);
    }
}
```

This code is a better solution because, as you can see, there is a lot of clear comments. 
Also, the variables have names that are appropriate. For example, I replace "Ford" by "fordCar" so it is more clear.
And I used a property (Model) to represent the car's model instead of a public field, avoiding primitive obsession.



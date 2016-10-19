---
layout: post
title:  "To Be .self Or Not To Be, That Is The Question - Class vs Instance Methods"
date:   2016-10-18 22:28:43 -0400
---


Let's get right into it.  A Ruby class method is described, as a method that is called on a class.  A Ruby instance method is described, as a method that is called on an instance of a class.  Ok so now we know their definitions, but what does that actually mean?  What are their jobs, so to speak?  

Let's look at an example.  Coming from an automotive background I will use a Car class.
```
class Car
    def initialize(year, make, model)  #instance method
        @year = year
        @make = make
        @model = model
    end
    
    def self.horn                      #class method
        puts "HONK! HONK!"
    end
end
```
This is a very simple example but represents the two different methods.  First we will start with the instance method.  As we do keep this in mind.  Use instance methods when you need to act on a particular instance of the class.  Every car in the world, or instance of a car, has a year, make, and model.  The arguments for the initailize can change for each instance of the car.  So for example:
`
BMW = Car.new(2015, "BMW", "X5")   =>#<Car:0x007fcbb600e9a0 @make="BMW", @model="X5", @year=2015>
`
Here we have an instance of the Car class.  Look what happens if we forget the `new` keyword.
```
BMW = Car(2015, "BMW", "X5") =>#NoMethodError: undefined method  'Car'
```
We must always use the `new` keyword when creating a new instance of Car.


Next up we have the class method.  If class method is described as a method called on a class what does that actually mean?  When thinking about a class method remember that that method is not tied specifically to each 'instance' of that class.  In our example above we have a class method that is called 'horn'.  When thinking about cars all cars have a horn.  So horn would never change depending on an instance of the Car class. Now let's look at the structure a little bit.  There is other ways of defining this method but I think this way is the simplest to understand.  If we now called the horn method we would get;
```
Car.horn
HONK! HONK!
```
Notice the difference in how we defined the horn method.  We use `self.horn` to define that `horn` is a class method of the Car class.  Then when we called it we used `Car.horn` to specify the class that we made.

In conclusion, it is tough sometimes trying to figure out when to use a class method vs a instance method.  But if you keep this in mind it will help.  When the functionality of the method does not belong to an instance of a class then use a class method.  But when the method deals with the identity of the instance such as calling properties on the object, or invoking behaviour use an instance method.

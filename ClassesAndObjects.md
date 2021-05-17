# Classes and Objects
Luke Morrison - 12 May 2021

[Back](/README.md)

## First, An Example

```ruby
class Car

    @@wheels = 4

    def initialize(colour, number_of_seats=2)
        @speed = 0
        @colour = colour
        @passengers = ['John', 'Susan', 'Mike']
        @number_of_seats = number_of_seats
    end
    
    def get_current_speed()
        @speed
    end

    def get_number_of_passengers()
        num_passengers = @passengers.count
        num_passengers
    end
end
```

## Variables

Similar to many other languages, objects in Ruby can contain local variables, instance variables (properties), and class variables (static properties). There are also *Global Variables* but we will not discuss them in the object context.

**Local Variables** - Local variables are the variables that are defined in a method. Local variables are not available outside the method.

**Instance Variables** - Instance variables are available across methods for any particular instance or object. That means that instance variables change from object to object. Instance variables are preceded by `@` followed by the variable name. These variables are conceptually the same as object *properties*.

**Class Variables** − Class variables are available across different objects. A class variable belongs to the class and is a characteristic of a class (similar to a static variable in other languages). They are preceded by `@@` and are followed by the variable name. 

## Instantiating an Object
To create a new object instance, you can use the `new` method on the class:

```ruby
    my_car = Car.new('red')

    num_passengers = my_car.get_number_of_passengers() # 3
```

Notice that the `Car` class expects one parameter, `colour`, when being created. The second parameter `number_of_seats` is optional as long as a default value has been defined.

[`TRY IT OUT`][try]

## Accessing Properties (Class & Instance Variables)

Like many other languages, you will have both static properties (Class Variables) and instance properties (Instance Variables).  If you define a class variable, you may access it on the Class itself:

```ruby
class Car
    @@num_wheels = 4
end

num_wheels = Car.num_wheels # => 4
```

If you instead wish to access an instance variable, you must access the variable on the instance:
```ruby
class Car
    def initialize(colour)
        @colour = colour
    end
end

my_car = Car.new('red')
colour = my_car.colour # => 'red'
```

[`TRY IT OUT`][try]

## *Doing Things* With Methods

So far we have talked about an object's properties - tickets for sale, hair colour, weapon level, number of golden rings, etc.  But knowing these values isn't enough; we also need to change them.  Methods are what you could define as an objects actions - what it can *do*.

A nice thing about classes is that they can and should maintain their own state.  This means that only the object should be able to change itself (usually). Methods should be written to desribe and object taking action, rather than having action taken upon it.

An simple example:
```ruby
class Character
    
    def initialize(hair_colour)
        @hair_colour = hair_colour
    end

    def set_hair_colour(colour)
        @hair_colour = colour
    end
end
```

Here you can see that we are allowing the `Character` object to set its own hair colour rather than simply changing its property. We will discuss about why this is in [Getters and Setters](#getters-and-setters).

## Inheritance

Cars however are only a narrow cut of what we would consider to be a `Vehicle`.  In this case, it would make sense for us to allow the `Car` class to *inherit* properties of the `Vehicle` class:

```ruby
# The parent class - vehicle.rb
class Vehicle
    def initialize(colour)
    @colour = colour
    end
end
```
```ruby
# The child class - car.rb
require './lib/vehicle.rb'

class Car < Vehicle
    def initialize(colour)
        super(colour)
    end
end

car = Car.new('blue')
colour = car.colour # => 'blue'
```

You will notice several things here. Firstly, we are defining the `colour` on the car, but it is really being assigned as a local variable on the vehicle.  With the syntax above we can say that `Car` inherits from `Vehicle`.  In this configuration, the Vehicle is expecting a colour, however creating a new *Vehicle* isn't very useful to us - at the end of the day, we want a *Car*.  In order to accomplish this, we use the `super()` function.  

The `super()` function essentially acts as a `new()` method, but is only applicable when an object is inheriting from a parent class.  In this case, `super()` expects to receive any parameters listed in the *parent's* `initialize()` method - you are directly feeding this method with `super()`.

To inherit or *extend* a parent class, we use the `<` in the class' definition. Don't forget to `require` your parent class at the top of the file.

[`TRY IT OUT`][try]

## Accessors

![lightspeed](https://media2.giphy.com/media/12haGO61oFZ28w/giphy.gif)

Now by now you may have thought,"hmmm, but if I change the warp-speed cooefficent in the Millenium Falcon, would I have stranded a Princess in space?" The answer is **yes**, which is why there is no way the Millenium Falcon would allow that. Luckily, the Falcon is written Ruby...

```ruby
class MilleniumFalcon < Spaceship

    @warp_speed_const = 3.454221
    @crew = ['Luke', 'Leia', 'Chewie', 'Han Solo', 'C-3PO', 'R2D2']

    # Conduct aircraft lightspeed jump
    def warp()
        # This function exists somewhere else
        return some_crazy_lightspeed_algorithm(@warp_speed_const)
    end
end
```

In this example, we can see that this constant is used in a critical piece software, so it is important that this value can't change. *Note that this value is specific only to the Millenium Falcon*. Ruby can do a lot of this protection with attribute accessors: `attr_reader`, `attr_writer`, `attr_accessor`.

- `attr_writer` allows you to change an object's property, but not read it.
- `attr_reader` allows you to read the object's property, but not change it.           
- `attr_accessor` allows both reading and writing of an object's property - but remember the Falcon example.

We may want to *read* the warp-speed constant, but definitely not write it:

```ruby
class MilleniumFalcon < Spaceship

    attr_reader :warp_speed_const
    # other methods here...

end

falcon = MilleniumFalcon.new
falcon.warp_speed_const # => 3.454221
```

Trying to write to the Falcon without without an `attr_writer` or `attr_accessor` will return an error.

Remember that accessors apply only to an object being read or written externally.  An object may change it's own properties freely, which leads us to...

[`TRY IT OUT`][try]

## Getters and Setters

![spider man pointing meme](https://i.imgur.com/C87xx6T.jpg?fb)

Ok, so clearly setting a property is important, so how can I do this without single handedly crippling the Rebel Alliance? With a *getter* or *setter*, of course.  

**Getters** allow you to receive an object property with a method.  Perhaps you want to strictly control access with accessors but would still like to get certain information from the flight computer?

```ruby

class MilleniumFalcon < Spaceship

    @warp_speed_const = 3.454221

    def get_warp_speed_constant()
        @warp_speed_const
    end
    # other methods here...
end
```

Now, we have a clean, intentional way of acquiring the warp-speed constant without having any ability to change the Falcon itself.  

**Setters** work in the opposite way.  Obviously the engineer who created Her will need to change the warp-speed constant.  So a setter is a good candidate for this type of situation because it allows you to control *how* the property can change.

Let's imagine that the warp-speed constant actually has an acceptable range:
```ruby
class MilleniumFalcon < Spaceship

    @warp_speed_const = 3.454221

    def set_warp_speed_constant(new_constant)

        if(new_constant < 3.46 && new_constant >= 3.44)
            @warp_speed_const = new_constant
        end

    end
end
```

Notice that if a value is passed outside of this acceptable range, the warp speed constant is not changed. Therefore, our setter allows us to more tightly control how a user may interact with our object. Obi-Wan can rest easy knowing our New Hope is alive due to rigorous software engineering.

[`TRY IT OUT`][try]

## Further Reading

Class - https://ruby-doc.org/core-3.0.1/Class.html
Object - https://ruby-doc.org/core-3.0.1/Object.html

[try]: "https://try.ruby-lang.org/"

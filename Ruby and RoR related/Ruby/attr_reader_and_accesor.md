### Method to Return Instance Variable
Let's say, that the instance of CoffeeMaker wants to access the condition of coffee. In that case, we would have a problem. In Ruby, instances of CoffeeMaker can't access instance variables just like that. Only the methods can access instance variables. Let's see an example:
```
class CoffeeMaker
  def initialize(condition)
    @condition = condition
  end
end

coffee1 = CoffeeMaker.new("hot")
puts coffee1.condition
Output : Error
```

In order to fix this error, we can create a method which will return the instance variable.

```
class CoffeeMaker
  def initialize(condition)
    @condition = condition
  end

  def condition
    @condition
  end
end

coffee1 = CoffeeMaker.new("hot")
puts coffee1.condition
```
**In Ruby, we can use** `attr_reader` **to give object instances a simpler way to read the instance variables**
```
class CoffeeMaker
  attr_reader :colour, :temperature, :quantity, :origin, :brand
  def initialize(colour, temperature, quantity, origin, brand)
    @colour = colour
    @temperature = temperature
    @quantity = quantity
    @origin = origin
    @brand = brand
  end
end

coffee1 = CoffeeMaker.new("dark", "hot", "small", "Brunei", "Domos")
puts coffee1.colour
puts coffee1.temperature
puts coffee1.quantity
puts coffee1.origin
puts coffee1.brand
```
---

### Method to Set Instance Variable
To give instances access to the instance variables, we need to define new methods like we do here:
```
class CoffeeMaker
  def initialize(condition)
    @condition = condition
  end
  # Access the instance variable value
  def condition
    @condition
  end
  # Change the instance variable value that we can access
  def condition=(condition)
    @condition = condition
  end
end

coffee1 = CoffeeMaker.new("hot")
coffee1.condition = "cold"
puts coffee1.condition
```
Now imagine, that the CoffeeMaker has not one but five instance variables. For this to work, we'll have to create 5 methods to provide access to read them and 5 methods to change their respective values. 
In Ruby, we can use `attr_writer` along with `attr_reader` to give object instances a simpler way to update the instance variables
```
class CoffeeMaker
  attr_reader :colour, :temperature, :quantity, :origin, :brand
  attr_writer :colour, :temperature, :quantity, :origin, :brand
  def initialize(colour, temperature, quantity, origin, brand)
    @colour = colour
    @temperature = temperature
    @quantity = quantity
    @origin = origin
    @brand = brand
  end
end

coffee1 = CoffeeMaker.new("dark", "hot", "small", "Brunei", "Domos")
coffee1.colour = "light"
puts coffee1.colour
coffee1.temperature = "cold"
puts coffee1.temperature
coffee1.quantity = "large"
puts coffee1.quantity
coffee1.origin = "Damascus"
puts coffee1.origin
coffee1.brand = "Misty"
puts coffee1.brand
```
---

### Method to Set and Get Instance Variable attr_accessor

Look at the following code:
```
class CoffeeMaker
  attr_reader :colour, :temperature, :quantity, :origin, :brand
  attr_writer :colour, :temperature, :quantity, :origin, :brand
  def initialize(colour, temperature, quantity, origin, brand)
    @colour = colour
    @temperature = temperature
    @quantity = quantity
    @origin = origin
    @brand = brand
  end
end

coffee1 = CoffeeMaker.new("dark", "hot", "small", "Brunei", "Domos")
coffee1.colour = "light"
puts coffee1.colour

coffee1.temperature = "cold"
puts coffee1.temperature

coffee1.quantity = "large"
puts coffee1.quantity

coffee1.origin = "Damascus"
puts coffee1.origin

coffee1.brand = "Misty"
puts coffee1.brand
```
If you look at this part of the code,
```
attr_reader :colour, :temperature, :quantity, :origin, :brand
attr_writer :colour, :temperature, :quantity, :origin, :brand
```
it seems like a complicated way to achieve a simple thing: access and change instance variables.

Ruby provides us with `attr_accessor` to simplify this code:
```
class CoffeeMaker
  attr_accessor :colour, :temperature, :quantity, :origin, :brand
  def initialize(colour, temperature, quantity, origin, brand)
    @colour = colour
    @temperature = temperature
    @quantity = quantity
    @origin = origin
    @brand = brand
  end
end

coffee1 = CoffeeMaker.new("dark", "hot", "small", "Brunei", "Domos")
coffee1.colour = "light"
puts coffee1.colour

coffee1.temperature = "cold"
puts coffee1.temperature

coffee1.quantity = "large"
puts coffee1.quantity

coffee1.origin = "Damascus"
puts coffee1.origin

coffee1.brand = "Misty"
puts coffee1.brand
```

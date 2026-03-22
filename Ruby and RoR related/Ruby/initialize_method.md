### Initalize method or Constructor in Ruby
Ruby has a special method called initialize. The method initialize is called when a class creates an instance.

This initialize method is in all the classes sitting at the top doing nothing. In reality, our CoffeeMaker looks like this.
```
class CoffeeMaker
  def initialize
  end
end
```

When we are saying Coffeemaker.new("hot"), we are passing the argument hot to the `initialize method`. So far, we have not been using it. But now let's use it:
```
class CoffeeMaker
  def initialize(condition)
    @condition = condition
  end

  def serve
    puts "This coffee is being served #{@condition}"
  end
end

coffee1 = CoffeeMaker.new("hot")
coffee1.serve
```
```
class Carmaker
  def initialize(color)
    @color = color
  end

  def current_color
    puts "Color of this car is #{@color}"
  end
end

car1 = Carmaker.new("red")
car1.current_color
```
---

### Required Argument in initialize
In the case given below, the `initialize` method takes one argument:
```
class CoffeeMaker
  attr_reader :condition
  def initialize(condition)
    @condition = condition
  end
end

coffee1 = CoffeeMaker.new("hot")
puts coffee1.condition
```
While calling the `new` method, we can pass the value `hot`. **We can also tell Ruby that if no value is passed, then take hot as the default value.**
```
class CoffeeMaker
  attr_reader :condition
  def initialize(condition = "hot")
    @condition = condition
  end
end

coffee1 = CoffeeMaker.new
puts coffee1.condition
```
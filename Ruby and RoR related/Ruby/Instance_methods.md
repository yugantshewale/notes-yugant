### So, let's define some methods. A method starts with def and ends with end.

```
class Car
  def play_music
    puts "playing music"
  end

  def stop
    puts "stopping the car"
  end

  def turn_lights_on
    puts "turning the lights on"
  end
end

car1 = Car.new
car1.play_music
car1.stop
car1.turn_lights_on
```
Classes are used to make instances. In order for instances to do something, the class needs to have those methods.

Once again note that a method always starts with `def` and the method ends with `end`.

---

### Calling instance methods
```
class Biscuit
  def eat
    puts "eating biscuit"
  end

  def gift
    puts "biscuit is a wonderful gift"
  end
end

biscuit1 = Biscuit.new

biscuit1.eat
biscuit1.gift
```
After defining the method we need to call the method for that method to act. The way we call that method is by having the name of the instance then a dot and then the method name.

For example when we write `biscuit1.eat` then it means that we are calling method `eat` on the instance `biscuit1`.

When we write `biscuit1.gift` then we are calling method `gift` on the instance `biscuit1`.

If we write just eat or gift then we will get error.

---

### Calling instance methods with arguments
```
class Biscuit
  def eat
    puts "eating biscuit"
  end

  def gift
    puts "biscuit is a wonderful gift"
  end

  def bake(temperature)
    puts "baking biscuit at #{temperature} degrees"
  end
end

biscuit1 = Biscuit.new

biscuit1.eat
biscuit1.gift
biscuit1.bake(200)
```
When we define a method with arguments, we need to pass those arguments when we call the method.

For example when we write `biscuit1.bake(200)` then it means that we are calling method `bake` on the instance `biscuit1` with argument `200`.

If we write just bake then we will get error.

---

### Multiple Arguments
```
class Biscuit
  def eat
    puts "eating biscuit"
  end

  def gift
    puts "biscuit is a wonderful gift"
  end

  def bake(temperature, time)
    puts "baking biscuit at #{temperature} degrees for #{time} minutes"
  end
end

biscuit1 = Biscuit.new

biscuit1.eat
biscuit1.gift
biscuit1.bake(200, 10)
```
When we define a method with multiple arguments, we need to pass those arguments when we call the method.

For example when we write `biscuit1.bake(200, 10)` then it means that we are calling method `bake` on the instance `biscuit1` with arguments `200` and `10`.

If we write just bake then we will get error.

---

### Instance Methods Only Work on Instances
```
class Biscuit
  def eat
    puts "eating biscuit"
  end

  def gift
    puts "biscuit is a wonderful gift"
  end
end

biscuit1 = Biscuit.new

Biscuit.eat
Output : Error
```
We got an error because the **method exists only on the instances and not on the class**. These methods are also called **instance methods** because these `methods can only be called by an instance and not by the class`.

---

### Split price in two methods
So far we have been using puts in our methods.
```
class Coffeemaker
  def price(condition)
    price = condition == "hot" ? "$4" : "$3"
    puts "The cost of the coffee is #{price}"
  end
end

coffee1 = Coffeemaker.new
coffee1.price("hot")
```
In the above case the `method price doesn't return anything`. It prints the output. Let's change the code so that the price method returns the message and some other method prints the output.

```
class Coffeemaker
  def price(condition)
    price = condition == "hot" ? "$4" : "$3"
  end

  def print(condition)
    cost = price(condition)
    puts "The cost of the coffee is #{cost}"
  end
end

coffee1 = Coffeemaker.new
coffee1.print("hot")
```
```
class CapitalCityFinder

  def get_capital_city(country)
    data = { France: "Paris", India: "New Delhi", England: "London" }
    city = data[country.to_sym] # to_sym converts the string to symbol
    return city
  end

  def info(country)
    city = get_capital_city(country)
    puts "The capital of #{country} is #{city}"
  end
end

finder = CapitalCityFinder.new
finder.info("India")
```

Let's say that we want to return nil if the country is not present.
```
class CapitalCityFinder

  def get_city(country)
    data = { France: "Paris", India: "New Delhi", England: "London" }
    
    return nil if country == nil
    city = data[country.to_sym]
    return city
  end

  def info(country)
    city = get_city(country)
    if city == nil
      puts "Sorry we don't have info about the country #{country}"
    else
      puts "The capital of #{country} is #{city}"
    end
  end
end

finder = CapitalCityFinder.new
finder.info("Japan")
``` 
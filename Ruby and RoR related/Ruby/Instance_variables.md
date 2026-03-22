### Instance Variables

Instance variables are variables that are defined within a class and are accessible within the class and its instances. They are prefixed with an `@` symbol.
```
class Carmaker
  def turn(direction)
    @direction = direction
    puts "The car is turning"
  end

  def current_direction
    puts "The current direction is #{@direction}"
  end
end

car1 = Carmaker.new
car1.turn("left")
car1.current_direction
```
As we can see, the instance variable `@direction` is accessible within the class and its instances. This allows us to store and retrieve data specific to each instance of the class. 

---

### Class level instance variable
A class level instance variable is a variable that belongs to a class but is accessible to all instances of that class. They are prefixed with a `@@` symbol.

It is different from a regular instance variable, which is specific to each individual object.

```
class Counter
  @@count = 0

  def initialize
    @@count += 1
  end

  def self.count
    @@count
  end
end

object1 = Counter.new
object2 = Counter.new

puts Counter.count
```
In this example, we have a Counter class that keeps track of the count of objects created.

The @@count class level instance variable is being used to store and update the count.

**Each time a new instance of the Counter class is initialized, the @@count variable is incremented**.

The class method `count` allows us to retrieve the total count of objects.

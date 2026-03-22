### Mixin modules
In Ruby, a Class can have methods. Similarly, a **Module can also have methods.**

However, **we can't call new on a Module**. A **module needs to be mixed in with a class**. In other words,**we need to put the module in a class and then we need to instantiate that class**. Then, that instance will have access to the methods defined in the module.

```
module Info
  def name
    puts "Roger Smith"
  end
end
```
```
module Info
  def name
    puts "Roger Smith"
  end
end

class Person
  include Info
end

p1 = Person.new
p1.name
```
---

### Utility of Modules
Let's say, that we have a method called `calculate_speed`. We want this method to be present in classes **Car, Rocket, and Ship**.

One way to do this is by adding the method in each of these classes:

```
class Car
  def calculate_speed
    puts "current speed is now visible on your dashboard"
  end
end

class Rocket
  def calculate_speed
    puts "current speed is now visible on your dashboard"
  end
end

class Ship
  def calculate_speed
    puts "current speed is now visible on your dashboard"
  end
end
```
But there is a problem with this approach. When we want to change puts `"current speed is now visible on your dashboard"` to puts `"current speed is now visible on your homepage"` we'll need to go into all the classes and change each method individually. This isn't ideal.

We want this method to be at only one place, so that if we make changes to it, we get to use the updated method everywhere else.

We can do that by putting this method in a module. 

```

module Speed
  def calculate_speed
    puts "current speed is now visible on your dashboard"
  end
end

class Car
  include Speed
end

class Rocket
  include Speed
end

class Ship
  include Speed
end
car1 = Car.new
car1.calculate_speed

car2 = Car.new
car2.calculate_speed

rocket1 = Rocket.new
rocket1.calculate_speed
```
Try changing the message in `calculate_speed` and you'll see that the result gets updated in all the instances.

---

### Instance Method Over Module Method
Sometimes, we might have a method defined by the same name in both the class as well as in the module. In that case, which method will Ruby choose? The answer depends on what path Ruby takes for looking up methods.
```
module Info
  def name
    puts "Roger Smith"
  end
end

class Person
  include Info
  def name
    puts "name from the Person class"
  end
end

p1 = Person.new

Output : name from the Person class
```
**In the example given above, we can see that p1 uses the name method that was defined in the class Person instead of the one defined in the module Info.**

Thus we can see, Ruby first looks at the instance methods of the class itself. If it does not find the method there, then Ruby will look for the method in the included modules.

---

### Last Module Wins

A class can include any number of modules.**If there are two modules with the same method name, then the module which was included later wins.**
```
module Info1
  def name
    puts "Roger Smith"
  end
end

module Info2
  def name
    puts "Mary Brett"
  end
end

class Person
  include Info1
  include Info2
end

p1 = Person.new
p1.name
Output : Mary Brett
```
`As we can see, both the modules have the same method name.` In this case, the module that was included later wins. Change the order of the modules inside the class and then notice how the result changes.

---

### Ancestors
In large programs, we cannot remember the order in which Ruby will look up methods. It turns out, we don't need to remember that.

We can ask Ruby to give us that order.
We can use `ancestors` method to get the order in which Ruby looks up methods.

```
module Info1
  def name
    puts "Roger Smith"
  end
end

module Info2
  def name
    puts "Mary Brett"
  end
end

class Person
  include Info1
  include Info2
end

puts Person.ancestors
Output : [Person, Info2, Info1, Object, Kernel, BasicObject]
```
Here, we can see that first Ruby will look for the method in the Person class itself and then in module Info2 and then in module Info1.

For the modules, it's simply preferring the ones that are included later, so essentially, it will feel like it is checking for the method in a bottom-to-top manner.

We can also ask Ruby what modules are included. Using `included_modules` method, we can get the list of modules included in a class.

```
module Info1
  def name
    puts "Roger Smith"
  end
end

module Info2
  def name
    puts "Mary Brett"
  end
end

class Person
  include Info1
  include Info2
end

puts Person.included_modules
Output : [Info2, Info1, Kernel]

```
---

### Modules Are Not Copy Paste
```
module Info
  def name
    puts "Roger Smith"
  end
end

class Person
  include Info
end

module Info
  def name
    puts "Mike Bohanan"
  end
end

p1 = Person.new
p1.name
Output : Mike Bohanan
```
As we can see, the result is Mike Bohanan.` Do not think that including a module is equivalent to copy pasting all the module code into the class. Including a module does not work like that.`

`Including a module is more like setting up a link in the method lookup.` 

When p1 is looking for the method name, then first Ruby will check if class Person has any instance method called name.The answer is No.

Then, Ruby will check if class Person includes any modules. The Answer is Yes. Module Info is included.

Then, Ruby checks if that module has a method called name. Answer is Yes. Now, Ruby executes that method.

---

### Nested Hash Configuration
Nested configuration involves configurations within other configurations, creating a hierarchical structure of settings.

This lesson focuses on nested hash configuration. However, nested configurations can also be created using other objects such as classes or arrays.
```
game_config = {
  player: {
    name: "John",
    level: 10,
    health: 100
  },
  world: {
    difficulty: "hard",
    size: "large"
  },
  graphics: {
    resolution: "1920x1080",
    quality: "high"
  }
}

puts game_config
```
In the code above, game_config utilizes hashes, which are key-value pairs.

We create a hash for each level of configuration and arrange them within each other as needed.

---

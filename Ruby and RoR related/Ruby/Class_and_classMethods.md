### Defining class in Ruby
 Here is how in Ruby we declare our class:
```
class Carmaker
end
```
Ruby allows us to use `new` to make a car out of the Carmaker class. new is truly a magical thing in Ruby. It can make a car out of a Carmaker.
```
class Carmaker
end

car1 = Carmaker.new
```
***Notice that Carmaker starts with a capital letter.*** 

So far, we have never used anything that starts with a capital letter. This is because so far we have been dealing with variables. ***In Ruby, all variables must start with a small letter.***

***A class is a special thing. A class name must start with a capital letter.***

We used new to create a car out of the Carmaker. `We need a word to describe what is created out of the class. That word is instance.` Here, we created an instance of car from the class Carmaker.

`An instance is like a real car that is built out of the car making machine.` When we say we have an instance of the class Carmaker, then what we mean is that we have a car that is created from the class Carmaker.
```
class Coffeemaker
end

coffee1 = Coffeemaker.new
```
```
class Biscuitproducer
end

biscuit1 = Biscuitproducer.new
```
---
### Many Instances of a Class
```
class Carmaker
end

car1 = Carmaker.new
car2 = Carmaker.new
car3 = Carmaker.new
```
---

### What is the Class
Ruby allows us to ask an instance what is their class. Let's ask car1, what is the name of its class:

```
class Carmaker
end

car1 = Carmaker.new
puts car1.class
Output: Carmaker
```
---

### What is the Class of String and Integer
```
hello = "Hello BigBinary Academy"
puts hello.class

age = 18
puts age.class
Output : String
         Integer
```
---

### Checking class name
If we want to **check if an instance is from a given** Class then we can use method `is_a?`.
```
class Carmaker
end

car1 = Carmaker.new
puts car1.is_a?(Carmaker)
Output: true
```
---

### Class methods
`Class methods are used for implementing functionality that is associated with a particular class`.

They are not tightly bound to individual objects, called instances of that class.
```
class Car
  def self.wheels
    puts "The car has 4 wheels."
  end
end

Car.wheels
```
**Syntax to define a Class method:**
```
class ClassName
  def self.method_name
  # do something
  end
end
```

It is necessary to add the word `self` when defining a Class Method.

Without the self word, this becomes an instance method which can only be called on an instance of the class.


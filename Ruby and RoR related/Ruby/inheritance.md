### Inheritance in Ruby
```
class Vehicle
  def number_of_wheels
  end
  def number_of_seats
  end
  def owner_name
  end
  def year_of_manufacture
  end
end

class EnginePoweredVehicle < Vehicle # EnginePoweredVehicle inherits from Vehicle
  def fuel_type
  end
  def chassis_number
  end
  def engine_manufacturer
  end
  def engine_size_in_cc
  end
  def number_of_cylinders
  end
  def maximum_power_in_hp
  end
  def maximum_torque_in_nm
  end
  def is_turbocharged
  end
end

class Bicycle < Vehicle # Bicycle inherits from Vehicle
  def chain_manufacturer
  end
  def additional_seating_at_carrier
  end
end

class Car < EnginePoweredVehicle # Car inherits from EnginePoweredVehicle
  def has_automatic_transmission
  end
  def body_type
  end
end

class Truck < EnginePoweredVehicle # Truck inherits from EnginePoweredVehicle
  def cargo_carrying_capacity
  end
  def number_of_axles
  end
end
```

<img src="https://d3rtegloudc34g.cloudfront.net/_next/image/?url=https%3A%2F%2Fik.imagekit.io%2Fd9mvewbju%2FCourse%2Finheritance_Qe4moSLJn.png&w=3840&q=75" width="1000" height="1000">

---

### Inheritance Classes
```
# The super-class
class Vehicle
  def number_of_wheels(wheels)
    "Has #{wheels} wheels"
  end

  def number_of_seats(seats)
    "Has #{seats} seats"
  end

  def owner_name(owner)
    "The owner is #{owner}"
  end
end

# The sub-class
class Bicycle < Vehicle
  def chain_manufacturer
    "Chain Manufactured by Shimano"
  end

  def additional_seating_at_carrier
    "Additonal seat available"
  end
end

# Instance
trekbike = Bicycle.new

puts trekbike.number_of_wheels(2)

puts trekbike.number_of_seats(2)

puts trekbike.owner_name("Renu Sen")

puts trekbike.chain_manufacturer

puts trekbike.additional_seating_at_carrier
```

<img src="https://d3rtegloudc34g.cloudfront.net/_next/image/?url=https%3A%2F%2Fik.imagekit.io%2Fd9mvewbju%2FCourse%2Finheritance_Qe4moSLJn.png&w=3840&q=75" width="1000" height="1000">

---

### Understanding Super
Let’s look at a simple example, to understand how `super` keyword works:
```
class Car
  def fast
    "Cars are fast!"
  end
end

class ElectricCar < Car
  def fast
    super + " but an electric car can accelerate faster!"
  end
end

tesla = ElectricCar.new
puts tesla.fast
Output: Cars are fast! but an electric car can accelerate faster!
```
So,**using super we can call the same method as defined in the super-class**.

This **helps us to re-use methods that exists in super-class, and modify them as per our needs in the subclass.**

---

### Difference between Super and Super()
When we use `super`, Ruby invokes the method with same name from parent class, along with the arguments that were passed to that method.

eg :
```
class Car
  def runs_on(name, fuel)
    "#{name} runs on #{fuel}."
  end
end

class PetrolCar < Car
  def runs_on(name, fuel)
    super
  end
end

ferrari = PetrolCar.new
puts ferrari.runs_on("Ferrari", "petrol")
Output : Ferrari runs on petrol.
```
But, when we call with `super()`, it doesn’t pass any arguments to the parent. You can use `super()` when you just want to call the method inherited from Parent without passing any arguments.

And, you can use `super(arg1, arg2, …)` to pass only some specified arguments to the inherited method.
```
class Car
  def runs_on(fuel)
    "Your car runs on #{fuel}."
  end
end

class ElectricCar < Car
  def runs_on
    super("battery")
  end
end

tesla = ElectricCar.new
puts tesla.runs_on
Output : Your car runs on battery.
```
---
### Inheriting Initialize method
```
class Car
  def initialize
    @driving = "You are driving a car"
  end
end

class PetrolCar < Car
  def drive
    @driving + ", which is petrol powered."
  end
end

class ElectricCar < Car
  def drive
    @driving + ", which is battery powered."
  end
end

ferrari = PetrolCar.new
puts ferrari.drive
tesla = ElectricCar.new
puts tesla.drive
Output : 
You are driving a car, which is petrol powered.
You are driving a car, which is battery powered.
```
In the above code example, we could observe that the `@driving` was written only once in parent class and could be used in child classes. So that means the same `initialize` method is inherited by child classes from parent.

```
class Car
  def initialize
    @driving = "You are driving a car"
  end
end

class PetrolCar < Car
  def initialize
    super
    @speed = "420"
  end
  def drive
    @driving + ", which is petrol powered." + @speed
  end
end
ferrari = PetrolCar.new
puts ferrari.drive
```
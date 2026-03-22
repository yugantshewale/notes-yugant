## Dig

### dig in Ruby Hashes
Look at the following example:
```
data = {
    players: [
        {
          name: "Oliver",
          wins: 22
        },
        {
          name: "Renu",
          wins: 23
        }
    ]
}
puts data[:players][0][:name]
puts data[:players][1][:name]
```
To get the name of the first player, we can use `data[:players][0][:name]`.
But if we tried to get the name of a player whose information doesn't exist, this will cause an error.

Sometimes, we might not know beforehand which information exists in the data. This is why, it is important that we have a way to access the information without resulting in an error. Ruby gives us `dig` for this purpose.
```
data = {
    players: [
        {
          name: "Oliver",
          wins: 22
        },
        {
          name: "Renu",
          wins: 23
        }
    ]
}

puts data.dig(:players, 0, :name)
puts data.dig(:players, 1, :name)
puts data.dig(:players, 2, :name)
```
As you can see, searching for a non-existent value does not create an exception. Instead, it simply shows a nil value.

Also, dig is easier to read too!

---

### dig in Ruby Arrays

Look at the following example:
```
data = [
  12, ["top", "bottom"], [1, [100, 101]]
]
puts data[1][0]
puts data[2][1][0]
```
To get the number 101, we can use data[2][1][1]. 
But if we tried to get to a nested array which doesn't exist and then asked for a value in it, this will cause an error.
```
data = [
  12, ["top", "bottom"], [1, [100, 101]]
]

puts data.dig(0)
puts data.dig(1, 0)
puts data.dig(2, 1, 0)
puts data.dig(3, 1, 0)
```
As you can see, searching for a value on a non-existent array does not create an exception. Instead, it simply shows a nil value.

---

## Safe Navigation Operator

### Safe Navigation Operator

Ruby provides us with `&.` which is called the Safe Navigation Operator. Let's look at it in action:
```
class User
  attr_accessor :name
  def initialize(name)
    @name = name
  end
end

user1 = User.new('Oliver')

# Method 1
if user1 && user1.name
  puts "We have a new user."
end

# Method 2 using &.
if user1&.name
  puts "We have a new user."
end
```
The `&.` checks if user1 exists and if the name method exists on user1. We can see that it is a much simpler approach compared to checking the existence of each method at every subsequent stage.

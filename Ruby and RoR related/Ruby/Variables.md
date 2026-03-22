## Variables

### Using Variables
```
name = "John Smith"
intro = "My name is " + name
puts intro
```
 In this example given above, `name` is a `variable`. We are assigning the value of John Smith to the variable `name`. `intro` is also a variable to which a value is being assigned.
 Variables are also reusable.
 
 eg:
 
 ```
 number1 = 10
number2 = 20
result = number1 + number2

sentence = "Result of adding 10 and 20 is " + result.to_s

puts sentence
```
**In Ruby, variable names must start with an underscore or with a lowercase letter.**

full_name, get_age, and fixed_price are good examples of Ruby variable naming.

Recommended style in Ruby
```
first_name = "John"
```

Variable declared inside do-end block can't be accessed outside the block.

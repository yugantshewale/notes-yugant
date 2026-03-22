## Ruby Methods or Functions
Ruby **methods are similar to functions in other programming languages**. They are used to encapsulate one or more repeatable statements into a single unit.

### Naming Conventions
Method names should `start with a lowercase letter`. `If a method name begins with an uppercase letter, Ruby may mistakenly interpret it as a constant`, leading to potential parsing errors.
```
def print_hello_world
  puts "Hello world!"
end

print_hello_world
```
---

### Methods with Parameters
Parameters are variables in a method definition that allow you to pass information (or arguments) into the method. They let the method perform actions based on the input values provided when the method is called. This is useful when the method needs to work with different inputs. 

Here's an example:
```
def greet(name)
  puts "Hello, #{name}!"
end

greet("Alice") # Output: Hello, Alice!
greet("Bob") # Output: Hello, Bob!
```
---

### Methods with Multiple Parameters
Methods can also accept multiple parameters. These parameters are separated by commas in the method definition and can be used within the method body to perform operations based on the provided values.

Here's an example:
```
def add_numbers(a, b)
  puts "The sum of #{a} and #{b} is #{a + b}."
end

add_numbers(3, 5) # Output: The sum of 3 and 5 is 8.
add_numbers(10, 20) # Output: The sum of 10 and 20 is 30.
```
---

### Methods with Default Parameters
Methods can also have default parameters. **These parameters are assigned a default value if no argument is provided when the method is called**. This is useful when you want to provide a fallback value for a parameter.

Here's an example:
```
def greet(name = "Guest")
  puts "Hello, #{name}!"
end

greet("Alice") # Output: Hello, Alice!
greet # Output: Hello, Guest!
```
---

### Named Parameters
Methods can also accept `Named Parameters` also known as `keyword arguments`. These arguments are `specified using a key-value pair and are optional`. This is useful when you want to provide a more descriptive way to pass arguments to a method.

Here's an example:
```
def greet(first_name:, last_name:)
  puts "Hello, #{first_name} #{last_name}!"
end

greet(first_name: "Alice", last_name: "Smith") 
```
With named parameters, the order doesn't matter because each argument is associated with a specific parameter name


**You can also set default values for named parameters:**
```
def greet(first_name: "Guest", last_name: "User")
  puts "Hello, #{first_name} #{last_name}!"
end
```
---

### Return statement
In Ruby, methods automatically return the value of the last evaluated expression, so an explicit return statement is often unnecessary. However, you can use `return` if you want to exit the method early or `return` a specific value.

---

### Implicit Return
Here's an example where Ruby implicitly returns the last evaluated expression:
```
def add(a, b)
  a + b
end

puts add(2, 3)
```
In this case, a + b is the last line in the method, so its value 5 is returned automatically.

---

### Explicit Return
You can use return to exit a method early or to make the return value clearer:
```
def add(a, b)
  return a + b
end

puts add(2, 3)
```
---
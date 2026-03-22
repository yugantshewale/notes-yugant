### Displaying on Screen in Ruby
In Ruby, puts is used for displaying on the screen.

eg :

`puts "I love ice cream"`

`puts 2+3`

---

### Interpolation using double quoted string
The below code
```
name = "John Smith"
greetings = "Good morning " + name
puts greetings
```
Can be rewritten using interpolation as follows:
```
name = "John Smith"
greetings = "Good morning #{name}"
puts greetings
```
Notice that instead of concatenating the two strings with a + sign, we are using #{ }. If the string is a double quoted string, then Ruby will try to evaluate the code inside the { }. This is called ***String Interpolation***.

```
puts "Current time is #{Time.now}"

movie = "Gone with the wind"
puts "We are going to watch #{movie}"

city = "Tokyo"
country = "Japan"
puts "#{city} is the capital of #{country}"
```

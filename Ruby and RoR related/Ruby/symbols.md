### What is symbol
In the example given below, both the variables `hello` and `name` contain different string values:
```
hello = "Hello World"
name = "John Smith"

puts hello
puts name
```
In the case given below, we have three strings with the same value.
```
hello1 = "Hello"
hello2 = "Hello"
hello3 = "Hello"

puts hello1
puts hello2
puts hello3
```
Even though the `value is same`, for Ruby, these are three different strings.

So, `Ruby creates room to have all the three strings and all strings take memory`.

Memory is an expensive thing when we are running programs. We want to take as little memory as possible. That's where symbol comes in picture.
```
hello1 = :hello
hello2 = :hello
hello3 = :hello

puts hello1
puts hello2
puts hello3
```
**In this case, we created three symbols. However, the value is same for all the three symbols, so Ruby will treat them as a single symbol. This will take a lot less memory.**

We can check if all the symbols refer to the same thing or not by asking each string and each symbol what is their object_id.

---

### Convert a String Into a Symbol

A string can be converted into a symbol by using the method `to_sym`.
```
hello = "Hello World".to_sym
puts hello
```
---

### Convert a Symbol Into a String

A symbol can be converted into a string by using the method `to_s`.
```
hello = :hello_world
puts hello.to_s
```
---
### Symbols are immutable
**Symbols are immutable. It means that once a symbol has been created it can't be changed. We can't append anything to a symbol.**
```
puts :hello << "world"
Output: Error: no implicit conversion of String into Symbol
```
---
### What's the use of symbols
Symbols are used a lot for method arguments.

symbols are frequently used as hash keys.
```
person2 = { :name => "Sam", :age => 47}
age_of_person = person2[:age]

puts age_of_person
```

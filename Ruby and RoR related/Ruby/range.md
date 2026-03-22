### Range of Numbers
Let's say that I want a range of numbers from 1 to 20. In Ruby, we can get the range of numbers by using `(1..20)`.

Just like an array, a range also supports each and do end.
```
numbers = (1..20)

numbers.each do |number|
  puts number
end
```
### Checking if Value is in Range
Range has a method `include?` which can be used to find if a value is in a given range.
```
range = (30..50)
puts range.include? 45
```
---

### Converting Range into an Array

A range can be converted into an array using the `to_a` method.
```
range = (1..20)
array = range.to_a
puts array
```
---
### Double Dot `..` vs Triple Dot `...`
Range supports both double dots and triple dots.

When we use **double dots**, the **range includes the last value**.

When we use **triple dots**, the **last value is not included in the range**.
```
puts (1..5).to_a
puts (1...5).to_a
#Output : [1, 2, 3, 4, 5]
#       : [1, 2, 3, 4]
```
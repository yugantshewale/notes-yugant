## Array creation
### Create an array with elements
```
array = [1, 2, 3, 4, 5]
```
---

### Array length
Get the length of an array
```
array = [1, 2, 3, 4, 5]
puts array.length
```
---

### each in array and do-end block
Array has a special thing called `each`. Array also has a `do end block`.
```
things_i_like = ["ice cream", "chocolate","movies"]

things_i_like.each do |thing|
  puts "I like " + thing
end
```
```
numbers = [1,4,8,9,41]

numbers.each do |number|
  puts number * 2
end
```
In the `do end` block, `each item` is `captured` in `between` those `two vertical lines ||` & `printed one by one.`

Those two vertical lines are also called pipes.

---

### Find the Number of Items in an Array
Array has a method called `length`. It is used to get the number of elements in an array.
```
array = [1, 2, 3, 4, 5]
puts array.length
```
---

### Array index
Get the index of an element in an array
```
array = [1, 2, 3, 4, 5]
puts array.index(3)
puts array[3]
```
---

### Add an Item to an Array
Add an element to the end of an array using the `push` method.
```
array = [1, 2, 3, 4, 5]
array.push(6)
puts array
```
---

### Remove an Item from an Array
Remove the last element from an array using the `pop` method.
```
array = [1, 2, 3, 4, 5]
array.pop
puts array
```
---

### Remove the First Item from an Array
Remove the first element from an array using the `shift` method.
```
array = [1, 2, 3, 4, 5]
array.shift
puts array
```
---

### Add an Item to the Beginning of an Array
Add an element to the beginning of an array using the `unshift` method.
```
array = [1, 2, 3, 4, 5]
array.unshift(0)
puts array
```
---

### Array delete
Remove an element from an array using the `delete` method.
It takes the element to be removed as an argument.
```
array = [1, 2, 3, 4, 5]
array.delete(3)
puts array
Output: [1, 2, 4, 5]
```
---

### Array slice
Get a slice of an array
```
array = [1, 2, 3, 4, 5]
puts array.slice(1, 3)
Output: [2, 3, 4]
```
---

### Array reverse
Reverse an array
```
array = [1, 2, 3, 4, 5]
puts array.reverse
Output: [5, 4, 3, 2, 1]
```
---

### Find the count of equal items in an Array
We have an array appliances with a list of appliance names.
```
appliances = ["Refrigerator", "Air Conditioner", "Heater", "Refrigerator", "Television", "Heater", "Air Conditioner", "Refrigerator"]
```
You can see that there are some items which are repeated in this array. If we wanted to get a clear understanding of how many items are repeated, we have a handy method, tally at our disposal. 

We can use `tally` to get a count of each item in the array.
Therefore we can do the following to get a clear understanding of how many items are repeated:
```
count = appliances.tally
puts count
Output: {"Refrigerator"=>3, "Air Conditioner"=>2, "Heater"=>2, "Television"=>1}
```

The tally method also accepts a hash as an optional argument.

Instead of returning a new hash as the output, the tally method will update the values of this hash and return it.

This is useful when accumulating a count of values in multiple arrays.

Let us take a look at an example:
```
tallied_animals = {}

animal_group_1 = ["Cat" ,"Cat" , "Dog", "Sloth"]

animal_group_2 = ["Sloth", "Elephant", "Tiger"]

animal_group_3 = ["Dog", "Tiger", "Cat"]

animal_group_1.tally(tallied_animals)
animal_group_2.tally(tallied_animals)
animal_group_3.tally(tallied_animals)

puts tallied_animals
# {"Cat"=>3, "Dog"=>2, "Sloth"=>2, "Elephant"=>1, "Tiger"=>2}
```
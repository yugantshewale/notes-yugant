### Select Certain Items From Array
We have an array of numbers and we want to get only the even numbers from that array:
```
array = [1,2,3,4,5,6,7,8]

even_array = []
array.each do |item|
  even_array.push(item) if item.even?
end

puts even_array
```
This code works but array has `select` to handle this in a better way.
`select` will only pick items for which the result of the given condition is true.
```
array = [1,2,3,4,5,6,7,8]
even_array = array.select do |item|
  item.even?
end

puts even_array
```
---

### Remove Certain Items From an Array
We have an array of numbers and we want to remove all the odd numbers from that array.
```
array = [1,2,3,4,5,6,7,8]

even_array = []
array.each do |item|
  even_array.push(item) if item.even?
end

puts even_array
```
This code works, but Array provides `reject` as a simpler way to `reject certain items`.

reject will `only reject items for which the result of condition is true`.
```
array = [1,2,3,4,5,6,7,8]
even_array = array.reject do |item|
  item.odd?
end

puts even_array
```
---

### Add an Item to an Array Using Double Arrows

In the earlier lesson, we saw that we can add values to an array by using push.
```
numbers = [1,2,3,4]
numbers.push(5)
puts numbers
```
Instead of using `push`, we can also use `<<` to add to an array.
```
numbers = [1,2,3,4]
numbers << 5
puts numbers
```
We can also add another array to an array.
```
numbers = [1,2,3,4]
numbers += [5,6,7,8]
puts numbers
Output: [1,2,3,4,5,6,7,8]
```
---

### Joining Arrays
In the programming world, concatenation means adding two items.

We can use `+` to concatenate two arrays.
```
numbers1 = [1,2,3,4]
numbers2 = [5,6]

all_numbers = numbers1 + numbers2
puts all_numbers
```
---

### Concatenating Arrays Using `concat`

We can also use `concat` to concatenate two arrays.
```
numbers1 = [1,2,3,4]
numbers2 = [5,6]

numbers1.concat(numbers2)
puts numbers1
```
---

### Remove All Nil Elements
If an array has `nil` items and we want to remove these nil items, then we can use `compact`.
```
array1 = [1, 2, nil, 4, "6", nil, "John"]

array2 = array1.compact

puts array1.to_s
puts array2.to_s
Output: [1,2,nil,4,"6",nil,"John"]
        [1,2,4,"6","John"]
```
---

### Remove All Nil Elements
### Remove All Duplicate Elements
If an array has duplicate items, then we can use `uniq` to remove all the duplicates.
```
array1 = [1, 2, 2, 3, 4, 4, 4, 5, 5, 6, 7, 7]

array2 = array1.uniq

puts array1.to_s
puts array2.to_s
Output: [1,2,2,3,4,4,4,5,5,6,7,7]
        [1,2,3,4,5,6,7]
```
---

### Remove All Nested Arrays
We have an array which contains other arrays. We want to keep all the items of the arrays, but we want to remove all the arrays themselves.

Ruby provides `flatten` to do this job.
```
array1 = [1, [2, 3, 4], 5, 6, [7,8]]

array2 = array1.flatten

puts array1.to_s
puts array2.to_s
Output: [1,[2,3,4],5,6,[7,8]]
        [1,2,3,4,5,6,7,8]
```
As we can see, `array2` only has numbers and does not have any arrays.

`flatten` does not change the original array.

---

### Removing Elements From Array Using Minus Sign
Ruby uses the `-` sign to subtract or remove items from an array.
```
array1 = [1,2,3,4,5,6,7]
array2 = array1 - [2,3]
puts array1.to_s
puts array2.to_s
Output: [1,2,3,4,5,6,7]
        [1,4,5,6,7]
```
The `-` **does not change the original array**. A new array is created after removing the specific elements from the array.

---

### Array Destructuring
Look at the following code:
```
array = [55, 75, "August 25"]
puts array

home_team_score = array[0]
puts home_team_score

opposite_team_score = array[1]
puts opposite_team_score

date_of_game = array[2]
puts date_of_game
```
Rather than taking four separate statements to assign values, the same thing can be done in one line as shown below:
```
array = [55, 75, "August 25"]
home_team_score, opposite_team_score, date_of_game = array

puts home_team_score
puts opposite_team_score
puts date_of_game
```
---

### Destructuring Using Greedy Variables
During destructuring, **adding a star before a variable name makes that variable greedy and that variable `takes up all the remaining values`**.
```
array = [1,2,3]

a, *b = array
# b = [2,3]
# a = 1

puts b
puts a
```

In the case given above, variable `b takes up both the values 2 and 3 and puts them in an array`.

---

### The variable can be greedy, but Ruby is smart
```
array = [1,2,3]

a, *b, c = array
# a = 1
# b = [2]
# c = 3
puts a
puts c
puts b
Output: 1
        3
        [2]
```
In the case provided above, even though b is greedy, Ruby first attempts to assign at least one value to each of the variables.

In this case, one value is assigned to a, b & c. Since nothing else is left, b ends with only 2. But, since b is using a *, that 2 is an array.

Now, let's try the same thing with more values.
```
array = [1,2,3,4,5]

a, *b, c = array
# a = 1
# b = [2,3,4]
# c = 5
puts a
puts c
puts b
Output: 1
        5
        [2,3,4]
```
In this example, Ruby first assigned 1 to a and 2 to b and 5 to c.

Still, we were left with 3 & 4 which got assigned to b.

**Two Greedy Variables Will Cause Problems**

---

### Destructuring With Not Enough Elements In An Array 
```
array = [1,2,3]
a, b, c, d, e = array
# a = 1; b = 2; c = 3; d = nil; e = nil
```
If there are not enough values for variables, then the variables who did not get any value are assigned `nil` value by Ruby.

If a variable uses the `*` operator, then it `always gets an array`.

If there is `no value for the greedy variable`, then the `final result is an empty array`:
```

array = [1,2,3]
a, b, c, *d = array
# a = 1; b = 2; c = 3; d = []
```
---

### Loop Over Array Using Index
```
names = %w(John Mary Adam)
names.each_with_index do |name, index|
  puts "#{name} is at position #{index}"
end
```
When we use `each_with_index` then along with the value in the array, we also get the position of each value.

While `each_with_index` is convenient, you might encounter situations where you need more control over the iteration. This is where `with_index` comes into play. The `with_index` method `can be applied to an enumerator`, providing additional flexibility:
```
names = %w(John Mary Adam)
names.to_enum.with_index(1).each do |name, index|
  puts "#{name} is at position #{index}"
end

Output:
John is at position 1
Mary is at position 2
Adam is at position 3
```
Here, `to_enum` is `used to create an enumerator for names`, and `with_index(1) specifies that the index should start from one`. By providing an argument to `with_index`, we can `set a custom starting index`. The end result is the same as our adjusted each_with_index example.

---

### Loop Over Equal-Sized Array Chunks
The `each_slice` method in Ruby is used to iterate over an array `in groups of a specified size`, or slice.

`each_slice` `divides the array into consecutive slices of the specified size and yields each slice to the provided block`. You can perform operations on each slice within the block, such as printing, processing, or aggregating data.
```
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9]
numbers.each_slice(3) do |slice|
  puts slice.join(', ')
end

Output:
1, 2, 3
4, 5, 6
7, 8, 9
```

If the array length is not evenly divisible by the slice size, the last slice will contain the remaining elements.

If you don't provide a block, each_slice returns an enumerator, allowing you to chain it with other Enumerable methods.

---

### Loop Over Array in Reverse Order
The `reverse_each` method in Ruby is used to iterate over an array in reverse order.

`reverse_each` `iterates over the array elements in reverse order`, starting from the last element and moving towards the first element. It yields each element to the provided block, allowing you to perform operations on each element in reverse order.
```
numbers = [1, 2, 3, 4, 5]
numbers.reverse_each do |number|
  puts number
end

Output:
5
4
3
2
1
```

If you don't provide a block, reverse_each returns an enumerator, allowing you to chain it with other Enumerable methods.

---

### Sort items of Array

We can use `sort` to sort the elements in an array in the ascending order.
```
array = [1,6,3,87,4,98]
sorted_array = array.sort
puts sorted_array
```
---

### Quicker Way to Create Array of Strings
Creating long arrays can become cumbersome, where you have to type multiple comma and quotation marks.

Ruby gives us simpler ways to create arrays. For creating an array of strings, use `%w`:
```
array_of_strings = %w[green red blue]

puts array_of_strings
```
However, if there is a whitespace in the word, then we need to put a `\` to escape the whitespace.
```
array = %w(Colorado California New\ York)

puts array
```
---
### Create Array of symbols

We can use `%i` to create an array of symbols.
```
array_of_symbols = %i[green red blue]

puts array_of_symbols
```
---
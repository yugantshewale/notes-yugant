### Map
Let's say that we have an array of 6 numbers and we need to double all those numbers. Here is how we can do that
```
def doubler(array)
  doubled_array = []
  array.each do |element|
    doubled_array << element * 2
  end

  doubled_array
end

array = [4,8,7,3,9,7]
doubled = doubler(array)
puts doubled
```
Ruby provides method `map` which can help us to this in a much simpler way. First let's see how to use map.
```
def doubler(array)
  array.map do |element|
    element * 2
  end
end

array = [4,8,7,3,9,7]
doubled = doubler(array)
puts doubled
```
`map internally builds an array for us and that's why we don't need to build an array`. All we need to do is to tell map how to calculate the new value that will go into the array. In this case we are multiplying each element with 2.
```
def capitalizer(array)
  array.map do |element|
    element.capitalize
  end
end

array = ["france", "india", "england"]
puts capitalizer(array)
```
If the code in the block is of only one line then the code can be written like this.
```
def capitalizer(array)
  array.map { |element| element.capitalize }
end

array = ["france", "india", "england"]
puts capitalizer(array)
```
---

### Filter
Let's say that we have an array of 6 numbers and we want to get only the even numbers. Here is how we can do that.
```
def number_selector(array)
  even_numbers = []
  array.each do |element|
    even_numbers << element if element.even?
  end

  even_numbers
end

array = [4,8,7,3,9,7]
puts number_selector(array)
```
Ruby provides method `filter` which can help us to this in a much simpler way. First let's see how to use `filter`.
```
def number_selector(array)
  array.filter do |element|
    element.even?
  end
end

array = [4,8,7,3,9,7]
puts number_selector(array)
```
Just like `map`, `filter` also internally builds an array for us and that's why we don't need to build an array. **All we need to do is to tell filter a condition that it needs to apply on each of the elements. If an element passes the condition then add that element to the array else reject that element.**
```
def selector(array)
  array.filter do |element|
    element.size > 5
  end
end

array = ["France", "India", "England", "Australia"]
puts selector(array)
```
It should be noted that the methods `select` and `find_all` are identical to `filter` in that they all serve to filter elements from an array or hash based on a specified condition.

---

### Find
We can use `find` to select the very first element that passes a condition.
```
def number_finder(array)
  array.find do |element|
    element > 10
  end
end

array = [4, 8,7,3,13, 9,7, 11]
puts number_finder(array)
Output: 13
```
---

### all?
`all?` returns either `true` or `false`. **It will return true if all the elements pass the given condition.**

Let's check if all the elements of the given array are even or not.
```
def number_finder(array)
  array.all? do |element|
    element.even?
  end
end

array = [4, 8,7,3,13, 9,7, 11]
puts number_finder(array)
Output : false
```
---

### Reading documentation
[documentation](https://courses.bigbinaryacademy.com/learn-ruby/enumerable/reading-docs/)

---
### Aliases
Ruby has aliases for a lot of methods. For example if you open Ruby [Enumerable](https://ruby-doc.org/core-3.1.2/Enumerable.html) documentation and if you look at the sidebar then you will see method like find_all. However when you click on that then you will see this.
```
select {|element| ... } → array
select → enumerator
```
What it means is that `find_all` is an alias for `select`. In your code you can write `find_all` or `select` and it would do the same thing.

Similarly let's see method `collect` in the sidebar. Once you click on it you will be taken to the method `map`. Method `collect` is an alias to method `map`.

---

### Enumerable Methods
There are many more methods like `any?`, `none?`, `one?`, `take`, `drop`, `cycle`. All these methods come under Enumerable module.

Here is [link](https://ruby-doc.org/core-3.1.2/Enumerable.html) of the Enumerable documentation.
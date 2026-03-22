### Sum using inject

First let's take an example. Let's say that we have an array of items and we want to add all the items. Here is how we can add all the items of the array.
```
total = 0
[5,6,7,8].each do |element|
  total = total + element
end
puts total
```
In the above case we had to create a variable called `total` and we kept adding values to `total` to get the final result. This works. However we can solve this problem much more easily using `inject`
```
total = [5,6,7,8].inject(0) do |result, element|
  result + element
end
puts total
```
Here is how it works.

For the first time the value of result is zero because we are passing that value. The value of element is 5. Now we perform result + element. So in this case we do 0 + 5. "0 + 5" is 5. And this "5" becomes the new value for result.

For the second time the value of result is "5". The value of element is 6. Now we perform result + element. So in this case we do 5 + 6. "5 + 6" is 11. And this "11" becomes the new value for result.

For the third time the value of result is "11". The value of element is 7. Now we perform result + element. So in this case we do 11 + 7. "11 + 7" is 18. And this "18" becomes the new value for result.

For the fourth time the value of result is "18". The value of element is 8. Now we perform result + element. So in this case we do 18 + 8. "18 + 8" is 26. And this "26" becomes the new value for result.

**We are done with all the elements so inject method will return the final value of result which is 26.**

---

### Inject for multiplication
```
total = [2,3,4,5].inject(1) do |result, element|
  result * element
end
puts total
```

---

### inject to build hash
In this case we have the country name and the capital city in an array. The whole array is part of a bigger array.
```
data = [
  ["France", "Paris"],
  ["India", "New Delhi"],
  ["England", "London"]
  ]
  ```
The goal here is to build a hash with the country name as the key and the capital city as the value.

We can iterate through the arrays and we can build the hash like this.
```
data = [
  ["France", "Paris"],
  ["India", "New Delhi"],
  ["England", "London"]
  ]

hash = {}
data.each do |array|
  country = array[0]
  city = array[1]
  hash[country] = city
end

puts hash

```
We can also solve this problem using `inject`.
```
data = [
  ["France", "Paris"],
  ["India", "New Delhi"],
  ["England", "London"]
  ]

hash = data.inject({}) do |result, element|
  country = element[0]
  city = element[1]
  result[country] = city
  result
end

puts hash
```
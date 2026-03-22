### Use New to Create a Hash
There is another way to create a hash using `new`:
```
hash2 = Hash.new
puts hash2
```
`Hash.new` creates an empty hash. To this empty hash, we need to add key and value, as shown below:
```
hash3 = Hash.new
hash3 = hash3.merge({ name: "John Smith" })
puts hash3
```
---

### Select Some Elements of the Hash
Here we have a hash of people with their house numbers:

| Name	| House number |
--------|--------------
| John  |	507         |
| Sally |	239         |
| Adam  |	786         |
| Nancy |	324         |
| Kelly |	788         |

Our task is to find every person who has a house with a house number greater than 500.
We can use `select` to do this. Using `select`, **we can get a smaller part of the original hash**. **select will only select the elements for which the condition is true**.

In this case, the condition is that the house number should be more than 500.
```
houses = {
    John: 507,
    Sally: 239,
    Adam: 786,
    Nancy: 324,
    Kelly: 788
}

houses2 = houses.select do |key, value|
  value > 500
end

puts houses2
```
It's important to note that when select is used then the "do end" block should return either true or false. If the block returns true, then that key and value pair will be selected and if the block returns false, then that key and value pair will be rejected.

---
### Remove Some Elements From the Hash
`reject` is the opposite of select. **Elements that meet the given condition get rejected**.
```
houses = {
    John: 507,
    Sally: 239,
    Adam: 786,
    Nancy: 324,
    Kelly: 788
}

houses2 = houses.reject do |key, value|
  value <= 500
end

puts houses2
Output:
{:John=>507, :Adam=>786, :Kelly=>788}
```
---

### Default Value in Hash
A hash contains key and value. If the key is not found, then hash returns `nil`.
```
hash = { name: "John Smith",
         city: "Chicago"}

age = hash[:age]
puts age
Output : nil
```
As we can see, the hash does not have a key called age and this is why, the hash returned nil. That's what hash does by default.

**However, we can tell hash to return some other default value.**
```
hash = { name: "John Smith",
         city: "Chicago"}

hash.default = 0

age = hash[:age]
puts age
Output : 0
```
----

### Default Value in Hash Using new
The default value can also be set using `Hash.new`.
```
h = Hash.new(0)
hash = h.merge({ name: "John Smith", city: "Chicago"})

age = hash[:age]
puts age
```
---

### Merge to Add More Data to Hash
We can use `merge` to merge the contents of two hashes. It returns a new hash. The original two hashes remain the same.
```
hash =  { USA: "Washington D.C.",
          England: "London",
          France: "Paris" }

hash2 = {
  Italy: "Rome"
}

hash3 = hash.merge(hash2)

puts hash
puts hash2
puts hash3
```
We can also use `merge!` to merge two hashes. The difference is that in this case the original hash itself is altered.
```
hash =  { USA: "Washington D.C.",
          England: "London",
          France: "Paris" }

hash.merge!({ Italy: "Rome"})

puts hash
```
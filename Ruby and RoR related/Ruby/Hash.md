### Key Value Pair

A Hash stores information in the form of a key value pair.

| Key	    | Value           |
|---------|-----------------|
| USA	    | Washington D.C. |
| England | London          |
| France	| Paris           |

In the hash given above, the key is the country name and the value is the capital of the country.
```
hash = {
  "USA" => "Washington D.C.",
  "England" => "London",
  "France" => "Paris"
}
puts hash
Output:
{"USA"=>"Washington D.C.", "England"=>"London", "France"=>"Paris"}
```
But the usage of `hash-rockets =>` for representing a hash, while still valid and occasionally seen in older Ruby code, has become less common. 

This is due to the introduction of a newer, `more concise syntax in Ruby 1.9 that resembles JSON, making the code more readable and easier to write`, especially for those familiar with JSON from other languages.
```
hash =  { USA: "Washington D.C.",
          England: "London",
          France: "Paris" }

puts hash
```
It's essential to note that in this newer syntax, keys are automatically converted to symbols, not strings. For instance, in the example above, `USA:` is equivalent to `:USA =>`. This approach is suitable for most situations, as symbols are more memory-efficient and quicker to process compared to strings.

---

### Get Value Using Key
We can pass a key to a hash and we can ask the hash to return the value for the given key.
```
hash = {
  "USA" => "Washington D.C.",
  "England" => "London",
  "France" => "Paris"
}

puts hash["USA"]
```
---

### Add Data to a Hash
We can add another key value pair to an existing hash using the `merge!` method.
```
hash =  { USA: "Washington D.C.",
          England: "London",
          France: "Paris" }

hash.merge!({ Italy: "Rome"})

puts hash
Output:
{:USA=>"Washington D.C.", :England=>"London", :France=>"Paris", :Italy=>"Rome"}
```
Using `merge!` changes the original hash.

---

### Update Data in a Hash
We can update the value of a key in a hash using the `[]=` method.
```
hash =  { USA: "Washington D.C.",
          England: "London",
          France: "Paris" }

hash[:USA] = "New York"

puts hash
Output:
{:USA=>"New York", :England=>"London", :France=>"Paris"}
```
---

### Adding Data to a Hash Using Key
```
hash =  { USA: "Washington D.C.",
          England: "London",
          France: "Paris" }

hash[:Italy] = "Rome"

puts hash
```
### Access All Keys
Hash provides the method `keys` to list all keys from a hash.
```
hash =  { USA: "Washington D.C.",
          England: "London",
          France: "Paris" }

puts hash.keys
#Output: USA 
         England 
         France
```
---

### Loop Over All Keys and Values

Just like Array and Range, Hash also supports `each do` method.

```
hash =  { USA: "Washington D.C.",
          England: "London",
          France: "Paris" }

hash.each do |key, value|
  puts " Capital of #{key} is #{value}"
  puts "Capital of " + key.to_s + " is " + value
end
```
The `to_s` method converts the symbol to a string so that it can be concatenated with the other strings.

---

### Access All Values
Hash provides the method `values` to list all values from a hash.
```
hash =  { USA: "Washington D.C.",
          England: "London",
          France: "Paris" }

puts hash.values
#Output: Washington D.C. 
         London 
         Paris
```
---
### Value omission in Ruby Hash Literals
In Ruby, if the value of a key inside a hash is not specified, it will be assigned a default value of `nil`.

From Ruby version 3.1, we have an option to omit the value in a hash, provided that we have a variable in scope with the same name as the key.
The value stored in the variable will be assigned to the key inside the hash.
eg :

```
dog = "Pluto"
cat = "Tom"

mammals = { dog: dog, cat: cat}
# Shorthand
animals = { dog:, cat:}

puts animals
puts mammals
```
As we can see from the above code, both mammals and animals hash have the same values.

When using the shorthand, make sure never to add variables as a string. Doing this will throw an error.
```
fish = "Clown-fish"
bird = "Seagull"

life = {"fish":, "bird":}
```
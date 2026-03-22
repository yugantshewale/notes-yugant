## Strings in Ruby

### Combining two strings
```
name = "John Smith"
greeting_style = "Hello"

greeting = greeting_style + " " + name
puts greeting
```
---

### Convert All Letters in String to Capital Letters

```
string1 = "hello ruby".upcase
puts string1
```

Similarly, we can use `.downcase` to convert all letters in a string to lowercase.
---

### Reversing a String

```
string2 = "hello ruby".reverse
puts string2
```
----

### Removing Extra Spaces in String

```
string3 = "   hello ruby   ".strip
puts string3
```
---

### Convert Numbers and Arrays Into a String
In Ruby, there are situations where you need to convert data types to strings to perform certain operations, especially when working with numbers and arrays.
```
puts "Ruby is " + 24.to_s + " years old now"
```
```
puts "Ruby is #{24} years old now"
```
If you just did 
```
puts "Ruby is " + 24 + "years old"
```

it will give an error because you cannot concatenate a string with an integer directly. Instead, you need to convert the integer to a string using the `.to_s` method before concatenating it with the string.

---

### Convert Arrays Into a String

```
array = [1, 2, 3]
puts array.join(", ")
```
```
puts "Ruby is #{array.join(", ")} years old now"
```

```
array = [1, 2, 3, 4, 5, 6, 7, 8]

puts array
puts array.to_s
```
---

### Convert a String Into a Number

```
# We will get error here
puts "12" + 2
```
We can convert a string into a number using the `.to_i` or `.to_f` method.
```
puts "12".to_i + 2
```
```
puts "12".to_f + 2
```
---

### Capitalize the First Letter of a String
```
puts "miami".capitalize
#Prints Miami
```
---

### Running Methods One After Another
```
name = "John Smith"
puts name.upcase.downcase.capitalize
#Output: John Smith
```

In the above example, three methods are called one after another.
name.upcase results in JOHN SMITH. This is then passed on to the downcase method.
The downcase method runs on JOHN SMITH and we get john smith. This result is passed on to the capitalize method.
Finally, the capitalize method runs on john smith and the result, John smith, is displayed on the screen.

---

### Array operations on string
```
string = "hello"
puts string[0]
```
***Last position is -1***
```
string = "hello"
puts string[-1]
#Output : o
```
---

### Check for the Starting Characters in a String
Ruby provides ` start_with? ` to check if a string starts with the given string.

```
string = "hello"
puts string.start_with?("he")
#Output : true
```
---

### Check if a String is included in another String
Ruby provides ` include? ` to check if a string is included in another string.

```
string = "hello"
puts string.include?("lo")
#Output : true
```
---
### Convert String to Characters

Ruby provides `chars` method to convert a string into a list of characters.
```
name = "John Vanderbilt"

characters = name.chars

puts "printing all characters"
puts characters

puts "printing 3rd character"
puts characters[2]
```
---

### Convert Characters to String

Ruby provides `join` method to convert a list of characters into a string.
```
characters = ['J', 'o', 'h', 'n']

string = characters.join

puts "printing all characters"
puts string

puts "printing 3rd character"
puts string[2]
```
---

### Compare Two Strings Ignoring Case

Ruby provides the `casecmp` method to compare two strings without considering their case.

If string1 and string2 are the two strings you want to compare, the result will be an integer that indicates the relationship between the two strings.
1. If the result is `0`, it indicates that `both strings are equal, disregarding case.` 

eg : ```"John".casecmp("john") == 0 #Output : true```

2. If the `result` is a `positive number`, it signifies that `string1 comes after string2 in a dictionary order when ignoring case`.

eg : ```"Kohn".casecmp("john")   #Output : 1```

3. If the result is a `negative number`, it means `string1 precedes string2` in a dictionary order while ignoring case.

eg : ```"john".casecmp("Kohn")   #Output : -1```

4. If the result is nil it means that the two are incomparable.

```
string1 = "hello"
string2 = "HELLO"

result = string1.casecmp(string2)
puts result
```
---

### Compare Two Strings Considering Case
 The `<=> operator`, also known as the `spaceship operator`, facilitates `case-inclusive string comparisons`.

If string1 and string2 are the two strings you want to compare, the result will be an integer that indicates the relationship between the two strings.

1. If the result is 0, it indicates that both strings are equal.
2. If the result is a positive number, it signifies that string1 comes after string2 in a case-sensitive dictionary order.
3. If the result is a negative number, it means string1 precedes string2 in a case-sensitive dictionary order.
4. If the result is nil it means that the two are incomparable.
```
string1 = "hello"
string2 = "HELLO"

result = string1 <=> string2
puts result
#Prints : 1 cuz string1 comes after string2 in a case-sensitive dictionary order.
```
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

***Same logic applies DOES NOT APPLY for single quoted strings as well.***

---

### What is escape sequence
Sometimes in programming, we need to use non-printable items.

For example, on laptops, if you press the wrong button, then you hear a beep sound. How do we tell the computer to play that sound?

Researchers had agreed that `\a` would be `treated as an alarm or a beep`.

These special instructions that start with a backslash are called Escape Sequences.

Given below is the list of escape sequences with their corresponding meaning:

```
| ` | Single quote | | " | Double quote | | \a | Audible bell | | \b | Backspace | | \f | Form feed | | \r | Carriage return | | \s | A space | | \t | Horizontal tab | | \n | New line |
```
```
string = 'I am John.\a I am 25 years old'
puts string
string = "I am John.\n I am 25 years old"
puts string
```
---

### Get a Part of the String
```
game = "basketball"
puts game[0,6]
puts game[6,4]
Output: basket
Output: ball
```
The first argument is the index of the first character to be included in the substring, and the second argument is the length of the substring.

---

### Replace characters in a string
Let's say we have a string `ping`. We want to `replace` the character `i` with `o`, making the resulting string `pong`.

In Ruby, we can use the `tr` method to do this:
```
message = "ping"
acknowledgment_message = message.tr("i", "o")
puts acknowledgment_message
```

The tr method can also be used to replace multiple characters in a string at once. Look at the following example:
```
word = "hello"
new_word = word.tr("el", "ip")
puts new_word
```
eg : IMPORTANT

```
word = "must"
replaced_word = word.tr("mt", "cp")
puts replaced_word
#Output: cusp
```
---

### Replace strings within a string
 Let's say we want to replace a continuous chunk of string within a larger string (also called a substring), with something else. For example, we want to convert the string twist into test. In such cases, we can use the `gsub` method.
```
word = "twist"
new_word = word.gsub("wi", "e")
puts new_word
#output: test
```
The `gsub` method can also be `used to remove characters from a string`. Just set the second argument to an empty string.
```
word = "must"
replaced_word = word.gsub("mu", "")
puts replaced_word
#Output: st
```
---

### String length
You can use the `length` method to get the `number of characters in a string`. This method returns the `total count of characters, including whitespaces and special characters.`
```
name = "John Smith"
puts name.length
```
---
### Convert a String into an Array
String has a method `split` that splits a string into an array.
```
city_name = "Salt Lake City"

array = city_name.split

puts array.to_s
#Output: ["Salt", "Lake", "City"]
```
---

### Split String Along Comma
We can split string along spaces, commas or any other character.
```
things_i_like = "ice cream, chocolate, movies, beaches"

items = things_i_like.split(",")
puts items.to_s
#Output: ["ice cream", " chocolate", " movies", " beaches"]
```
```
cities = "Chicago | Miami | Seattle"

array = cities.split(' | ')

puts array
#Output: ["Chicago", " Miami", " Seattle"]
```
---

###  Convert an Array Into a String

Array has a method `join` which converts the contents of an array into a String.
```
array = ["Salt", "Lake", "City"]

string = array.join()

puts string
#Output: SaltLakeCity
```
In order to fix the issue with `join` we need to tell `join` to add spaces between the elements `join(" ")`
```
array = ["Salt", "Lake", "City"]

string = array.join(" ")

puts string
#Output: Salt Lake City
```
### The If Condition 
eg
```
food = "pizza"

if food == "pizza"
  puts "You like pizza."
end
```
---

### Difference between == and ===

The `"=="` operator is used to check if two values are equal. It compares the values without considering their data types.
In Ruby, "==" does not perform type coercion between strings and numbers. "4" is a String, and 4 is an Integer, so they are not equal.

On the other hand, the `"==="` operator is primarily used in case statements to perform pattern matching.

It behaves differently based on the class of the object being compared.

eg:

```
puts (1..5) === 3
puts /tar/ === "Guitar"
puts Integer === 4
Output:
true
true
true
```
In the first example, the "===" operator is used with a range object (1..5) and checks if the value 3 falls within that range. Since it does, Boolean true is returned.

In the second example, the "===" operator is used with a regular expression /tar/ to match it against the string "Guitar". Since the string contains the pattern defined by the regular expression, it returns Boolean true.


In the third example, we are checking if the 4 belongs to the class Integer.

---

### The if else Condition
```
food = "pizza"

if food == "pizza"
  puts "You like pizza"
else
  puts "You do not like pizza"
end
```
```
food = "pizza"
drink = "juice"

if food == "pizza" and drink == "juice"
  puts "You like pizza and juice"
else
  puts "You neither like pizza nor juice"
end
```
---

### Using elsif
```
score = 63

if score > 80
  puts "You got A grade."
elsif score > 60
  puts "You got B grade"
else
  puts "You did not get A grade. Good luck next time."
end
```
---

### Inline if Condition
In general we write `if` conditions like this:
```
number = 8
if number < 10
  puts "Number is less than 10"
end
```
Simple if conditions can be written without an `end`:
```
number = 8
puts "Number is less than 10" if number < 10
```
---

### Ternary Operator
Typically, we write if else conditions like this:
```
age = 22
can_vote =  if age > 10
              "yes"
            else
              "no"
            end

puts can_vote
```
We can also write that code as shown below:
```
age = 22
can_vote = age > 10 ? "yes" : "no"
puts can_vote
```

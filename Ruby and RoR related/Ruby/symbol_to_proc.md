### Symbol to Proc
In Ruby, the “symbol to proc” syntax is written like this:
```
&:method_name
```
What does &:to_s mean?
It is a short way of writing:
```
[1, 2, 3].map { |x| x.to_s }
```
So:
```
.map(&:to_s)
```
means:
“**For each element, call the method to_s on it.**

we can use map like this.
```
def capitalizer(array)
  array.map { |element| element.capitalize }
end

array = ["france", "india", "england"]
puts capitalizer(array)
```
We can make the code even shorter. First let's see the shorter version.
```
def capitalizer(array)
  array.map(&:capitalize)
end

array = ["france", "india", "england"]
puts capitalizer(array)
```

Similarly we can find all the even elements in a given array.

```
def even_finder(array)
  array.filter(&:even?)
end

array = [1, 2, 3, 4, 5,6]
puts even_finder(array)
```

Let's say that we have an array full of numbers but they are in String format. We need to apply to_i on them to convert them to integers. We can do that like this.

```
def numericalize(array)
  array.map(&:to_i)
end

array = ["1", "2", "3", "4", "5", "Book"]
puts numericalize(array)
Output:
[1, 2, 3, 4, 5, 0]
```
**Notice that the last value in the result is zero. That's because to_i on "Book" would be zero.**

**This trick works because Ruby converts all these symbols into procs.**

Remember that anything that starts with `:` is a symbol. In this case we are using `&:capitalize`. Here it looks a bit odd but `:capitalize` is a Symbol.

In Ruby, & does something special when passing arguments to methods.

When you write:
```
&something
```

Ruby tries to convert something into a Proc object using:
```
something.to_proc
```
Symbols in Ruby have a special method:
```
:to_s.to_proc
```

This converts the symbol into a Proc that looks like:
```
proc { |obj| obj.to_s }
```

So:
```
&:to_s
```

is basically:
```
proc { |obj| obj.to_s }
```

**When should you use it?**

Use &:method_name when:
1. You just want to call ONE method
2. On each element
3. With no extra logic

---

### Symbol to Proc more
We saw that we can use inject like this.
```
def adder(array)
  array.inject { |result, element| result + element }
end

array = [1,2,3,4,5,6]
puts adder(array)
```
In Ruby the plus sign is a method so we can write the above code like this.
```
def adder(array)
  array.inject(&:+)
end

array = [1,2,3,4,5,6]
puts adder(array)
```
another example.
```
string = "Ruby is programming language"
puts string.split.map{ |element| element.length }.reduce { |result, element| result + element }
```
to :
```
string = "Ruby is programming language"
puts string.split.map(&:length).reduce(&:+) # reduce is alis for inject
```
---

### Real world usage of Symbol to Proc 
https://courses.bigbinaryacademy.com/learn-ruby/symbol-to-proc/real-world-usage-of-symbol-to-proc/
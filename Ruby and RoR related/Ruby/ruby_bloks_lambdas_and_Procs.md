### Ruby Blocks
Ruby `blocks` allow a section of code to be passed to methods without first storing that section of code into any variable.

eg :
```
[1, 2, 3].each { puts "hello" }
```
In the case given above,` { puts "hello" }` is the section of code that is being passed to the method `each`.

 As we can see, this section of code is not stored in a variable first. That's why, some people say that Ruby blocks are used to pass anonymous code to methods.
 Here, by anonymous, the only thing they mean is that the block of code is not first stored in a variable.
 ```
 4.times { puts "Good day" }

4.times do
  puts "Good evening"
end
```
---

### Accepting Arguments in Blocks

A block can also accept arguments. Here is an example:
```
[1, 2, 3].each { |n| puts n }
```
When a method accepts an argument, then the argument is inside` ( )`. However, when a block accepts an argument, then the argument is inside `| |`.

Here is another example of a block accepting arguments:
```
5.times do |n|
  puts n
end

```
---
### Yield
`yield` is a special thing in Ruby. Using yield, **a method can ask a block to be executed.**
```
def greet
  puts "Good morning"
  yield
  puts "Good evening"
end

greet { puts "Roger Smith" }
Output:
Good morning
Roger Smith
Good evening
```
Here, the method first prints *Good morning*. Then, the method yields the control to the block. Once the block is processed, then the method gets the control back and then the method prints *Good evening*.

If the method does not get a block to execute, then the method will raise an error. Let's try it out and this time no block will be passed to the method.

You should get an error in the case given below:
```
def greet
  puts "Good morning"
  yield
  puts "Good evening"
end

greet
Output: Error: no block given (yield)
```
**We want to yield to a block only if a block is passed.** There is no point in yielding to a block if there is no block. **We can solve this by using the `block_given?` method. block_given? would return true if a block is passed.**
```
def greet
  puts "Good morning"
  yield if block_given?
  puts "Good evening"
end
greet
Output :
Good morning
Good evening
```
If a block is passed, then that block will be evaluated.
```
def greet
  puts "Good morning"
  yield if block_given?
  puts "Good evening"
end

greet { puts "Roger Smith" }
```
---

### Call Block
```
def greet
  puts "Good morning"
  yield
  puts "Good evening"
end

greet { puts "Roger Smith" }
```
In the case given above, the greet method is not explicitly accepting any block. Implicitly, all methods can accept a block. That's how Ruby is structured.

However, Ruby also allows us to explicitly accept a block. In order to do so, the argument must start with an `&`. Usually, such arguments are named ``&block`.
```
def greet(&block)
  puts "Good morning"
  block.call
  puts "Good evening"
end

greet { puts "Roger Smith" }
```
---

## Proc & Lambda

### Proc

The `proc` keyword defines a block. This way, we can store the block in a variable. Later, we can call that block using the `call` method.
```
intro = proc { puts "I am Roger Smith" }
intro.call
```
**Procs can also take arguments.**
```
intro = proc { |name|  puts "I am #{name}" }
intro.call("Mary")
```
### Lambda
Ruby also has something called `lambda` which is very *similar to a proc*. `lambda enforces arity`. It means, `if a lambda accepts 2 arguments but if we're trying to pass it 3 arguments, then the lambda will raise an error. On the other hand, a proc will ignore the extra argument`.

```
intro = lambda { |name|  puts "I am #{name}" }
intro.call("Mary")
```
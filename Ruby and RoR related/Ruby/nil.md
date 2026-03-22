### What is nil
`nil` is a special thing in Ruby. It `represents empty or nothing`.

If we ask for a value from an array and that value is not there, then we get nil.
```
array = [1, 2, 3]
result = array[10]
puts result

Output: nil
```
---

### nil is Like false

In Ruby, `nil` is like `false`.
```
can_vote = nil

if can_vote
  puts "You can vote"
else
  puts "you cannot vote" #This gets printed
end
```

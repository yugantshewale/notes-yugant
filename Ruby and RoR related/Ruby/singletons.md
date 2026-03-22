### Understanding Singleton Classes
In Ruby, every object has its own unique class associated with it. This is called a `singleton class`. To access the singleton class of an object, you can use the `singleton_class method`.

```
class User
	attr_reader :name

	def initialize(name)
		@name = name
	end
	
  def greet
		puts "Hello, I'm #{name}!"
	end
end

user1 = User.new("Alice")
user2 = User.new("Bob")

puts user1.singleton_class
puts user2.singleton_class
Output:
#<Class:0x00007f9c3c0a3e28>
#<Class:0x00007f9c3c0a3e28>
```
In the above code, the `User` class has an instance variable `@name` and a getter method `name` defined using the `attr_reader` method. The `greet` method prints a greeting message using the `name` attribute of the user. The `singleton_class` method is called on `user1` and `user2` to retrieve their respective singleton classes.

Upon running the code snippet, the output will show the singleton class of `user1` and `user2`, which will be different for each object. Even though both objects user1 and user2 are instances of the same `User` class, each object will have its own singleton class associated with it.

**Singleton classes allow us to define behaviors that are unique to a particular object.**

```
class User
  attr_reader :name

  def initialize(name)
    @name = name
  end

  def greet
    "Hello, I'm #{name}!"
  end
end

user1 = User.new("Alice")
user2 = User.new("Bob")

def user1.greet
  puts "Bonjour, je m'appelle #{name}!"
end

puts user1.greet
puts user2.greet

Output:
Bonjour, je m'appelle Alice!
Hello, I'm Bob!
```
In the above example, a new `greet method` is defined specifically for `user1`. This singleton method for `user1` overrides the `greet method` defined in the `User` class.


The focus is on modifying the behavior to accommodate the fact that `user1` speaks only French. When `user1.greet` is called, the singleton method defined for `user1` is invoked, which overrides the `greet` method of the `User` class. As a result, it prints `Bonjour, je m'appelle Alice!`.

Singleton classes have two primary uses: 
1. altering the behavior of individual objects.
2. creating classes with only one instance. 

While both concepts involve singleton classes, they serve different purposes and have distinct implications.

---

### Creating a Class with Only One Instance
**The singleton class can also be used to enforce the restriction that there can be only one object of that class in the entire application. This design pattern is called the Singleton Pattern.**

In Ruby, you can create a [`singleton`](https://docs.ruby-lang.org/en/3.2/Singleton.html) object by using the Singleton module. This module provides a convenient way to define a singleton class with just a few lines of code. By including the Singleton module, only one instance of the respective class can be created. 
```

require 'singleton'

class Logger
  include Singleton

  def log(message)
    puts "[LOG] #{message}"
  end
end

logger1 = Logger.instance
logger2 = Logger.instance
Output:
logger1 object ID: 60
logger2 object ID: 60
```
In this example, we define a `Logger class` that includes the `Singleton module`. We create two instances of the `Logger` class, `logger1` and `logger2`, by calling the `instance` method provided by the `Singleton module`. Since the `Logger class` includes the `Singleton module`, calling `Logger.instance` **will always return the same instance of the class**.

To verify whether the instances `logger1` and `logger2` are the same, we output their respective object IDs using the `object_id` method. When you run this example, you'll see that the object IDs of `logger1` and `logger2` are identical, demonstrating that only one instance of the `Logger` class is created.

While it is possible to create singletons without using the Singleton mixin, incorporating the mixin provides important advantages, particularly in terms of **thread safety.** It simplifies the implementation, ensures consistent usage, and provides a standardized API for accessing the singleton instance. 

---

### Practical Use Cases of Singleton pattern
Singleton pattern is a design pattern that restricts the instantiation of a class to a single instance. This is useful when exactly one object is needed to coordinate actions across the system. 

 Assume that we are tasked with managing a system wide cache. 
 
 A simple way to handle this would be as follows
 :
 ```
 class CacheManager
  def initialize
    @cache = {}
  end

  def store(key, value)
    @cache[key] = value
  end

  def retrieve(key)
    @cache[key]
  end

  def clear
    @cache.clear
  end
end
```

`The above implementation might work if we are going to use a single instance of the CacheManager class throughout the entire application.` 

**But if we create multiple instances of the CacheManager class, we may encounter the following issues:**

1. **Inconsistent cache data**: Each instance would have its own separate cache, leading to inconsistent data across different parts of the application.
2. **Resource wastage**: Multiple instances would consume additional memory and resources to maintain their individual caches, resulting in inefficient resource usage.
3. **Synchronization challenges**: If multiple instances modify the cache concurrently, it can lead to synchronization issues and data inconsistencies.

In this scenario, by using a singleton class, we can ensure that there is a single, shared instance of the cache manager throughout the application.
```
require 'singleton'

class CacheManager
  include Singleton

  def initialize
    @cache = {}
  end

  def store(key, value)
    @cache[key] = value
  end

  def retrieve(key)
    @cache[key]
  end

  def clear
    @cache.clear
  end
end
```

In this example, we have a `CacheManager` class that includes the `Singleton` module. **The class ensures that only one instance of the cache manager is created and shared across the application**.

Using the singleton class, we can store and retrieve cached data from anywhere in the application like this:
```
cache_manager = CacheManager.instance
cache_manager.store('user:1', user_data)
cached_user = cache_manager.retrieve('user:1')
```
**Singleton objects are often used for managing global state or resources that should have only one instance**.
`For example, you might use a singleton to handle database connections, configuration settings, or logging functionality.`



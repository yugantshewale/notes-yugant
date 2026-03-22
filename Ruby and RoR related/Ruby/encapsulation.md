### Bundling Data and Methods
```
class Person
  def initialize(name, age)
    @name = name
    @age = age
  end

  def introduce
    puts "Hi, I'm #{@name} and I'm #{@age} years old."
  end
end

person1 = Person.new("Albert",  23)
person1.introduce
```
In this class, the instance variables `@name` and `@age` serve as containers that hold the specific characteristics of an instance of the Person class. The instance method `introduce` can be invoked on a Person object to reveal information about that individual.

The class acts as a unified entity bundling both the data, represented by the instance variables, and the methods that operate on that data. This cohesion establishes a protective boundary, safeguarding the data from unauthorized access and alterations, a principle known as encapsulation.

Encapsulation serves to conceal internal details, exposing only the essential components. Using class objects, we create encapsulated instance variables and methods accessible solely by the object's class or the object itself, restricting access from external sources.

Employing method access control further fortifies this encapsulation, restricting even the object itself from accessing these variables and methods. 

---

### Access Control Modifiers
Ruby provides three levels of access control: `public`, `protected`, and `private`. These modifiers determine the visibility of methods within a class.

**Public**: Public methods can be called by anyone both from outside the class and from within the class. By default, all methods in Ruby are public.

```
class Person
  def initialize(name, age)
    @name = name
    @age = age
  end

  def introduce
    puts "Hi, I'm #{@name} and I'm #{@age} years old."
  end
end

person1 = Person.new("Albert",  23)
person1.introduce
```
In this example, `introduce` is a public method that can be called from any part of the code.

**Protected**: Protected methods can be called only by objects of the same class or its subclasses. They are not accessible from outside the class.
```
class Person
  def initialize(name, age)
    @name = name
    @age = age
  end

  def introduce
    puts "Hi, I'm #{@name} and I'm #{@age} years old."
  end

  protected

    def update_name(new_name)
      @name = new_name
    end
end

class Adult < Person
  def marry(spouse_name)
    new_full_name = "#{@name.split.first} #{spouse_name.split.first}"
    update_name(new_full_name)
  end
end

alice = Adult.new("Alice Smith",  27)
alice.introduce
alice.marry("Richard Roy")
alice.introduce
```
**Private**: Private methods are the most restrictive. They can be called only within the context of the object itself. Private methods cannot be called with an explicit receiver, even if the receiver is self.
```
class Person
  def initialize(name, age)
    @name = name
    @age = age
    @username = generate_username
  end

  def introduce
    puts "Hi, I'm #{@name} and I'm #{@age} years old. My username is #{@username}"
  end

  protected

    def update_name(new_name)
      @name = new_name
    end

  private

    def generate_username
      name_parts = @name.split
      "#{name_parts.first.downcase}_#{@age}"
    end
end
person1 = Person.new("Albert",  23)
person1.introduce
```
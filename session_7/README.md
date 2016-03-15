| [← Session 6](../session_5/README.md) |[ Session 8 →](../session_7/README.md) |
|---------------------------------------|---------------------------------------|

Ruby Course Session 7
=====================

Session Outline:
- Recap
- Classes, a retro
- Built in Classes
- Creating our own Classes
- Modifying existing Classes
- Exercises

Recap from Session 5
--------------------
Last session we used methods and learned how to create our own. We also discussed the benefits of making our methods concise and readable at the same time. Additionally, we compared a few of our own custom methods to loops.

Variables were a big topic in methods! We saw how to deal with multiple known and unknown inputs to our functions.

By this point, you should be feeling much more confident while using the Ruby docs. Don't worry if you still feel confused about the documentation, it takes practice to get to a comfortable point.

Classes, a recap
----------------
We have dealt with a lot of Ruby's core classes in the last 6 sessions. To remind you, here are a few of the main ones:
- String
- Fixnum
- Array
- Hash
- Symbol
- Float

With classes, there are a few keywords/concepts you need to be aware of, knowing about them now will help you massively later on when you are going through documentation or reading a more advanced book on Ruby!
Below are a few of the basic keywords/concepts:

**Ruby Classes keywords:**
1. Instances
2. Inheritance
3. Getters
4. Setters

I encourage you to spend some time researching these 4 points and how they fit in with Ruby classes. When you are done, we'll discuss them in more depth.
*Hint*: To find the parent object, you can use a mix of these methods: `class`, `ancestors`, `superclass`

### Float example
Let's take a sample float to help us understand the basics of classes.

```ruby
var = 2.3

var.class # => Float
var.class.ancestors # => [Float, Numeric, Comparable, Object, PP::ObjectMixin, Kernel, BasicObject]
```

We basically found the 'family tree' for that given float!
But what does that really mean? Is `var` a part of the float class? Well, not really.

We simply created an *instance* of the Float class, a class which contains the necessary attributes and methods that allow us to manipulate the `var` variable as a Float! You can think of this process of creating an instance as being similar to a master recipe that we can use to make some cake. Who doesn't like cake :P

Built in Classes
----------------
Other than the classes that we have come across so far, there are many more built into Ruby's Core or Standard Lib. To find out more about this, please see the [documentation](http://ruby-doc.org/)

I'm going to introduce a few classes that are useful for scripting and general usage. Before doing that, let's cover how we used to create instances of the classes we have come across so far.

```ruby
# Strings
str = ""

# Arrays
arr = []

# Hashes
hsh = {}

# Integers
int = 123

# Floats
flt = 12.3
```

We have rarely used the `new` method to create an instance of these classes. That is because Ruby makes it so much easier for us to get straight to the point and create them intuitively as shown above! However, this does not apply to all classes as we shall see later.

### Time Class
Time is a built-in class that represents time :)
It can be manipulated with simple arithmetic in order to get the time in the future or past. The integer 1 represents 1 second when dealing with this class, and here is an example to illustrate that:

```ruby
time = Time.new

puts time
# => 2016-03-14 20:01:39 +0000

time + 1
# => 2016-03-14 20:01:40 +0000
```

Cool. So, now its time to think about what the above output means. Take a minute to think about it and play with the time class in `irb`, and when you are done let me know what you think.

### Range Class
We have used this class in some of the previous sessions. This is a widely used class.
Ranges can be used for letters and numbers, and because it belongs to Enumerables, we can apply a lot of handy methods to ranges. If you cant remember Enumerables from last session, I would recommend searching for them on Google.

Also, please see dig up on the Range class from the documentation.

There is one main feature provided by ranges that can be replaced by another feature that is provided by Strings. Let's say we want to check if a certain file is a `pdf`, here's how this might come into play:

```ruby
def pdf_checker(file_name)
  if file_name[-4, 4] == '.pdf'
    true
  else
    false
  end
end
```

This is a clear function that is checking the last four characters to see if it is a pdf. We can rewrite this method using ranges, like so:

```ruby
def pdf_checker(file_name)
  if file_name[-4..-1] == '.pdf'
    true
  else
    false
  end
end
```

As we can see, there are many ways to do the same thing in Ruby.

Creating our own Classes
------------------------
Everything in Ruby is modifiable, this includes classes. So we can create our own classes and make use of them.
Let's say we need to use an object that does not yet exist in Ruby, we would go about creating a class for it!

Let's assume we have a virtual car that we can drive around and eventually park. We can break down our requirements into verbs and nouns, and since methods are messages, they will closely resemble a verb (something is being done).

So we can take two verbs from our car example: drive and park.

```ruby
def drive
  "Car is driving"
end

def park
  "Car is parked"
end
```

So we now have to basic methods that output a string that simply informs us what the car is doing. This is where a class would come in to capture all this behaviour in one place and allow these methods to belong to a larger object.

To create our class:

```ruby
class Car
end
```

Notice that we capitalize the class name, unlike in methods, and if we have more than one word, it would take on this format:
`class FastCar`

So, after we declare our class, let's throw in the methods.

```ruby
class Car
  def drive
  end

  def park
  end
end
```

Now that we have our methods, let's think about how we can make them send meaningful messages as objects. This is where we will start using instance variables. Remember them from last time? These are variables that last as long as the object does. So, when we instantiate a new object from the Car class, the instance variable in this new object will last until we close the program. Unlike local variables that last as long as the method itself.

So just a recap on instance method syntax:

```ruby
@status = "This is a string"
@status = 123
```

They are variables at the end of the day so don't get confused :)

Going back to our Car class, lets add some instance variables so that we can get the status of the car:

```ruby
class Car
  def drive
    @status = "Driving"
  end

  def park
    @status = "Parked"
  end

  def status
    @status
  end
end
```

Any idea what we did here? Take a few and let me know what you think.

Also, how would be able to test this out in `irb`?

### Using `irb` to test our class.
Say we have a file named `car.rb` inside our current directory and we want to see how we can use the methods of this new class as an external part of our Ruby language.

This is where `require` comes into play!

You would have to fire up `irb` and then type in: `require "./car.rb"`.
Any idea what this command resembles?

After we required the file that contains the new class, we can now play around with it in `irb`. However, we still need to create a new instance of the class like so:

```ruby
:001 > require './car.rb'
 => true
:002 > car = Car.new
  => #<Car:0x007ff99aa52c10>
```

So we now have a new object that we can talk to.

```ruby
:003 > car.status
  => nil
```

As you can see we called the method `status` but it returned `nil`. Any idea why?

Spend a few minutes playing with this class until you fully understand what is happening.

*Hint*: To view the class' methods, use the `method` method to show you the available ones :P
Usually, the ones that were most recently created will be displayed first!

### Initialize your engines
Sure all is this is fun. But this still doesn't make sense to have a car that is neither parked nor driving when we first create it! Common sense would be to have a car that is parked when created, correct?

That's where the `initialize` methods comes in. This is a built in method that comes with every class. It allows us to add behaviour to a certain class when it is created. As an example, let's see how this may apply to our car class.

```ruby
class Car
  def initialize
    @status = "Parked"
  end

  def drive
    @status = "Driving"
  end

  def park
    @status = "Parked"
  end

  def status
    @status
  end
end

```

If you exit your previous `irb` session and start a new one, require the file again and then create a new Car object, you should see something new. Share with us what you find.

Also try to find the difference between `new` and `initialize`.

Exercises
---------

### Exercise 1
Change the display of the time class to output in the following format:

```ruby
day/month/year hour:minute:second timezone
```

### Exercise 2
Assuming you were born on midnight, find how old you are in terms of seconds, using the `Time` class.

### Exercise 3
Build a class called `Die` that has the required behaviour of rolling dice and showing a score at the end. Remember the dice rolls have to be random!

### Exercise 4
Remember Pokemon? We're going to create a new game that is called RubyMons (short for Ruby Monsters). In order to play this game properly, our RubyMons should have the following:
- have names
- can sleep
- can eat
- can walk

### Exercise 5
Let's extend our RubyMons to be able to fight each other. In doing so, they will have to have a "strength" rating.
This is where it gets challenging; try to find out how we can get these RubyMon to fight and then find out who won at the end of the battle!


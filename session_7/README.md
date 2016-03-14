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

Exercises
---------

### Exercise 1
Change the display of the time class to output in the following format:

```ruby
day/month/year hour:minute:second timezone
```

### Exercise 2
Assuming you were born on midnight, find how old you are in terms of seconds, using the `Time` class.


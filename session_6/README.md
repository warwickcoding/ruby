| [← Session 5](../session_5/README.md) |
|---------------------------------------|

## Ruby Course Session 6

Session Outline:
- Recap
- Methods, a Retro
- Creating our own methods
- Exercises

Recap from Session 5
--------------------
Last session we used hashes and learned about their role as a data structure. We also compared them to arrays and saw how we can use them together if we need to.

We also made a clear distinction between the hash syntax and the Ruby block syntax. It could be confusing at the beginning because they both use `{}`.

We used documentation heavily to learn how to find something we are looking for. It is okay to start with Google sometimes, but I would recommend using the documentation first if you know what your are looking for.


Remembering Methods
-------------------
If we remember from the previous sessions, methods have been used quite a lot. So far, we have been using methods that belong to certain classes provided by the core Ruby language.

Methods are Ruby's functions. Their job is to send a message to another object and this message can perform other functions, collect data or even produce some output. There are so many different things we can do with a method. The following list contains a few of the methods we have come across so far.

- `to_s`
- `+`
- `==`
- `each`
- `map`
- `select`
- `count`

We can see how methods/functions are an essential part of any language. Luckily for us, the Ruby language is full of great methods that we don't need to write on our own, they are simply shipped with the language.



Creating our own Methods
------------------------
Before we go into creating our own custom methods, we'll take a look at two examples. The first one will use loops and conditionals, while the second will be a custom method that does the same thing, more efficiently.

```ruby

# Without a custom method:
name = "Mike"
puts "Hello #{name}"
# => Hello Mike

name = "Sally"
puts "Hello #{name}"
# => Hello Sally

# ============================

# With a custom method:
def hello(name)
  puts "Hello #{name}"
end

hello("Mike")
# => Hello Mike

hello("Sally")
# => Hello Sally
```

From the above examples, we can see that the second way allows us to reuse the code multiple times without having to repeat the same lines over and over again. This is just a simple example that shows the power of methods. Before we move on to more complicated examples, lets break down the simple custom method.

The first thing that we have to do to declare a method is to define its name and end it:

```ruby
def hello
end
```

Next, we have to decide if the code inside this method requires any outside information, and in this case the answer is **yes**, because we have a new name that we want to say hello to. This is where we add an arbitrary name to the parameter/argument after the name of the method. What you use as the name of the argument(what is inside the parenthesis) doesn't matter as long as it is readable and easily understood by anyone who goes over the code. In this case I call it "name" because that is what is going to be passed in, a name of a person.

```ruby
def hello(name)
end
```

After that, we can start writing our method from the inside.

```ruby
def hello(name)
  puts "Hello #{name}"
end
```

Let's move on to something with more arithmetic:

```ruby
def doubler(number)
  number *= 2
  puts number
end

doubler(4)
# => 8

doubler(92)
# => 184
```

Take a few moments to understand what is happening here.

Return
------
There is a special keyword that is used inside methods called `return`. When this is called, it will exit the method and no code in the method is executed after the `return`. Let's take a look at an example:

```ruby
def whats_my_name(name)
  puts "Your name is:"
  return
  puts name
end

whats_my_name("Carlos")
# => Your name is:
nil
```

We can see that the argument `name` was never returned. This is because the `return` stopped the method at a point before we actually display anything. If you remember the `break` from loops, this acts in a similar way. You have to be cautious when using `return` because it can result in unnecessary issues if used in a wrong way.

There is another important point that you need to know about methods. Methods return the last line of code that is executed if not explicitly returned elsewhere. Here is an example that shows this in action:

```ruby
def name
  first_name = "Huckleberry"
  last_name = "Finn"
  age = 13
end

name
# => 13
```

You have to be careful if you are feeding in the output of a certain method into another place, as this will only execute the last line. So, for the above example, feeding in `name` will result in the following:

```ruby
if name == "Huckleberry"
  puts "Hello Finn!"
else
  puts "huhh??"
end

# => huhh??
```

If we switch around the lines in the expression to have the `first_name` as the last line in the method, our condition will pass and thus return `"Hello Finn!"`. This example was used to purely demonstrate how the last line is being returned in methods.

Methods and variables
---------------------
When dealing with methods, we will come across loads of variables inside and outside these functions. By taking a look at the following snippet, can you decide what will be returned?
Take a minute to think about this before you decide 😀

```ruby
def name
  first_name = "Huckleberry"
  last_name = "Finn"
  age = 13
end

puts first_name
puts name.last_name
puts age + 12
```

This is where it gets interesting and probably confusing, so don't worry if this takes some time to sink in. There are different scope levels when talking about variables, for now the only one we should be concerned with is the "local variable". Local variables are accessible only inside the defined space. In the case of methods, this means that "normal variables" that are **only** defined inside a certain method cannot be accessed outside it. What do we mean by a normal variable?

```ruby
# Normal/Local Variable:
name = "Jimmy"

# Instance Variable
@name = "Jimmy"

# Class Variable
@@name = "Jimmy"

# Global Variable
$name = "Jimmy"

# Constants
NAME = "Jimmy"
```

Local variables are the variable type that we have been dealing with so far. Don't worry about the other types for now, but feel free to read more about them [here](http://www.tutorialspoint.com/ruby/ruby_variables.htm).

Going back to the previous example, when we call on a local variable that is defined outside our scope, we will get the following error: `undefined local variable or method`. This gives us a hint, that we are calling on something that is currently not accessible to us, even if we did define it elsewhere.

Here is another example that will aim to illustrate the different levels of scope:

```ruby
age = 98

def my_vars(age)
  age = 77
  puts age
end

my_vars(age)
# => 77
puts age
# => 98
```

So you can see that our original variable was not changed, even though we did something to it inside the method. Think about similar cases as having two different variables rather than one.


Multiple Arguments
------------------
So far we have been creating methods that accept one argument only. This is not a general rule, methods can accept as many arguments that we set out.
It is also important to note that in Ruby, the data type of the argument doesn't have to specified at the top level. This is something that Ruby handles on its own. In other words, we don't have to specify that a certain argument input is going to be a string or integer.

### Two or more args
Let's take an example in which we want to add two numbers to each other:

```ruby
def add(num1, num2)
  num1 + num2
end

add(1, 9)
# => 10

add('ab', 'cd')
# => 'abcd'
```

### Splat Operator
Placing a splat operator `*` infront of a argument name means that this will take on an undefined number of arguments. This could be useful when we are expecting an unknown number of inputs to the method. A good example would be applying some calculations to incoming weather reports.

**NOTE**: When you pass in arguments to a method with a splat, these arguments are stored in an array! Think about that next time you want to manipulate the data

```ruby
def avg_temp(*temps)
  sum = 0
  temps.map |temp| do
    sum += temp
  end

  sum/temps.length
end

avg_temp(1, 2, 9)
# => 12

avg_temp(32, 7, 1, 18)
# => 58
```

### Default Values
Sometimes, we want to place a specific value to unused arguments. This could apply in an example where we provide an option to enter values, otherwise our preset values will take place.

```ruby
def favourite_colour(colour="Blue")
  puts "Your favourite colour is #{colour}"
end

favourite_colour()
# => Blue

favourite_colour("Red")
# => Red
```

Method errors
-------------

Make sure that you cover the following steps when dealing with methods:
- methods should be defined before calling them, otherwise Ruby will raise an exception for undefined method invoking.
- using `def` and `end` to contain your method logic
- using lowercase letters and underscores for naming methods
- `()` immediately after the method name
- if using more than 1 argument, are they separated by commas
- using correct indentation


Exercises
---------

### Exercise 1
Write a method that will take in a number and return the square only if it is even. If it is odd, return a message of your choice

<!--
SOLUTION:
```ruby
  def square(num)
    squared = num**2
    if squared.even?
      return squared
    else
      puts "This number is not even, #{squared}"
    end
  end
```

-->

### Exercise 2
You must take the following method and write the underlying logic to allow it to tell us if a string is upcase or not.

```ruby
def str_upcase?(string)
  .....
  .....
end
```

<!--

SOLUTION:
```ruby
def str_upcase?(string)
  if string == string.upcase
    true
  else
    false
  end
end
```

-->

### Exercise 3
Write a method that will take in an argument and then display that to the user reverse and capitalized.
So for example:
```ruby
"name" => "Eman"
"Bond" => "Donb"
"CARS" => "Srac"
```

### Exercise 4
Compare the following examples and decide if they are valid or invalid:

```ruby
# example 1
def add(abcdef + yeah)
 abcdef + yeah
end

# example 2
def show_name (name)
  puts "Your name is #{name}"
end

# example 3
def personal_information name, age, nationality, height
  # bla bla bla
end

```

### Exercise 5
Write a method called `ask` which will ask a user questions and the program will then display messages corresponding to the users answer.

Your questions should be inside the method, for example: "Do you like coffee?", and depending on the users answer to that question, you can display a message.

Place at least one of your questions inside a loop so that the user will keep getting asked the same questions until they answer yes or no.

```ruby
def blabla

  while ....
    puts "aksdkajsdla"
    user_input = .....
  end

  puts "alskdja"
  user_answer = ....

  if user_answer == ....
    puts "asdasd"
  end

  puts "Thank you for answering the questions :)"
end
```

### Exercise 6
Recreate the arithmetic in Ruby: `+-*/` as new methods where you can pass in 2 numbers and the result is outputed

### Exercise 7
Using the the methods you created from Ex 6 and extend them to accept multiple inputs, through a splat operator `*`. Revisit the section above if you need to.
As a hint, look up the `inject` method for arrays. :)

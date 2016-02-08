| [← Session 2](../session_2/README.md) | [Home](..) |
|---------------------------------------|-------------|

##Ruby Course Session 3

Session Outline:
- Recap
- Loops
- Types of Loops
- Introduction to documentation
- Exercises



Recap of Session 1
------------------
In the previous session, we learned how to use Ruby's interactive shell (`irb`). We also learned a bit more about the object-oriented nature of this language. We dived deeper into the different data types, such as integers, floats, strings, symbols, and booleans.

Variables were a big topic as well. We were introduced to capturing input and output into a ruby variables.
In addition to the above, we learned how to assign a datatype, how to convert from one data type into another one.

Finally, we started using conditional statements with `if` `else` `elsif`.

Here's a sample program that allows you to output different messages depending on what a sample variable holds.

```ruby
puts "Please enter a number:"
num = Integer(gets.chomp)

if num < 0
  puts "This is a negative integer!"
elsif num > 0
  puts "This is a positive integer!"
else
  puts "This is zero!"
end
```

Can you notice anything different about the variable?
*Hint*: We used to capture user output by using only `gets.chomp` and then converting that to and integer.

Before we move onto the next part, it is worth pointing out that there is a cleaner way to express a conditional statement if we are comparing negatives. Take a look at the following example:

```ruby
num = gets.chomp.to_i

if num != 0
  puts 'This is not zero!'
end

# Versus

unless num == 0
  puts 'THis is not zero!'
end
```

To break it down, think about the difference between `if` and `unless`.

Let's say I wake up in the middle of the night and I'm not sure if I should drink water.
```ruby
thirsty = true

if thirsty == false
  puts 'Go back to bed!'
else
  puts 'Go drink water!'
end

# Versus

thirsty = true

unless thirsty
  puts 'Go back to bed!'
else
  puts 'Go drink water!'
end
```

The question would be when to use `if` and when to use `unless`. This is dependant on the situation, at the end of the day we want to write code that is readable, so what ever does the job in a better manner. The more you practice this, the better you become at deciding.

Loops
-----

What if we want to repeat something multiple times while a certain condition is held, but we don't know how many times to repeat that action.

This is where loops come into the mix. Loops are meant to repeat something until you give a condition to stop the loop.

Let's uncover loops by taking a look at an example without loops. What if I wanted to print a string 10 times, so far we have learnt to do the following:

```ruby
# Without a loop

puts "I love Ruby!"
puts "I love Ruby!"
puts "I love Ruby!"
puts "I love Ruby!"
puts "I love Ruby!"
puts "I love Ruby!"
puts "I love Ruby!"
puts "I love Ruby!"
puts "I love Ruby!"
puts "I love Ruby!"
```

That does not seem efficient at all! A loop can help us get rid of all this repetitiveness.

```ruby
# With a loop

counter = 0

while counter < 10
  puts "I love Ruby!"
  counter = counter + 1 
end
```

That's much much better! 

Let's start with the counter variable in which we're storing a starting number for the loop. In this case, the loop will assess if the counter reached a value greater than 10. If it has not, then it will puts a string and it will then add 1 to the counter. This happens on and on until we reach the preset threshold, which is anything over 10.

When we reach 11, which is naturally the first number after 10, the condition will evaluate to `false`, thus ending the loop.

Loops can be used for endless purposes. As long as a process requires some repetition, there is a place for loops.

Let's look at another example:

```ruby
name = ""

while name != "Mike"
  puts "What is your name?"
  name = gets.chomp
end

puts "Hello Mikey!!!"
```

`while` is testing our condition to check if name is `== Mike`. The initial run will obviously be false because we declared `name` as an empty string. Then the program ask for an input and that input is fed into the loop again!

```flow
st=>start: name == ""
e=>end: puts "Hello Mikey!"
op=>operation: is name == "Mike" ?
cond=>condition: Processing...

st->op->cond
cond(yes)->e
cond(no)->op
```

We can also set a condition to interrupt the loop like so:

```ruby
name = ""

while true
  puts "What is your name?"
  name = gets.chomp
  if name == 'Mike'
    puts "Hello Mikey!!!"
    break
  end
end
```

Take great caution when dealing with loops because they could run into an infinite loop. To break out of such a loop, you can press CTRL + C.



Types of Loops
--------------
The first type of Ruby loop that we have come across so far is the `while` loop. In Ruby there are a few more.

###For loop
Here is a sample `for` loop:

```ruby
for i in 1..15
  if i.odd?
    puts "#{i} is odd"
  else
    puts "#{i} is even"
  end
end
```

Can you spot some differences between this loop and the `while` loop?

As always, let's break it down.
- `for` is a Ruby keyword that marks the beginning of a loop
- `i` is an arbitrary value, it can be anything else. This references the current iteration of the loop. You can call it the `current_iteration_number` if you like.
- `in` is another Ruby keyword that is used to point towards `1..15`
- `1..15` is a Ruby Range. The first number is the lower bound and the second number is the upper bound.

###Times loop
This loop is a bit different. It allows you to repeat something by sending a message to an integer.

```ruby
5.times do |i|
  i * 2
end

# => 02468
```

- `5` is a sample number. You can set this to be the number of iterations you would like to perform.
- `times` is the method name
- `do` marks the beginning of a Ruby block. We'll discuss blocks in the next sessions.
- `|i|` again i is an arbitrary value for the variable that we use to keep track of current iteration. It has to be set after the `do`. Also, bear in mind that this could be avoided depending on if you would like to access the iteration number or not.
- `end` this marks the closing of the loop.

Here is another usage of `times` without setting a variable:

```ruby
3.times do
  print "chooo "
end

# => chooo chooo chooo
```

###Upto and Downto loops
These two loops act in opposite ways. They are similar to `times` in the sense of sending a message to an integer. However, notice the number in parenthesis being introduced after `upto` and `downto`. This is what we call a parameter or argument. Some methods require you to pass them a parameter, while others are optional.

```ruby
# Upto
1.upto(5) do |i|
  print i
end

# => 12345

# Downto
1.downto(-5) do |i|
  print i
end

# => 1 0 -1 -2 -3 -4 -5
```

####NOTE
You have noticed by now that some loops are similar to others, it is great to experiment with all different types and then use the one that does the job in the most efficient way.



Intro to documentation
----------------------
You might have come across this world before. You can think of documentation as a manual to understand what's happening under the hood of a programming language or framework. Documentations are one of the most underrated aspects of open-source. If you ever get involved with any project, you will understand how a lack of clear and expressive documentation is a big pain. These documents are compiled, edited and written over a span of years.

In our case, we care about Ruby documentation. Naturally, the first place to look would be the [official Ruby documentation page][2].



Exercises
---------

###Exercise 1
Look at the following statements and decide whether each one is true or false.

```ruby
a = 153 != 153

b = -67 < -33

c = -9 <= -9

d = 10 == 1000
```

###Exercise 2
Same thing here but we're adding boolean operators to the mix `&&` and `||`

```ruby
a = 63 < 89 && 55 < 55

b = 2**3 != 3**2 || true

c = false && 50 == 50

d = false || -10 > -9

e = 3**2 == 9 && 4**2 == 16

f = false || false

g = true || true
```

###Exercise 3
Same thing but with the 'not' operator `!` 

```ruby
a = !true

b = !true && !true

c = !(50 / 5 == 10)
```

###Exercise 4
Fix the following program, it seems to keep running non stop 😵

```ruby
while true
  puts "Tell me to do something"
  user_request = gets.chomp
end
```

###Exercise 5
Again fix the following program so that it will display a number at the end of the program consisting of 1..`threshold`. 
For example, if I enter 10, it should return `"12345678910"`

Notice the `<<`, this is called a shovel operator. Try to find what it's used for.

```ruby
  puts 'Enter a number to act as a threshold'
  threshold = gets.chomp

  final_number = ''
  i = 0

  while i <= threshold
    res << i
  end
```

###Exercise 6
Write a program to print put the lyrics of the song "99 Bottle of Beer on the Wall". If you are unfamiliar with the song, check it out [here][1].

*Hint*: Use a loop for the repetitive stuff.

  [1]: http://www.99-bottles-of-beer.net/lyrics.html://www.99-bottles-of-beer.net/lyrics.html
  [2]: http://ruby-doc.org/





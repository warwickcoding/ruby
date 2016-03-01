| [← Session 4](../session_4/README.md) |
|---------------------------------------|

## Ruby Course Session 5

Session Outline:
- Recap
- Hashes
- Exercises

Recap of Session 4
------------------
In the previous session, we were introduced to Arrays Ruby language. With arrays we were able to start making use of data structures in the scope of accessing and modifying elements in a list.

Hashes
------
Hashes are the older cousin to arrays. The have more functionality but still share some features with arrays. Unlike arrays, hashes don't have to use integer indices like arrays; they can use any data type to do so. Don't worry if this might sound a bit confusing, we'll clear this up later.

Before explaining hashes any further, lets take a quick look at the code difference between a hash and an array, both of which contain person information for a given user.

```ruby
# Array implementation
info = ['Mike', 'Ike', 29, 'Blue']

# Hash implementation
info = {
  'First name' => 'Mike',
  'Last name' => 'Ike',
  'Age' => 29,
  'Eye colour' => 'Blue'
}
```

Just a quick glance at both structures tells a lot about hashes. First of all, data is stored in `{}` rather than `[]`. Secondly, we have a better way to call on the actual elements with the introduction of the key and value pairs. A key is what helps us in accessing the actual value, so for example, we can directly ask the info hash to return the age of our user without having to know its index, and we can do it like so:

```ruby
puts info['Age']
# => 30
```

The above example also reminds us of how to access an element in an array. It is practically the same syntax.

Another point that can be noticed is the hash rocket `=>`, this points a given key to its value. This is the old way of expressing keys and values, but it is still used widely.

So how do we go about creating a Hash without using the **literal notation** like we did in the above examples?
Well this is where it also reminds of creating an Array. We would use the method `new` and call it on the Hash class like so:

```ruby
info = Hash.new

puts info
# => {}
```

#### Iterating over Hashes
This is another area that we learned when we dealt with arrays. This will be slightly different with hashes.
As a reminder, when we "Iterate" through an array/hash, we are basically looping through them for a finite number of iterations.

`.each` was a big one from arrays. We will use it again here for hashes quite a lot.
Let's just first take a look at the syntax of `each` when used for a hash and then we will go into further details about the optional parameters and so on.

```ruby
# Taking the info hash from the above examples:

info.each do |key, value|
  puts "your #{key} is: #{value}"
end

=begin
your First name is: Mike
your Last name is: Ike
your Age is: 29
your Eye colour is: Blue
=end
```

This looks way easier that having to specify what every element in an array contains. We are simply telling the hash to return each key and its value, andif you take a close look after we called the `.each` method, you can see that we now have two parameters because of the key-value pair in hashes.

*Side note*: if you feel that this is confusing you, don't worry, everyone gets confused when you start dealing with more parameters and optional arguments. Let's go the official [Ruby docs](http://ruby-doc.org/) in order for us to see how to make sense of all this.

If we look under the 2.3.0 Core, and then look for the Hash Class documentation, we will get to a page that looks like this:

![Hash docs](../images/session_5/ruby_session_5-1.png)

On the side bar, we can look for the `each` method and from there well see this:

![Hash#each doc](../images/session_5/ruby_session_5-2.png)

Exercises
---------

### Exercise 1

### Exercise 2
### Exercise 3
### Exercise 4
### Exercise 5


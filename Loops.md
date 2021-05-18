# Loops
Luke Morrison - 12 May 2021

[Back](/README.md)

Now that we have a basic understanding of Objects and Data Types, we are ready to get our hands dirty with loops.  Now that we have an efficient way to store values into colletions with Arrays and Hashes, let's explore how we can programatically access each value in sequence.

First, a very basic example though:

```ruby
3.times do
    print 'MAYDAY ' # => 'MAYDAY MAYDAY MAYDAY '
end
```

[`TRY IT OUT`]("https://try.ruby-lang.org/")

Here we are using the `times` method on the Integer object.  This allows us to repeat the specified behaviour 3 times. But now let's set some conditions.  It would be nice if we could have our program loop only as long as a condition is `true`. This can be done with both `while` and `until` loops.

### While

The `while` keyword requires a conditional statement, and will continue to execute the define block until the condition is satisfied:

```ruby
infinity_stones = 0

while(infinity_stones < 6)
    infinity_stones += 1
end

print infinity_stones # => 6
```

From the above example, our condition is tested before the loop is execute and must test `true` for the block to be executed.

[`TRY IT OUT`]("https://try.ruby-lang.org/")

### Until

Similar to `while` though has one main difference - an `until` loop will test a condition and only run the block when the condition is `false`:

```ruby
infinity_stones = 0

until(infinity_stones == 6)
    infinity_stones += 1
end

print infinity_stones # => 6
```

[`TRY IT OUT`]("https://try.ruby-lang.org/")

### For

Getting a little more adventurous, let's we want to create a stopwatch.  Assuming we want to count to 5, we can print a value each second using the following for loop:

```ruby
for second in 1..5 do 
    print(second)
    sleep(1)
end
```

### (For) Each

Now let's consider we are working with an array:

```ruby
characters = ['sonic', 'tales', 'knuckles', 'eggman']
```

Wouldn't it be nice to print each of these character name individually - perhaps as a list.  Let's use the `each` method:

```ruby
character.each do |name|
    print name
end

# sonic
# tales
# knuckles
# eggman
```

### Map

Shouldn't the names start with a capital letter? They are proper nouns after all.  If this is the case, we would like to loop through each item in the array and *change* the current value.  This is done using the `map()` method:

```ruby
characters = ['sonic', 'tales', 'knuckles', 'eggman']

capitalized_characters = characters.map do |name|
    name.capitalize
end

# capitalized_characters = ['Sonic', 'Tales', 'Knuckles', 'Eggman']
```

Notice how we must define the result of this method as a new variable.  In some cases however, this is not required. `map`, like several other array/hash methods can be suffixed with an exclamation mark `!`. In Ruby, an `!` indicates that the value should be changed in place, thus removing the requirement to *redefine* you data.

```ruby
characters = ['sonic', 'tales', 'knuckles', 'eggman']

characters.map! do |name|
    name.capitalize
end

# characters = ['Sonic', 'Tales', 'Knuckles', 'Eggman']
```

See - much cleaner. Note now though that your original `characters` array has forever been changed, so use this new found power with caution.


[`TRY IT OUT`]("https://try.ruby-lang.org/")

# Loops

[Back](/README.md)

Now that we have a basic understanding of Objects and Data Types, we are ready to get our hands dirty with loops.  With Arrays and Hashes, let's explore how we can programatically access each value in sequence.

First, a very basic example though:

```ruby
3.times do
    print 'MAYDAY ' # => 'MAYDAY MAYDAY MAYDAY '
end
```

[TRY IT OUT]("https://try.ruby-lang.org/")

Here we are using the `times` method on the Integer object.  This allows us to repeat the specified behaviour 3 times. But now let's set some conditions.  

### While

It would be nice if we could have our program loop only as long as a condition is `true`. This can be done with both `while` and `until` loops. The `while` keyword requires a conditional statement, and will continue to execute the define block **while the condition is satisfied**:

```ruby
infinity_stones = 0

while(infinity_stones < 6)
    infinity_stones += 1
end

print infinity_stones # => 6
```

From the above example, our condition is tested before the loop is execute and must test `true` for the block to be executed.

[TRY IT OUT]("https://try.ruby-lang.org/")

### Until

Similar to `while` though has one main difference - an `until` loop will only run **until a condition is satisfied**:

```ruby
infinity_stones = 0

until(infinity_stones == 6)
    infinity_stones += 1
end

print infinity_stones # => 6
```

[TRY IT OUT]("https://try.ruby-lang.org/")

## While vs. Until

These two are easily confused, so let's see a comparison.  We'll need exactly [99 bottles of beer on the wall](https://en.wikipedia.org/wiki/99_Bottles_of_Beer) to prove our point:

```ruby
beers = 99

# While the number of beers is greater than zero.
while(beers > 0)
    print beers # bottles or beer on the wall, 99 bottles beer
    beers -= 1 # take one down, pass it around
end
# => 99...98...97...1

# OR

# Until the number of beers equals one.
until(beers == 0)
    print beers
    beers -= 1
end
# => 99...98...97...1
```

I've never finished this song, so let's assume it has no ending...

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

Wouldn't it be nice to print each of these character names individually - perhaps as a list.  Let's use the `each` method:

```ruby
character.each do |name|
    print "#{name}\n"
end

# sonic
# tales
# knuckles
# eggman
```

### Map

Shouldn't the names start with a capital letter? They are proper nouns after all.  If this is the case, we would like to loop through each item in the array and *change* the current value.  This is done using the `map` method:

```ruby
characters = ['sonic', 'tales', 'knuckles', 'eggman']

capitalized_characters = characters.map do |name|
    name.capitalize
end

# capitalized_characters = ['Sonic', 'Tales', 'Knuckles', 'Eggman']
```

Notice how we must define the result of this method as a new variable.  In some cases however, this is not required. `map`, like several other array/hash methods can be suffixed with an exclamation mark `!`. In Ruby, an `!` indicates that the value should be changed in place, thus removing the requirement to *redefine* your data.

```ruby
characters = ['sonic', 'tales', 'knuckles', 'eggman']

characters.map! do |name|
    name.capitalize
end

# characters = ['Sonic', 'Tales', 'Knuckles', 'Eggman']
```

See - much cleaner. Note that your original `characters` array has forever been changed, so use this new found power with caution.

### Select (Filter)

It would be nice if we could store more information about these characters, so let's reimagine our array using hashes for each character:

```ruby
characters = [
    {
        name: 'Sonic',
        team: 'good'
    },
    {
        name: 'Tales',
        team: 'good'
    },
    {
        name: 'Knuckles',
        team: 'good'
    },
    {
        name: 'Eggman',
        team: 'bad'
    }
]
```

Now, we can see which characters belong to which *team*.  This is a great improvement, now lets see if we can extract only those characters who are **good**:

```ruby
good_team = characters.select do |character|
    character[:team] == 'good'
end

# good_team = [
#     {
#         name: 'Sonic',
#         team: 'good'
#     },
#     {
#         name: 'Tales',
#         team: 'good'
#     },
#     {
#         name: 'Knuckles',
#         team: 'good'
#     }
# ]
```

Here we are only selecting the elements of an array who have a `team` *attribute* of `good`.  Remember that methods like `select` require a conditional statement to be defined inside their block. Select also has an `!` variant.

[TRY IT OUT]("https://try.ruby-lang.org/")

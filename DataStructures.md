# Data Structures

Data Structures are designed to enable efficient access and modification of data.  For example, a *sentence* as we know it in English, is known to the geeks as a `String`.  In Ruby a String exists has an object and has characteristics and behaviours beyond its *value*.  Imagine the contact list in your phone.  A person's name is used to identify all of their contact information.  In computer science this is often know as a `dictionary`- though in Ruby we call these `Hashes`.  You can see that interacting with a String is likely quite different than interacting with a hash, and you'd be right.

## String

One of the most primitive data structures, a [String](https://ruby-doc.org/core-3.0.1/String.html) is used when text is to be stored. Embedded numbers are fine inside of strings, just note that they will be treated as letters rather than numbers in this case. Strings are defined between single `'` or two double `"` quotes.

```ruby
first_name = 'Banjamin'
```

Ruby also allows you to embed variables into strings dynamically:
```ruby
first_name = 'Banjamin'

print "Your first name is: {#first_name}." # => Your first name is: Benjamin.
```

Take the following string: ```1sgbv5sdgg```.  We need to figure out how long it is, and how many `g` it contains.  Now, visit the [String](https://ruby-doc.org/core-3.0.1/String.html) documentation and see if you can find the functions that can help with this.

## Integer



## Array

If you've ever been to a chinese buffet, you will undoubtably know that fortune cookies tend to come with *lucky numbers*.  This group of numbers can be represented as an [Array](https://ruby-doc.org/core-3.0.1/Array.html).  An array is an ordered collection of data structures.

```ruby
lucky_numbers = [13, 56, 23, 107]
```
It is important to note that these values are specficially ordered and can be refered through their `index`.  Arrays in Ruby start at index 0. You may get a value at a certain index in the following ways:

```ruby
# Single Index
first_lucky_number = lucky_numbers[0] # => 13
# Backward Index
last_lucky_number = lucky_numbers[-1] # => 107
## Range
range_of_lucky_numbers = lucky_numbers[0..1] # => [13, 56]
```

## Hash

## Symbol


[`TRY IT OUT`][try]


[try]: "https://try.ruby-lang.org/"

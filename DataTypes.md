# Data Types

[Back](/README.md)

Data Types are classes of concrete objects used to store different variations of data.  For example, a *sentence* as we know it in English, is known to the geeks as a `String`.  In Ruby a String exists as an object and has characteristics and behaviours beyond its *value*.  Imagine the contact list in your phone.  A person's name is associated to all of their contact information.  In computer science this is often know as a `Dictionary`- though in Ruby we call these `Hashes`.  You can epect that interacting with a string is likely quite different than interacting with a hash, and you'd be right.

## String

One of the most primitive data types, a [String](https://ruby-doc.org/core-3.0.1/String.html) is used for storing text. Embedded numbers are fine inside of strings, just note that they will be treated as string characters rather than numeric in this case. Strings are defined between single `'` or double `"` quotes.

```ruby
first_name = 'Banjamin'
```

With double-quotes, we can do something called *string interpolation* - allowing us to embed dynamic data into strings:
```ruby
first_name = 'Banjamin'

print "Your first name is: #{first_name}." # => Your first name is: Benjamin.
```

Take the following string: ```1sgbv5sdgg```.  We need to figure out how long it is, and how many `g` it contains.  Now, visit the [String](https://ruby-doc.org/core-3.0.1/String.html) documentation and see if you can find the functions that can help with this.

[TRY IT OUT](https://try.ruby-lang.org/)

## Integer

An [Integer](https://ruby-doc.org/core-2.5.0/Integer.html) extends the [Numeric](https://ruby-doc.org/core-2.5.0/Numeric.html) class and is any numeric value that does not contain a decimal value.  They can be positive or negative.

```ruby
positive_int = 1
negative_int = -4
```

Integers can be manipulated mathematically like you would expect:

```ruby
last_year = 2021 - 1 # => 2020
apples = 2 + 3 # => 5

quotient = 234 / 5 # => 46.8
remainder = 234 % 5 # => 4 (the remainder or modulo)
# (5 * 46) + 4 = 234
```

Because all data types are objects in Ruby, we can use some cool built in functionality.  Some things to try:

1. What is the square root of 36?
2. Is 27 an even integer or an odd integer?
3. How many digits does 1234 contain?

[TRY IT OUT](https://try.ruby-lang.org/)

## Float

Similar to an integer, a [Float](https://ruby-doc.org/core-2.5.0/Float.html) also extends the [Numeric](https://ruby-doc.org/core-2.5.0/Numeric.html) class, but have decimal places for increased precision.

```ruby
airspeed_of_unladend_swallow = 34.2 # km/hr
```

Floats can be mathematically manipulated in the same way as integers.  Some other things to try:

1. How can I get the rounded-down value of 453.676?
2. Is -453.4 positive or negative?
3. How can I reduce 3.14159 to two decimal places? 

## Array

If you've ever been to a chinese buffet, you will undoubtably know that fortune cookies tend to come with *lucky numbers*.  This group of numbers can be represented as an [Array](https://ruby-doc.org/core-3.0.1/Array.html).  An array is an ordered collection of values (which can be any of the data types listed on this page).

```ruby
lucky_numbers = [13, 56, 23, 107, 23]

# Multiple data types are allowed
collection_of_stuff = [53, 'Lord of the Flies', ['another', 'array']]
```
It is important to note that these values are specficially ordered and can be referenced by their `index`.  Arrays in Ruby start at index 0. You may get a value at a certain index in the following ways:

```ruby
# Single Index
first_lucky_number = lucky_numbers[0] # => 13
# Backward Index
last_lucky_number = lucky_numbers[-1] # => 23
## Range
range_of_lucky_numbers = lucky_numbers[0..1] # => [13, 56]
```

Some things to try:

1. How would you return only the *unique* values in our lucky numbers array?
2. How would you sort the lucky numbers from highest to lowest?

[TRY IT OUT](https://try.ruby-lang.org/)


## Hash

Arrays are cool, but it would be nice to *label* values in a collection to make them easier to use.  Enter Hashes. A [Hash](https://ruby-doc.org/core-3.0.1/Hash.html) (aka Dictionary, Hashmap, or Associative Array) is a data structure allowing you to associate *keys* with *values*.

```ruby
image_metadata = {
    # key: value
    width: 1080,
    height: 920,
    name: 'Beautiful Sunset',
    extension: 'jpg'
}
```

In this example we store the image metadata as groupings of `key`-`value` pairs. It is important to also note that we are defining the `keys` as [symbols](#symbol). To access a specific value, we have two options:

```ruby
# as a string reference
width = image_metadata['width'] # => 1080
# or as a symbol reference
width = image_metadata[:width] # => 1080
```

Some things to try:

1.  How can we get an array of the `values` in the above hash?
2.  How could we see if the above hash has a `created_at` key?


[TRY IT OUT](https://try.ruby-lang.org/)

## Symbol

Relatively unique to Ruby is the [Symbol](https://ruby-doc.org/core-2.5.0/Symbol.html).  A symbol is immutable and will remain unchanged during the entire program's execution. They are not *pointers* but rather values themselves and so are more comparable to a string than a variable. You have seen one of their most common use-cases above where they act as keys to an array:

```ruby
# :width is a symbol reference
width = image_metadata[:width] # => 1080
```

A symbol is define with a `:` preceding its name.  In [Classes and Objects](/ClassesAndObjects.md) you will also learn about accessors which are another extremely common application of symbols.

```ruby
class WallE
    attr_accessor :trash_collected
end
```

With what you have learned, see if you can define a new key on the above `image_metadata` hash, and then access that value using symbol reference.

[TRY IT OUT](https://try.ruby-lang.org/)

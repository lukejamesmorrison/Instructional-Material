# Functions

[Back](/README.md)

Functions are the actions of a program. A function in Ruby is comprised of 3 parts:
the keywords (`def`, `end`), the name, and the arguments.  A function *receives* arguments which it will then in some way use for further computation.

## Definition

Ruby is definitely set apart with its generosity when it comes to functions and how they are defined:

#### The Classic
```ruby
def hello_im_a_function(we, are, arguments=2)
    # code
end
```

A nearly universal way of function definition.  The function name is a descriptive string of characters and uses `()` to wrap comma-separated arguments. Almost all modern languages use this form. Note that an argument may have a default value making this argument optional when the function is called:

```ruby
hello_im_a_function(we, are)
```

Note that functions will always automatically `return` the last line of a function definition:

```ruby
def add_values(values)
    trickster = 10

    # This line will be returned as it contains 'value'
    values.sum
end

sum = add_values([1, 2, 3]) # => 6
```

The `return` keyword can still be used, but most Ruby developers embrace the freedom of now needing it.

[TRY IT OUT](https://try.ruby-lang.org/)

#### The Minimalist
```ruby
def hello_im_a_function
    # code
end
```
If your function doesn't require a function, then `()` are not required.  This seems like a perfect application when writing a [Getter](/ClassesAndObjects.md).

[TRY IT OUT](https://try.ruby-lang.org/)

#### The Basher
```ruby
def hello_im_a_function argument
    # code
end
```

Starting to look a little weird, this format is reminiscent of the command line syntax.  The argument is space separated from the function name.  If you are writing Ruby for interaction in the command line, this format helps keep your coding style more homogenous.

[TRY IT OUT](https://try.ruby-lang.org/)

#### The Purist
```ruby
def hello_im_a_function we,are,arguments
```

This format allows multiple arguments to be passed by using comma-separation.  Similar to [The Basher](#the-basher), this format aligns well with the command line.

[TRY IT OUT](https://try.ruby-lang.org/)

You can both define and call all of these formats.

## Calling a Function

A function can be called in a similar way to how it is defined:

```ruby
secret_word = create_secret_word_from_string('super secret')
```

In an [Object](/ClassesAndObjects.md) context, you may access *methods* in the same way as functions but with one minor difference, the method is called *on* the object:

```ruby
require './lib/calculator.rb'

calculator = Calculator.new

# `add()` acts in the same way as a function.
sum = calculator.add(1, 2) # => 3
```

[TRY IT OUT](https://try.ruby-lang.org/)

# Functions
Luke Morrison - 12 May 2021

[Back](/README.md)

Functions are the actions of a program. A function in Ruby is comprised of 3 parts:
the keywords (`def`, `end`), the name, and the arguments.  A function *receives* arguments which it will then in some way use for further computation.

## Definition

Ruby is definitely set apart when it comes to functions and how they are defined.  I will show you all of them, and try to argue for each of their use case:

#### The Classic
```ruby
def hello_im_a_function(we, are, arguments=2)
    # code
end
```
A nearly universal way of function definition.  The function name is a descriptive string of characters and uses `()` to wrap comma-separated arguments. Almost all modern languages use this form. Note that an argument may have a default value making this argument option when called:

```ruby
hello_im_a_function(we, are)
```

#### The Minimalist
```ruby
def hello_im_a_function
    # code
end
```
If your function doesn't require a function, then `()` are not required.  This seems like a perfect application when writing a [Getter](/ClassesAndObjects.md).

#### The Commander
```ruby
def hello_im_a_function argument
    # code
end
```
Starting to look a little weird, this format is reminiscent of the command line syntax.  The argument is space separated from the function name.  If you are writing Ruby for interaction in the command line, this format helps keep your coding style more homogenous.

#### The Purist
```ruby
def hello_im_a_function we,are,arguments
```
Even further towards the command line, this format allows multiple arguments to be passed by using comma-separation.  Similar to [The Commander](#the-commander), this format aligns well with the command line.

You can both define and call all of these formats.

[`TRY IT OUT`][try]


[try]: "https://try.ruby-lang.org/"


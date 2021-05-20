# Regular Expressions

A regular expression (RegEx) is a sequence of characters that specifies a search pattern. Usually such patterns are used by string-searching algorithms for "find" or "find and replace" operations on strings, or for input validation. Regular expressions can be challenging, so head over to [RegExr](https://regexr.com/) and try writting your own! It's an awesome tool for both beginners and experienced developers.

### Match

Let's start simple - imagine that you are signing up to a service and complete a form asking for your `Full Name`. When that for is submitted, the program assigns this value to the `name` variable.

```ruby
name = "Steve Jobs"
```

But wait - how many other users have the same last name?  If we could get *only* the last name, then you could search the database.  Regular Expressions give you the power to select only specific parts of a string:

```ruby
# Capture all characters after and including a non-word character
matches = name.match(/\W(.+)/) # => #<MatchData " Jobs" 1:"Jobs">

# Notice our first capture group at index = 1
last_name = matches[1] # => 'Jobs'
```

[TRY IT ON REGEXR](https://regexr.com/)


### Scan
Ok, now lest see just how many `i`s are in Mississippi:

```ruby
state = "Mississippi"

matches = state.scan(/^[i]/) # => ["i", "i", "i", "i"]
matches.count # => 4
```

[TRY IT ON REGEXR](https://regexr.com/)

### A Practical Example

You have probably inserted your phone number into countless forms throughout your life.  If you think really hard, it's likely that you can think of multiple different formats you have had to satisfy. The image below is a good example.

![phone number input](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRrm1MVsarMK3bxntcvwqqfYiG9HOjmENkt8Q&usqp=CAU)

Let's put on our UX hat - does the user care how their phone number is formatted? Should they? As a seasoned Ruby developer, surely this is a problem **you** can solve for the user and let them focus on enjoying their signup process.  Let's build a regular expression that can *infer* a phone number no matter the format the user chooses.

So what do we know?  A North American phone number has 10 digits (we will exclude the country code for this example). That's all we need. At most, we expect a phone number string can have **5 parts**:

`3 digits + space/character + 3 digits + space/character + 4 digits`

We need to construct a regular expression to select for each of these *parts* and using a matching function to get the digits that we really care about.

```ruby
# First we wish to capture exactly 3 digits.  We will also allow for optional brackets `()`
part_1 = /[\(]?(\d{3})[\)]?/

# Next we will allow for an optional space/character (period or hyphen)
part_2 = /[\s.-]?/ 

# We then capture the second set of 3 digits
part_3 = /(\d{3})/

# And another optional space/character
part_4 = /[\s.-]?/ 

# Finally, we capture our group of 4 digits
part_5 = /(\d{4})/
```

Now, lets throw them together into a single matching expression:

```ruby
match_expression = /[\(]?(\d{3})[\)]?[\s.-]?(\d{3})[\s.-]?(\d{4})/
```

Understandably, this expression is a little intimidating, but as you have seen, regular expressions are a procedural concept and so breaking your problem down into small, linear steps can simplify string matching considerably.

Congratulations, the above regular expression will match the following formats:
- (123) 456-7890
- 123-456-7890
- 123 456 7890
- 1234567890

```ruby
input = "(123) 456-7890"

matches = input.match(/[\(]?(\d{3})[\)]?[\s.-]?(\d{3})[\s.-]?(\d{4})/)
# => {1: '123', 2: '456', 3: '7890'}

phone_number = matches[1] + matches[2] + matches[3] # => '1234567890'

```

Tell the Customer Success team to stand down, no one is struggling with phone number inputs on your watch.

[TRY IT OUT](https://try.ruby-lang.org/)



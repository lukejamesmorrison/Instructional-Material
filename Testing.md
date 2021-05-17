# Testing
Luke Morrison - 14 May 2021

[Back](/README.md)

## The Importance of Testing

On 23 September 1999, NASA lost its $125-million [Mars Climate Orbiter](https://en.wikipedia.org/wiki/Mars_Climate_Orbiter) because spacecraft engineers failed to convert from Imperial to Metric measurements when exchanging vital data before the craft was launched.

![mars climate orbiter](https://upload.wikimedia.org/wikipedia/commons/thumb/1/19/Mars_Climate_Orbiter_2.jpg/260px-Mars_Climate_Orbiter_2.jpg)

A navigation team at the Jet Propulsion Laboratory used the *metric system* of millimeters and meters in its calculations, while Lockheed Martin Astronautics, which designed and built the spacecraft, provided crucial acceleration data in the English *imperial system* of inches, feet and pounds.

As the world becomes increasingly more dependent on software, ensuring that software does as advertised should be the highest of priorities for software developers.

## Enter Test-Driven Development (TDD)

Simply put, TDD is a paradigm of software development where developers first write tests to details how they expect their program to work knowing 100% that they will fail.  It all starts with a failing test.

Once the test has failed, the developer endeavours to write just enough code to pass this test.  At this point, it is safe to say that the piece of software that you are testing is acting as expected.  With a passing test, you are now in an excellent position to refactor and clean up your code.  As long as the test is still green, you know you haven't broken anything.  From here you simply repeat this process until you have built a software package ready for production.

Remember - we can't test for everything, but taking a test-first approach helps us better define our program's API. It also ensures we are able to refactor our codebase without the fear of introducing breaking changes - causing the nerds in Telemetry to lose their minds.

## Testing Ruby

One of the most common testing libraries for Ruby is [RSpec](https://rspec.info/).  With RSpec, we can ensure our Ruby programs are acting as expected.

### A Simple Test

The code below shows a basic rspec test:

```ruby
# spec/satellite_spec.rb
require './lib/satellite.rb'

RSpec.describe "Satellite" do

  it "uses the metric system" do
    satellite = Satellite.new

    expect(satellite.measurement_system).to eq('metric') # => false
    # OR
    expect(satellite.measurement_system == 'metric').to be_truthy # => false
  end


end
```
We first use the `describe` method to define which Class or *unit* we are testing.  In this case, this test suite should test features exclusing to the `Satellite` class.  Next, we can can use the `it()` function to define a new test.  It is important to make your test name descriptive as you may not be the only developer working on this project.

Tests are all about **asserting/expecting** behaviour and state.  RSpec does this with the `expect()` function.  Similar to how we write math equations, we want *left side* to equal *right side*.  In this example, we expect that the satellite's current measurement system is `metric`. We can either test that to value of `measurement_system` is `metric` with our assertion, or we can test that our boolean comparison is `true`.  This is largely left up to the developer so endeavour to make your assertions as simple as possible to not confuse other collaborators.

You can view a list of RSpec expectations on [Github](https://github.com/rspec/rspec-expectations).

### Running your Tests

It is good practice to run your tests every time you make a change to your code.  RSpec makes this very easy.  From within your project directory, run the following command in the console to run all tests:

```bash
rspec
```

Failing tests will display what value was expected versus what was received.  They will also indicate a file, line number and function/method to make your troubleshooting easier.


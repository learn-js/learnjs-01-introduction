# Introduction to testing with tape

We’ll be testing code using [tape](https://github.com/substack/tape).

## tape

tape is a simple, easy to learn testing library for javascript.

### Install tape as a development dependency:
```
npm install tape --save-dev
```

### Example:

Here’s a simple example of using tape to check if two strings are the same:

```
var test = require('tape');

var food = 'pizza';

test('string test', function(t){
  t.plan(1);

  t.equal('pizza', food);
});
```

Let’s step through this example line by line.

In this line we require the tape module, effectively importing its functionality, and assign tape to a variable named test:

```
var test = require('tape');
```

Here we assign the string `’pizza’` to a variable named `food`:

```
var food = 'pizza';
```

This shows usage of the `test` function that we created by requiring the `tape` module:

```
test('string test', function(t){
```
The first argument is an arbitrary string, whatever description you want to explain what you’re testing. The second argument is a callback, which gets the `t` callback that’s used to actually test our code.

In the following line we specify how many things you will test:

```
t.plan(1);
```

Here’s an actual test, where we make sure that the variable `food` is equal to the string `’pizza’`:

```
t.equal('pizza', food);
```

Here we close the callback function with a curly brace, close the call to the test function with a parentheses, and end the statement with a semi-colon:

```
});
```
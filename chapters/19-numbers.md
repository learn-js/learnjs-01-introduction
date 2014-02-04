# Numbers

## Problem

We need a bunch of random numbers to use in a game. They all need to have a different range, so we need to set the minimum and maximum values. We also need to be able to specify if the numbers should be integers or floats.

## How we might solve it

Let's make a module that takes three arguments, the mimimum value, the maximum value, and an optional boolean that if set to `true`, ensures that the function only returns integers.

## Create a module

### Tests

```
var test = require('tape');
var randomizer = require('./');

test('string test', function(t){
  t.plan(2);

  t.ok(randomizer(1, 5) % 1 !== 0);
  t.ok(randomizer(1, 5, true) % 1 === 0);
});
```

### Implement the module

```
module.exports = function(min, max, int){
  var num = Math.random() * (max - min) + min;

  if (int){
    return Math.floor(num)
  }

  return num;
}
```

## Usage

Here's an example that returns a random float between 1 and 5:

```
var randomizer = require('./math');

console.log(randomizer(1, 5));
```

And here's an example that returns a random integer between 1 and 5:

```
var randomizer = require('./math');

console.log(randomizer(1, 5, true));
```
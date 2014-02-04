# Arrays

## Problem

We have a bunch of arrays that need to be put together into one array, then ordered alphabetically.

## How we might solve it

We can use the `.concat()` method to concatenize arrays.

We can use the `.sort()` method to order the arrays alphabetically.

Here's a rough example:

```
var first = ['a', 'd', 'b'];
var second = ['c', 'f', 'e'];

var joined = first.concat(second);

var ordered = joined.sort();

console.log(ordered);
```

Run this, and it should return the following:

```
['a', 'b', 'c', 'd', 'e', 'f']
```

Cool, so that works.

Let's write some tests to make sure everything works as expected, and to explore some possible use cases.


## Create a module

### Tests


```
var test = require('tape');
var concatSort = require('./concat-sort');

/* a helper function to check if two arrays have the same contents */
function arraysEqual(first, second) {
  if(first.length !== second.length) {
    return false;
  }
  
  var firstLength = first.length;
  for (var i = 0; i < firstLength; i++) {
    if(first[i] !== second[i]) {
      return false;
    }   
  }
  return true;
}


test('array test', function(t){
  t.plan(2);

  var firstCheck = [1, 2, 'a', 'b', 'c', 'd'];
  var sorted = concatSort([1, 2, 'c'], ['b', 'a', 'd']);

  t.ok(arraysEqual(firstCheck, sorted));

  var secondCheck = [6, 5, 4, 3, 2, 1];

  function reverser(a, b){
    return b - a;
  }

  var reversedSort = concatSort([2, 6, 3], [1, 4, 5], reverser);
  
  t.ok(arraysEqual(secondCheck, reversedSort));
});
```

When we run the tests using `node test.js`, we'll get an error saying `TypeError: object is not a function` because we haven't defined our concat-sort.js module file yet.

### Implement the module

Create the skeleton of our module in the concat-sort.js file:

```
module.exports = function(){
  
}
```

Run the tests again and you'll see that the two tests are failing. Excellent. Now we can start filling it in based on previous experiments.

We want to be able to concat two arrays, so we need those two arguments.

In the second test we're also passing a callback function that is meant to provide an alternate sort behavior than the default alphanumeric sort.

This can work because the `.sort()` method accepts such a callback function.

Here's the working module:

```
module.exports = function(first, second, sorter){
  return first.concat(second).sort(sorter);
}
```

## Usage

As seen in the tests, the module can be used like this for simple concatenation and alphanumeric sorting:

```
var concatSort = require('./concat-sort');

var sorted = concatSort([1, 2, 'c'], ['b', 'a', 'd']);
console.log(sorted)
```

In this example we want only the strings in the arrays, sorted in reverse order, and everything else should be excluded:

```
var concatSort = require('./concat-sort');

var firstArray = ['food', 'yum', function pizza(){}];
var secondArray = ['pizza', 'yeah', 3333333333];

function onlyStrings(value){
  return (typeof value === 'string') ? value : false;
}

function sorter(a, b){
  return b - a;
}

var sorted = concatSort(firstArray, secondArray, sorter);
var filtered = sorted.filter(onlyStrings)

console.log(filtered);
```
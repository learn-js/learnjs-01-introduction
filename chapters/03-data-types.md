# Part 2: In depth with javascript data types

In this section of the book we'll review strings, numbers, arrays, and objects, and focus on a problem that often comes up with each of them.


# Strings

## Problem

We have a large amount of text that has weird strings in it that need to be replaced.

## How we might solve it

We can use the String.replace() method.

It would be cool if there were a function that accepted a buffer or a string, replaced the characters we want to remove with whatever we want instead, and returned it as either a buffer or a string, depending on what the input was.

That approach assumes that when we are working with buffers, we want the data stay a buffer.

We haven't talked about buffers before in this book. You can learn more about them by [reading the node.js docs about buffers](http://nodejs.org/api/buffer.html).

Buffers are used for dealing with binary data. A likely reason for using buffers: you're reading or writing files using node.js.

## Create a module

Our module will be a single function that takes three arguments:
- the string or buffer that has a substring we want to replace
- a string or regular expression that represents the substring we want to remove
- an optional string that will replace whatever we want to remove

### Tests

Let's write a test that shows how our module might be implemented.

```
var test = require('tape');
var replace = require('./');

var food = 'pizza $$$ awesome';

test('string test', function(t){
  t.plan(1);

  food = replace(food, '$$$', 'is');

  t.equal('pizza is awesome', food);
});
```


### Implement the module

```
module.exports = function(str, remove, replacer){
  var replacer = replacer || '';
  var buffer = false;
  var str = str;

  if (Buffer.isBuffer(str)){
    str = str.toString();
    buffer = true;
  }

  str = str.replace(remove, replacer);

  if (buffer){
    str = new Buffer(str);
  }

  return str;
}
```

## Usage

The test we wrote shows pretty clearly how to use this module, but here's an example of using it with a string:

```
var replace = require('./index');

var messyString = 'this is a WHAT string';

cleanString = replace(messyString, 'WHAT ');
```

Because we made the 3rd argument optional, this will just remove the `'WHAT '` substring to return this:

```
this is a string
```

Here's another example that works with a buffer and uses a regular expression to find the substring that should be removed:

Create a file named example.txt and save it with this text:

```
This is some #we#ird text that has #a bunch# of pound sig#ns mixed in. #wtf.
```


```
var fs = require('fs');
var replace = require('./index');

var file = 'example.txt';

fs.readFile(file, callback(err, content){
  if (err) throw err;

  fs.writeFile(file, replace(content, /#/g));
});
```

We're using this regular expression: `/#/g`.

A regular expression has forward slashes (`/`) at the beginning and end, followed by optional parameters that change the behavior of what the regexp matches. By placing `g` at the end of the regexp our replace statement will find all instances of the pound symbol. Without the `g` only the first instance of the `#` would be matched.

After running `node test.js` in the terminal the file should now look like this:

```
This is some weird text that has a bunch of pound signs mixed in. wtf.
```

Note that this usage with the `fs` module from node.js won't work in the browser, because you won't be able to read or write files from the browser in this way. In the browser you'll typically be working with strings instead of buffers anyway.


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



# Objects

## Problem

We need to iterate through all the properties of an object, excluding any methods on that object.


## How we might solve it

```
var anObject = {
  aString: 'some string value',
  anInteger: 1234,
  aMethod: function(){
    return 'a function that belongs to an object';
  }
}

for (var key in anObject){
  console.log(anObject[key]);
}
```

This gives you an idea of how to iterate through an object using a for...in loop. Note that this will also log the method `aMethod` to the console in a useless and potentially problematic way. This approach works best with objects that do not have methods.

Running the above code will return:

```
some string value
1234
function (){
    return 'a function that belongs to an object';
  }
```

Ouch, returning that function definition in that way is going to mess stuff up.

You can, however, check if the any key on an object references a function using an if statement like this:

```
for (var key in anObject){
  if (typeof anObject[key] !== 'function'){
    console.log(anObject[key]);
  }
}
```

This will return:

```
some string value
1234
```

Nice, now that method on `anObject` isn’t an issue.

## Create a module

Let's create a simple module that we can reuse that will iterate through the properties of an object, but not any methods on an object.

### Tests

```
var test = require('tape');
var eachKey = require('./each-object-key');

var anObject = {
  aString: 'some string value',
  anInteger: 1234,
  aMethod: function(){
    return 'a function that belongs to an object';
  }
}

test('test object keys', function(t){

  // test to make sure aMethod isn't included as one of the keys
  eachKey(anObject, function(key, value){
    t.notEqual(anObject.aMethod, value)
  });

  t.end();
});
```

### Implement the module

Create a file named each-object-key.js, and add the following module code:

```
module.exports = function(obj, callback){
  for (var key in obj){
    if (typeof obj[key] !== 'function'){
      return callback(key, obj[key]);
    }
  }
}
```

## Usage

To use the each-object-key module, do the following:

```
var eachKey = require('each-object-key');

var anObject = {
  aString: 'some string value',
  anInteger: 1234,
  aMethod: function(){
    return 'a function that belongs to an object';
  }
}

eachKey(anObject, function(key, value){
  console.log(key, value)
});


# Javascript strings cheatsheet

## String methods
Here are a collection of common and useful string methods that exist in Javascript.

### .charAt()
Returns the character of a string at a specific index.

#### Usage example

```
var someString = 'pizza';

someString.charAt(1)
// returns: 'i'
```

### .concat()
Join two or more strings together, and it returns a copy of the combined strings.

#### Usage example

```
var someString = 'pizza';
var anotherString = ' is awesome!';

someString.concat(anotherString);
// returns: 'pizza is awesome!'
```

### .indexOf()
Find a string in another string, and it returns the index position of its first occurrence.

#### Usage example

```
var someString = 'pizza';

someString.indexOf('a');
// returns: 4
```

### .lastIndexOf()
Find a string in another string, and it returns the index position of its last occurrence.


#### Usage example

```
var someString = 'pizza';

someString.lastIndexOf('z');
// returns: 3
```

### .match()
Returns an array of all matches of a regular expression in a string.

#### Usage example

```
var someString = 'pizza is awesome and soda is awesome.';

someString.match(/is/g);
// returns: ['is', 'is']
```

### .replace()
Find and replace a substring in a string with a new substring. You can use a regular expression in place of a substring for the first argument. 

#### Usage example

```
var someString = 'pizza is awesome';

someString.replace(/awesome/, 'delicious');
// returns: 'pizza is delicious'
```

### .search()
Very similar to .indexOf(), only it takes a regular expression as the argument, and returns the index of the substring's position in the string.

#### Usage example

```
var someString = 'pizza is awesome';

someString.search(/is/);
// returns: 6
```

### .slice()
Specify start and end index positions, and .slice() will return the part of the string that exists within the start and end points.

#### Usage example

```
var someString = 'pizza is awesome and soda is awesome';

someString.slice(0, 5)
// returns: 'pizza'
```

### .split()
Create an array from a string, split by using a separator you define.

#### Usage example

```
var someString = 'pizza is awesome';

someString.split(' ');
// returns: ['pizza', 'is', 'awesome']
```

### .substr()
Extracts characters from a string, beginning at a specified index and through the specified number of characters.

#### Usage example

```
var someString = 'pizza is awesome';

someString.subst(0,5)
// returns: 'pizza'
```

### .substring()
Specify two index positions, and .substring() will return the characters between those two indexes.

#### Usage example

```
var someString = 'pizza is awesome';;

someString.substring(9,16)
// returns: 'awesome'
```

### .toLowerCase()
Convert a string of any case to all lowercase.

#### Usage example

```
var someString = 'PIZZA IS AWESOME';

someString.toLowerCase();
// returns: 'pizza is awesome'
```

### .toUpperCase()
Converts a string to uppercase letters

#### Usage example

```
var someString = 'pizza is awesome';

someString.toUpperCase();
// returns: 'PIZZA IS AWESOME'
```

### .trim()
Use .trim() to remove extra white space from both ends of a string.

#### Usage example

```
var someString = '  pizza is awesome ';

someString.trim();
// returns: 'pizza is awesome'
```

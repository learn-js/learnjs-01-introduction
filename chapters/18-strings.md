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
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
```
# Control flow: making decisions in code

> How do I control the flow of a program?

There are a few basic approaches for controlling the flow of a javascript program.

### "if" statements

An if statement looks like this:

```
if (something === true){
  /* do something */
}
```

An extended example might look like this:

```
if (hungerLevel > 10) {
  eat(food).fast();
} else if (hungerLevel > 5) {
  prepare(food).leisurely():
} else {
  do(somethingElse);
}
```

Note that you can use `else if` to check follow-up values, and that you can use `else` for any other case, as a kind of fallback.

## Loops

### "while" loops

```
var i = 0;

while (i < 10){
  console.log(i);
  i = i + 1;
}
```

### "for" loops

Any time you want a program to do something a specific number of times, or you want to perform an action on every item in an array or object, you'll likely end up using a loop.

### "for" loops
A for loop

A simple for loop looks like this:

```
for (var i = 0; var i < 10; i++){
  console.log(i);
}
```


You can use this to loop through items in an array like this:

```
var alpha = ['a', 'b', 'c'];
var alphaLength = alpha.length;
for (var i = 0; i < alphaLength; i++){
  console.log(alpha[i]);
}
```

Run this in your javascript console and you’ll see the items in the array being logged to the console one at a time.

There’s an alternate way to iterate through arrays that is somewhat supported in browsers, and is fully supported in Node, the `.forEach` method.

Here’s an example:

```
var alpha = [‘a’, ‘b’, ‘c’];
alpha.forEach(function(item, i, array){
  console.log(item);
});
```

The forEach method takes a callback function that executes once for every item in the array.

### The "for ... in" loop

The forEach method works great for arrays, but for objects I typically use the "for ... in" loop.

```
var foods = {
  pizza: ['cheese', 'dough', 'sauce'],
  taco: ['tortilla', 'cheese', 'hot sauce']
}

for (var type in foods) {
  console.log (type + ': ' + foods[type]);
}
```
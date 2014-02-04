# Operators & arithmetic

## How do I check if something is equal, not equal, less than or greater than?

### Equals:

```
===
```

Examples:

```
true === false
// returns false

'pizza' === 'pizza'
// returns true

123 === '123'
// returns false
```

You may have noticed there are three equals signs. If you’ve tried out other programming languages, you’ll probably remember that two equals signs were used to check equality, like this: `something == otherThing`.

That works in javascript, too, but there’s a difference in the behavior of `==` and `===`.

When using `==`, the types of your values will be coerced into being the same.

Open your javascript console and type this in:

```
‘123’ == 123
```
This will return true, because the `==` operator is coercing the values to be the same type.

Now try this one out in the javascript console:

```
‘123’ === 123
```

This returns false, because when using the `===` operator it checks to make sure the two values are of the same type, and if not, returns false. If the two values are the same type, then it’ll do the usual equality check.

For this reason it is a good idea to use `===` rather than `==` in most situations.

### Does not equal: 
```
!==
```

Examples:

```
'pizza' !== 'gross'
// returns true
```

Like the `===` operator, `!==` has a counterpart that coerces the type of values, `!=`.

```
123 !== '123'
// returns true
```

Greater than and less than:
```
>
<
```

Examples:

```
1 < 3
// returns true

'pizza'.length > 'poop'.length
// returns true
```

With this example: `'pizza'.length > 'poop'.length`, the `.length` method returns how many characters are in the string, so it’s really evaluating those numbers: `5 > 4`.

Greater than or equal to, less than or equal to:
```
>=
<=
```

Examples:

```
i = 0;
i <= 10;
// returns true

[1, 2, 3].length >= [4, 3, 2, 1].length
// returns false
```

Like the example above, using the .length property on an array returns the number of items in the array, so a statement like this:

```
[1, 2, 3].length >= [4, 3, 2, 1].length
```

Is really being evaluated like this:

```
3 >= 4
```

## How do I group equality statements?
With logical operators `&&` and `||`.

By using `&&`, you're saying that all of the comparison checks must return true.

By using `||`, you're saying that at least one of the comparison checks must return true.

Examples:

```
true && false
// returns false

3 < 10 && 'pizza'.length > 3
// returns true

false || true
// returns true
```


You can also alter the boolean value that's returned from a variable by using `!`. Any time you put `!` it'll return the opposite of its actual boolean value. 

Examples:

```
!true
// returns false

!false
// returns true

var pizza = null;
!pizza
// returns true
```

It's like saying "NOT false", or "NOT true".

## How do I do math?

### Add:
```
+
```

Examples:

```
3 + 5
// returns 8

'abc' + 'def'
// returns 'abcdef'
```

Wait, those strings just glomped together!

The `+` operator will add two numbers together, and it will also concatenate two strings, meaning that the two strings will be combined into one.

For fun, you should open the javascript console and experiment with using the `+` operator with arrays. The results of operations like this one are messy and unexpected:
```
['a', ['b', 3]] + [1, 2, 3, 'a', 'b', 'c']
```

The `+` operator is the only arithmetic operator that has this multipurpose behavior, so you won’t be able to subtract, multiply, or divide strings with the relative operators.

### Subtract:
```
-
```

Examples:

```
5 - 3
// returns 2

1 - .1
// returns .9
```

Note that any time an operator is used with a mix of integer and float numbers, the result will typically be a float.


### Multiply:
```
*
```

Examples:

```
var x = 5;
x * 10;
// returns 50

var pizzasIWantToEat = 23;
var percentageIWillActuallyEat = .033;
pizzasIWantToEat * percentageIWillActuallyEat;
// returns 0.759
```


### Divide:
```
/
```

Examples:

```
6 / 2
// returns 3

var i = 21
i / 3
// returns 7
```


### Remainder:

```
%
```

You can check to see if there’s a remainder from division really easily by using the remainder operator.

Examples:

```
12 % 4
// returns 0

3 % 2
// returns 1
```

This is really useful for doing things like checking to see if a number is even or odd.


## Parentheses 

Just like in the math you learned in school, you can use parentheses to group operations.

Examples:

```
(3 + 3) * (21 / 7)
// returns 18

3 + 3 * 21 / 7
// returns 12
```

### The Math object

A great resource for learning more about javascript's Math object is the [Mozilla Developer Network's javascript documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math).

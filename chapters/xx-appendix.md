# Appendix

# Additional resources

## interactive terminal tutorials:
You should definitely visit [nodeschool.io](http://nodeschool.io). It features tutorials that are almost like adventure games, except for learning programming:

- [Learn You The Node.js For Much Win!](https://github.com/rvagg/learnyounode) An intro to Node.js via a set of self-guided workshops.
- [Stream Adventure](https://github.com/substack/stream-adventure). Learn about streams in node.js
- [Level Me Up Scotty!](https://github.com/rvagg/levelmeup) Learn about using leveldb with node.js

### Online interactive tutorials:
- [codecademy.com](http://codecademy.com)
- [Kahn Academy Computer Science](https://www.khanacademy.org/cs)

## javascript books:
- [js for cats](https://github.com/maxogden/javascript-for-cats)
- [eloquent javascript](http://eloquentjavascript.net/)
- [learning javascript design patterns](http://www.addyosmani.com/resources/essentialjsdesignpatterns/book/)
- [writing modular javascript](http://addyosmani.com/writing-modular-js/)
- [jquery fundamentals](http://jqfundamentals.com/)
- [javascript enlightenment](http://www.javascriptenlightenment.com/JavaScript_Enlightenment.pdf)

## node.js books:
- [art of node](https://github.com/maxogden/art-of-node)
- [stream handbook](https://github.com/substack/stream-handbook)
- [node beginner book](http://www.nodebeginner.org/)

## html/js/dom books:
- [dive into html5](http://diveintohtml5.info/)
- [dom enlightenmnet](http://domenlightenment.com/)

## Style guides:
- [idiomatic js](https://github.com/rwldrn/idiomatic.js)
- [idiomatic html](https://github.com/necolas/idiomatic-html)
- [idiomatic css](https://github.com/necolas/idiomatic-css)
- [airbnb js style guide](https://github.com/airbnb/javascript)
- [felixge node style guide](https://github.com/felixge/node-style-guide)
- [jQuery's javascript style guide](http://contribute.jquery.org/style-guide/js/)

**[Mozilla Documentation](https://developer.mozilla.org/en-US/)**  
Have a question about some css property or html element? The Mozilla Developer Network has awesome documentation. If you're searching on google.com for anything css/html/js related, add the abbreviation "mdn" to your search query to see results from Mozilla Documentation. This site also has a bunch of introductory tutorials that are really useful.

**[WebPlatform.org](http://www.webplatform.org/)**  
This is a newer resource, but a good one. It's got a great design and well-organized resources.

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

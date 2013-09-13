# Enter the wild and wondrous land of javascripting.
To control a computer with code can feel like wielding a weird and mighty magic. It can seem intangible and unfamiliar, but it’s important to know that code is real and learnable. 

Magic in popular culture typically belongs to those who are born with the power.

The magic of programming belongs to those who practice.

See what some old wizards (Gerald Jay Sussman and Hal Abelson) had to say about the similarities between programming and sorcery in a book called _Structure and Interpretation of Computer Programs_:

```
A computational process is indeed much like a sorcerer's idea of a spirit. It cannot be seen or touched. It is not composed of matter at all. However, it is very real. It can perform intellectual work. It can answer questions. It can affect the world by disbursing money at a bank or by controlling a robot arm in a factory. The programs we use to conjure processes are like a sorcerer's spells. They are carefully composed from symbolic expressions in arcane and esoteric _programming languages_ that prescribe the tasks we want our processes to perform.
```

Let’s be sorcerers. _Open source_rers. Let's write some weird little programs, and, as they say in SICP,  “conjure the spirits of the computer with our spells.”


## Overview of the future
This book isn’t just a book.

Many of the exercises in this book can also be completed through an interactive tutorial that runs in your terminal.

Go to [github.com/learn-js/01-introduction](github.com/learn-js/01-introduction) to install and get started with the interactive tutorial.

This book is the first in a series about building projects with javascript. If you haven’t already you should sign up for updates by [subscribing to the Super Big Tree newsletter](http://eepurl.com/rN5Nv).


## Thank you.
I really appreciate the support you’ve given by purchasing this book.
I welcome you to help guide the direction of this book and the Learn.js series of javascript books. If there are particular libraries, development tools, or programming patterns that you'd like to see covered, please email me at [hi@learnjs.io](mailto:hi@learnjs.io).

The Learn.js series is highly inspired by the lean publishing model ([read more about it](https://leanpub.com/manifesto)) proposed by Peter Armstrong, founder of leanpub.com. It has proven successful as a way to receive feedback from you, the readers, so that together we can make the best book about javascript tools and libraries possible.

You’ll get updates about upcoming books in the series, and I’d love to hear your thoughts on what would be most useful.


## Setting up a development environment
There’s a lot of wind-up to getting started programming. You should understand things like git, github, the terminal, and more.

Instead of baking that information into each book in the series, I created a book called Development Environments for Beginners that helps you set up a javascript development environment (as well as ruby and python, but you can skip those sections if needed).

From that book you’ll learn how to install node.js, work with version control and testing tools, best practices for automating tasks and other programming tips and tricks.

If you’re feeling like you could use more information about what a development environment is and how best to set one up, you can purchase the Development Environments book at [superbigtree.com/books/dev-envs](http://superbigtree.com/books/dev-envs).

If needed you can check out the Development Environments book on GitHub for free here: [github.com/sethvincent/dev-envs](http://github.com/sethvincent/dev-envs).

Though, if you’re feeling generous and able to purchase the book, that’ll get you pdf, epub, and mobi versions, as well as support my work.





## node style
We will write in the style of node.js.

Even our code written for the browser will utilize the node.js style of modules thanks to browserify, a tool for bundling node modules for the browser.

This means that we won’t cover the RequireJS/AMD toolset for javascript development, but will focus on node/CommonJS modules.

You’ll learn more about this later in the book as we go into depth with browserify and node modules.

But for now, know that this book will be applicable to pretty much any javascript you write, and will provide additional resources for writing in the style of node.js.



## Who are you? Who am I? What is this?

### The book
This book is an introductory text. You likely got that from the title. I aim for this book to be a conversational and low-barrier approach to learning javascript. Everything we work on in this book can be done with just a browser, a terminal, and a text editor.

The book covers introductory node.js, and writing client-side code using node modules and browserify.

It’s meant as an introductory text that will get people up to speed for following books in the Learn.js series.

### The reader
I expect that the ideal reader for this book is someone who likes exploring, imagining, and inventing for themselves. You might even have some experience with javascript already. And that’s OK, because practicing, and even repetition is an important part of learning.

### The author
I’m Seth Vincent. I write code, stories, and music. 

I’m an independent programmer, designer and writer that is passionate about news, publishing and civic technology – particularly as it applies to local issues.

I’m a co-organizer of [seattle.io](http://seattle.io), [Code for Seattle](http://codeforseattle.org/), and [SeattleWiki](http://seattlewiki.net/). 

In case you couldn’t tell, I currently live in Seattle, Washington.

I write books like the one you’re reading, and build things like [crtrdg.js, a toolkit for 2d games](http://crtrdg.github.io/) at [Super Big Tree](http://superbigtree.com/).



## Keep coding
You're at a computer and your hands are sweaty. You have a text editor open and you're reading dense, arcane instructions.

You're about to write javascript for the first time.

It’s difficult, and it doesn’t make sense at first. This is normal.

You’re going to make mistakes.  There’s a trick for dealing with that problem. A trick that works really well.

The trick is to be OK with making mistakes.

Accept that you’re going to fail really hard at first.

I couldn’t ride a bike until I was embarrassingly old – in middle school. All my friends were riding bikes, and I couldn’t keep up with them unless I was on a bike. That motivated me to learn. To be a competent bike rider I had to ignore the moments when I ran into parked cars and fell over.

I had to really want it.

You will forget commas, or type semi-colons instead pf colons, or type something with a capital letter that’s supposed to be all lowercase.

You will run a program and spend agonizing minutes wondering why it spits errors, then realize you haven’t downloaded the needed dependencies.

You’re going to fuck up.

But that’s OK, because you’re OK with fucking up.

This book is meant to help guide you past common fuck-ups, but the book won’t solve all your problems for you. 

Your mastery of programming relies on how motivated you are to learn, and how diligent you are in solving frustrating errors.

Keep coding.




# THE BASICS

## In this section, we'll get started learning:

### Chrome's Developer Tools
All browsers include tools for evaluating, debugging, and auditing your code and your site's performance. This section will introduce you to the tools offered in the browser Chrome, and later in the book we'll go into these tools in more detail.

### Basic html and css
For many of our projects in this book, html and css will be kept as minimal as possible. This refresher will get you up to speed if you haven't worked with css or html much before.

### Javascript syntax, variables, data types, and functions
Here we'll go over the basic parts of javascript. We'll cover the equivalents of a programming language's grammar and punctuation, as well as the basic building blocks of javascript: strings, numbers, booleans, arrays, objects, and functions.

### Node.js and npm
Server side javascript is a seriously awesome thing, and while this book will only give an introductory look at what's possible, we'll be using many command line tools based on node.js that are installable using `npm`, node's package manager.

### Testing javascript
Writing tests for your code does two things: ensure your code works as expected when changes are made, and provides examples of usage of your project. When applicable we'll write the tests for a project first, before writing the code that does the real work, and we'll describe later why this is a useful workflow.



# Chrome Developer Tools
 Hello, javascript. It's nice to meet you.

```
console.log('hello, javascript. it's nice to meet you');
```

Open up the browser Chrome.

> If you don't already have Chrome installed, download and install it now at [google.com/chrome](http://google.com/chrome)

Now, use this keyboard shortcut on a Mac: command + option + j
Or this for Windows/Linux: control + shift + j

You just opened the javascript console.

**Type in this code:**

```
console.log('what is this?');
```

You just told the javascript console to print some text!

Any time you put `console.log()` in javascript code that executes in the browser, whatever you put between the parentheses will show up in your browser's javascript console.

As you learn javascript, the browser console and `console.log()` will be good buddies as you prototype new functionality and debug your code.

## Your first challenge:

Type this into the console:

```
console.error('this is an error');
```

That's an error! Note how it shows up in red. Look in the bottom right corner of the browser. You'll see a little red circle with an x in the middle, and a number on its right side. That's a helpful little indicator of errors in your javascript, and any time something is wonky with your code that red circle will show up.

With most errors you'll also be able to see a line number from your javascript file, which will help you pinpoint the offending code. We'll get into errors and debugging in more detail later in the book.

## More developer tools
The javascript console is just one of the tools available for web development inside of Chrome. For this book we will focus on using Chrome and its developer tools for two reasons: Chrome has a a set of versatile and powerful tools, and focusing on the tools of one browser helps keep the instructions simple.

Check out the [Chrome Developer Tools documentation](https://developers.google.com/chrome-developer-tools/) to learn more about all that Chrome has to offer for developers working with javascript, html, and css.

You should also familiarize yourself with the developer tools in Firefox. Check out the [Mozilla Developer Network documentation for the Firefox developer tools](https://developer.mozilla.org/en-US/docs/Tools).

## Recap! We learned that:
- the javascript console and learned that we can type in javascript!
- we can use code like `console.log()` and `console.error()` to print information to the console.
- Chrome has a lot of useful tools, and later in the book we'll learn how they can help with experimenting with code, auditing the performance of our site, investigating the information sent between the browser and the server, and more.

# HTML & CSS: an introduction

If you're new to building projects for the web, knowing javascript alone won't be enough.

This book focuses on javascript, but you'll certainly pick up some html and css along the way.

You might find it useful to learn about html and css before reading Learn.js, or to have a resource handy that you can refer to when introduced to new html elements or css properties.

## But here's a quick refresher to get you started:

An example of an html element:

```
<h1>This is a headline</h1>
```

That's an `h1` element. It is used for the most prominent headline of a document – often the site title or article title. Note that this element has an opening tag, `<h1>, and a closing tag, `</h1`>, which looks the same except it has a forward slash, `/`.

This is a common pattern for html elements. There are a few html elements that don't require closing tags. Like these:

```
<br>
```

The `br` element creates a line break in text.

```
<hr>
```

The `hr` element creates a horizontal rule, a straight line, across your web site. Usually used as a break between sections.

```
<img src="image.jpg" alt="this is the alt text of an image" />
```

The `img` element is a little unique. Note that it has a `src` attribute that specifies the image we want to have show up, and an `alt` attribute that provides text that will be displayed for screen readers, or that might be used as a caption. The `img` element is also a self-closing tag, meaning it has a forward-slash before the closing angle bracket.

## HTML attributes and CSS selectors.
We just saw the `src` and `alt` attributes on the `img` element. There are many attributes that can be used on any given html element. Some attributes control behavior of the element, some are used as selectors for css rules.

**Here are the two attributes most used as selectors in css rules:**

### `id`

Using the `id` attribute of an html tag looks like this:

```
<p id="introduction">This is the first paragraph of a story.</p>
```

Here we're marking a paragraph (a `p` element) as being the introduction. The `id` of `introduction` should only be used on one html element, making this one `p` element special.

We do this so that later, in the css, we can give the `introduction` different styling than the rest of the `p` elements on the page.

Here's some css that makes the `introduction` italic:

```
p#introduction {
  font-style: italic;
}
```

We don't have to include the `p` in `p#introduction`, but it's useful for clarity. Note the hash mark: `#`. `id` attributes are identified in css by using a `#`.

### `class`
Now, let's say that we want some of the paragraphs in our story to have a different background color to highlight them. One way of accomplishing this would be to add a `class` to these paragraphs.

The use of `class` attributes looks like this:

```
<p class="highlight">This paragraph will be bold and slightly bigger.</p>
```

We've given this `p` element a class of `highlight`, so let's add some css that gives this paragraph a yellow background.

```
p.highlight {
  background-color: yellow;
}
```

One of the differences between `id` and `class` attributes, is that a `class` can be given to multiple elements on a page, whereas an `id` should be unique to one element. So we can give this class to multiple paragraphs to make them highlighted.

### Where does the css go?
There are two options: include separate css files, or place css directly in your html file. In almost all situations, including a separate css file for your styles will be a faster and more organized option.

Here's what it looks like to embed css in your html file.

```
<!DOCTYPE html>
<html>
<head>

  <title>Your website</title>

  <style>

    p.highlight {
      background-color: yellow;
    }

  </style>

</head>
<body>

</body>
</html>
```

You'll add your css between the opening and closing `style` tags, which should in turn go between the opening and closing tags of the `head` element.

But the cleaner option is to create a separate css file that you reference from your html file:

```
<!DOCTYPE html>
<html>
<head>

  <title>Your website</title>

  <link rel="stylesheet" href="style.css" />

</head>
<body>

</body>
</html>
```

This tells the browser to load the css from the `styles.css` file. Having a separate file for your styles helps with keeping your site easy to maintain. Having everything in one big html file can be a pain to work on.

### So where will the javascript be in an html file?

Just as with css, there are a couple options for where you place your javascript code.

You can embed it in your html file between opening and closing `script` tags:

```
<!DOCTYPE html>
<html>
<head>

  <title>Your website</title>

</head>
<body>

<script>
console.log('this is javascript');
</script>

</body>
</html>
```

Or you can use a `script` tag to reference an external javascript file:

```
<!DOCTYPE html>
<html>
<head>

  <title>Your website</title>

</head>
<body>

<script src="site.js"></script>

</body>
</html>
```

Note that the `script` element needs a closing tag even though there's nothing between the opening tag and closing tag.

Just like with css, it's better to keep your javascript in a separate files. By separating the types of code in your project you make it easier for yourself and for others to figure out how to make changes. The more organized your project is, the quicker you can revise its design and functionality.

### Layout with html and css
There are a few common tags used for laying out an html document. Check out this example:

```
<!DOCTYPE html>
<html>
<head>

<title>Your website</title>

</head>
<body>

<header>
    <h1>Your website</h1>
</header>

<main role="main">
  <p>This is the content of your website</p>
</main>

<footer>
  <p>Contact: your info.</p>
</footer>

</body>
</html>
```

We're using the `header` element for the header of the page, the `main` element for the content of the page, and the `footer` element for supplementary information that goes in the footer. All three of these tags are relatively new as part of html5. Another new tag is 'section'. You might use it to break up your main content into parts:

```
<main role="main">
  <section id="part-one">
    <h1>Section one</h1>
    <p>This is the content of the first section</p>
  </section>

  <section id="part-two">
    <h1>Section two</h1>
    <p>This is the content of the second section</p>
  </section>
</main>
```

The `section` element is for breaking up your web page into distinct sections. Note that I've got `h1` tags in each of the sections as headers. In html5 anytime you create a new `section` you're allowed to start a new heirarchy of header tags.

Where `section` elements are for specifying blocks of content on your page in a semantic way, 'div' elements are used primarily for the positioning and alignment of your content. For example, you might want to use a `div` to act as a container that restricts the width of your content:

```
<section id="part-one">
  <div class="container">
    <h1>Section one</h1>
    <p>This is the content of the first section</p>
  </div>
</section>
```

With css like below you can have the `section` tag the full width of the page while the container stays centered at 800 pixels.

```
.container {
  width: 800px;
  margin: 0px auto 0px auto;
}
```

The `div` is centered by using `auto` for the left and right margins (the order goes top, right, bottom, left).

### More resources
This gives you an intro to some of the html and css concepts we'll use most often in the book. 

#### To learn html and css in more depth, check out these resources:
**[Don't Fear The Internet](http://www.dontfeartheinternet.com/)**  
This is a wonderful introduction to html and css. Watch, enjoy, and follow along.

**[Web fundamentals track at codecademy.com](http://www.codecademy.com/tracks/web)**  
After you've had your fears eased by Don't Fear The Internet, check out the codecademy.com web fundamentals course. It'll get you some nitty gritty experience with the basics.

**[Mozilla Documentation](https://developer.mozilla.org/en-US/)**  
Have a question about some css property or html element? The Mozilla Developer Network has awesome documentation. If you're searching on google.com for anything css/html/js related, add the abbreviation "mdn" to your search query to see results from Mozilla Documentation. This site also has a bunch of introductory tutorials that are really useful.

**[WebPlatform.org](http://www.webplatform.org/)**  
This is a newer resource, but a good one. It's got a great design and well-organized resources.



## Variables

### Creating a variable:

```
var nameOfVariable;
```

> Variables are camelCase, meaning first letter is lowercase, and if the variable is made of multiple words, the first letter of following words are capitalized.

### Creating a variable that references a string:

```
var thisIsAString = 'this is a string';
```

Surround strings with single quotes.

### Creating a variable that references a number:

```
var thisIsANumber = 3.14;
```

Numbers do not have quotes around them.

### Creating a variable that references an array:

```
var thisIsAnArray = [1, "two", [3, 4]];
```

Note that one of the values in the array is a number, one is a string, and another is an array. Arrays can hold any value in any order.

### Accessing the values in an array:

```
thisIsAnArray[0];
```

The above will return the number `1`. Arrays use numbers as the index of their values, and with javascript an array's index always start at `0`, making `0` reference the first value of the array.

```
thisIsAnArray[1];
```

This returns the string 'two';

#### How would you return the number `4` from the nested array?

Like this:

```
thisIsAnArray[2][1];
```

### Creating a variable that references an object:

var thisIsAnObject = {
  someString: 'some string value',
  someNumber: 1234,
  someFunction: function(){
    return 'a function that belongs to an object';
  }
};

Here we're setting `someString` to `'some string value'`, `someNumber' to `1234`, and we're creating a function named `someFunction` that returns the string `'a function that belongs to an object'`. So how do we access these values?

To get the value of `someString` using dot notation:

```
thisIsAnObject.someString;
```

Or using bracket notation:

```
thisIsAnObject['someString'];
```

To get the value of `someNumber` using dot notation:

```
thisIsAnObject.someNumber;
```

Or using bracket notation:

```
thisIsAnObject['someNumber'];
```

To use the function `someFunction` using dot notation:

```
thisIsAnObject.someFunction();
```

Or using bracket notation:

```
thisIsAnObject['someFunction']();
```

Using square bracket notations with functions looks a little wacky. It will be useful if you are storing function names in variables as strings, and need to use the variable to call the function being stored. Otherwise, stick with dot notation.
That goes for other attributes on an object, too: stick with dot notation unless there's a good reason to use bracket notation.

For instance, it's more clear to use bracket notation in a situation like this:

```
for (var key in thisIsAnObject){
  console.log(thisIsAnObject[key]);
}
```

This gives you an idea of how to iterate through an object using a for...in loop. Note that this will also log the method `someFunction` to the console in a useless and potentially problematic way. This approach works best with objects that do not have methods.

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
for (var key in thisIsAnObject){
  if (typeof thisIsAnObject[key] !== 'function'){
    console.log(thisIsAnObject[key]);
  }
}
```

This will return:

```
some string value
1234
```

Nice, now that method on `thisIsAnObject` isn’t an issue.



# Functions

## Eating, digesting, and pooping.

A function is a block of code that takes input, processes that input, and then produces output.

You can think of it like eating, digesting, and pooping.

And when we use a number of functions in succession, it's almost like that movie [The Human Centipede](http://www.imdb.com/title/tt1467304/), only less gross.

## Let's make a function named `eat`.

```
// take input / eat food
function eat(food){

  // process the input / digest the food
  var poop = digest(food);

  // send output / poop
  return poop;
}
```

The above example should make sense just from reading it.

Note that lines that start with `//` are comments, and they get ignored when the code is executed.

To create a function, we first write `function`. Next, we can name the function, and in this case it is named `eat`.

Inside of the parentheses we specify the input, which are also called arguments. We only have one argument in this case, named `food`.

Next, we use an opening curly bracket to indicate the beginning of the block of code connected with this function.

We create a variable named `poop`, which contains a "digested" form of the `food` argument. Here we're using another function named `digest` that is using the `food` argument as its own input. 

Finally, we `return poop;` so that the output of this function can be used in other parts of our code.

## Using the `eat` function:

We can use the `eat` function like this:

```
eat('pizza');
```

When we run this, it'll return something like `zpzia`, `apizz`, or `pzazi`.
You know, something random like that.

### So what is the `digest` function doing?

You've probably already guessed that it is a function that randomly shuffles letters in a string. In actual production projects you would want to name it something a little more clear, like`shuffleLetters()`.

Here's an example of the `shuffleLetters()` function using our food/poop language:

```
function digest(food){
  var food = food.split('')
  var digesting = food.length, digested, randomFoodPart;

  while (digesting) {

    randomFoodPart = Math.floor(Math.random() * digesting--);

    digested = food[digesting];

    food[digesting] = food[randomFoodPart];

    food[randomFoodPart] = digested;
  }

  var poop = food.join('');

  return poop;
}
```

_Adapted from [Mike Bostocks's Fischer-Yates Shuffle](http://bost.ocks.org/mike/shuffle)._

You're probably aware that the `digest` function is doing the heavy lifting, while the `eat` function is just a wrapper around `digest`.

If you were really modeling eating, digesting, and pooping using javascript functions, how would you do it?



# Introduction to callbacks.

A callback is a function that you pass as an argument to another function.
Typically, you'll use a callback as a way to work with data after it's been processed by a function.

A simple callback looks like this:

```
function holla(callback){
  callback();
}
```

Note how we're setting up an argument named `callback`, then calling that argument as a function: `callback()`.

Usage if the `holla` function:

```
holla(function(){
  console.log('this is part of the callback function);
});
```

Our function named `holla()` takes one argument, and we expect it to be a function. In this example we're using an anonymous function, but we could use a named function like this:

```
function holla(callback){
  callback();
}

function back(){
  console.log('this is part of the callback function);
}

holla(back);
```

But usually we're providing a function some kind of parameter,  that function performs an action on the parameter, then we use the callback to work with the output of the function we called. A simple example looks like this:

```
// create an eat function
function eat(food, callback){
  var food = food + " was eaten";
  callback(food);
}

// create a poop function to use as the callback
function poop(output){
  console.log(output);
}

// call the eat function, passing a food and the poop function as arguments
eat("pizza", poop);
```

Note that when we pass the callback function `poop` as an argument we don't write it like `poop()`. This would _call_ or execute the function, and we don't want that to happen when we pass the `poop` function as an argumet. The `poop` function gets called later inside the `eat` function.









# Introduction to node.

Node.js is server-side javascript. It is well-suited to real-time applications and systems that are heavy on input and output. You can use it to create web servers, to manage information in databases, to build real-time communication tools, and more.

## In this book, we'll use node in these ways:
- Install command line tools available through node's package manager, `npm`.
- Create basic web servers to serve static content to our web browser.
- Experiment with real-time, multi-user applications.

## To learn node in detail, read these resources in this order:
- [art of node](https://github.com/maxogden/art-of-node)
- [streams handbook](https://github.com/substack/stream-handbook)

## Install node:

There are a few options for this, and I've put them in my order of preference:

### Use nvm to manage node versions.
This option gives you the most control, allows you to switch between versions of node similar to using rvm or rbenv for Ruby. [Get nvm here](https://github.com/creationix/nvm). This is the method I use, and the one I recommend.

### Install using a package manager. 
This is a good option, but sometimes package managers can be out of date. If the node version you'll be using matters for your project, you should make sure that the version in the package manager works for you. [Check out a list of package manager instructions here](https://github.com/joyent/node/wiki/Installing-Node.js-via-package-manager).

### Download an installer from nodejs.org.
[Here's the node.js download page](nodejs.org/download).

Installing node gives us the node package manager `npm`. We'll use it to install a wide range of packages, including web frameworks, game dev libraries, and client-side javascript modules. 

> This section of the book is still a work in progress. Make suggestions at [github.com/learn-js/learnjs/issues](http://github.com/learn-js/learnjs/issues).

# Introduction to npm

You use `npm` to install javascript modules. It is most often used for installing node.js modules, but it is not limited to server side code.

You might expect `npm` to stand for Node Package Manager. But that's misleading – it reinforces the idea that `npm` is just for node.js projects.

Instead, we can follow the guidance of javascript developer Max Ogden and let is stand for Node Packaged Modules.

Read more about this idea on his blog post: [maxogden.com/node-packaged-modules.html](http://maxogden.com/node-packaged-modules.html), where he presents three projects based on the tool `browserify`. We'll make heavy use of browserify in the book.

## Getting started with `npm`
If you've alreadt installed node.js, you've got npm.

Check the version of `npm` like this:

```
npm -v
```

This should return something like:

```
1.2.32
```

The exact version numbers might differ, and that's ok.

Installing a module will automatically place the module in a folder named `node_modules` in your current working directory.

Make a new folder:

```
mkdir npm-experiments
cd npm-experiments
```

Install browserify:

```
npm install browserify
```

Now, if you look in the node_modules directory, you'll see browserify!

You can also install modules globally, typically so that you can run their commands at any time in any directory. This is useful with a module like browserify, so let's try it out:

```
npm install -g browserify
```

It's the `-g` option that install the module globally.

You can delete the node_modules directory:

```
rm -rf node_modules
```

And run the browserify command:

```
browserify
```

Without any options it'll only return help text. For more about browserify, check out the Introduction to browserify section.

To learn more about `npm` run the command without any options:

```
npm
```

This gives you a full list of the commands and options available through `npm`. To learn about any particular command you can run:

```
npm help name-of-command
```

## Creating a module
Any time you're using javascript modules from `npm` in a project you should create a package.json file. In this file you can save the dependencies for your project, along with license, author, repo inforamtion, and other details.

You can use the `npm init` command to generate a package.json file:

```
npm init
```

Answer the questions.

When you're done, you'll have a package.json file. You can install modules and save them as dependencies of your project like this:

```
npm install request --save
```

And if you are installing a module (like a test framework) as a development dependency, you can do so like this:

```
npm install tap --save-dev
```

## Publishing modules
Once you've written a module, you can publish it to `npm` super easy:

```
npm publish .
```

Before running the `npm publish` command you'll want to edit your package.json file to make sure that properties like version, author, homepage, and repository are all filled in. You should also first create a useful readme.md file, as that is displayed on a modules project page on [npmjs.org](http://npmjs.org).

## Finding modules
You can check out [npmjs.org](http://npmjs.org) as well as [npmsearch.com](http://npmsearch.com) to find modules that you can use in your projects.

You can also run the `search` command in the terminal:

```
npm search template
```

This will return a bunch of modules related to templates!

# Introduction to browserify.

There's all this wonderful code on `npm`, the node.js package manager.

What if we could use that code in the browser?

## Hey, we can. Use browserify.

With [browserify](https://github.com/substack/node-browserify), we can use some core node modules and many of the thousands of modules on `npm` in our browser-side code.

We can also write our browser-side javascript in the node.js style by using `require`.

Install browserify:

```
npm install -g browserify
```

We use the `-g` option to install browserify globally on your machine, allowing you to use it on the command line.

### Brief example:

```
// require the core node events module
var EventEmitter = require('events').EventEmitter;

//create a new event emitter
var emitter = new EventEmitter;

// set up a listener for the event
emitter.on('pizza', function(message){
  console.log(message);
});

// emit an event
emitter.emit('pizza', 'pizza is extremely yummy');
```

Put the above code in a file named index.js.

Now, to be able to run this code in the browser, enter this command in the terminal:

```
browserify index.js > bundle.js
```

The bundle.js file now has your event emitter code along with any dependencies on core node modules and shims to make them work in the browser.

You can include bundle.js in your html now like any other javascript file.

Example:

```
<!DOCTYPE html>
<html>
<head>
  <title>node / browserify example</title>
</head>
<body>

<script src="./bundle.js"></script>
</body>
</html>
```

That's it! Now you can use node modules and `require` in the browser!

## Live reload development environment
If you're in the middle of writing code, you'll find running `browserify` in the terminal to regenerate bundle.js, then refreshing the browser to be time-consuming and annoying.

**Enter beefy!**

`beefy` is a command-line tool for automatically generating and serving your browserify bundles as you develop. Each time you save your javascript file `beefy` will regenerate bundle.js and refresh the browser automatically.

Install beefy:

```
npm install -g beefy
```

Now, run this:

```
beefy index.js:bundle.js --live
```

The `--live` option enables the live reload functionality of beefy.

This will by default serve your index.html file at http://localhost:9966. Open Chrome, enter that url, then open the javascript console by using the keyboard shortcut `command+option+j`.

You'll see `pizza is extremely yummy` in the javascript console!



# Introduction to testing

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


# Additional resources

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
- [idiomatic.js](https://github.com/rwldrn/idiomatic.js)
- [idiomatic html](https://github.com/necolas/idiomatic-html)
- [idiomatic css](https://github.com/necolas/idiomatic-css)
- [airbnb js style guide](https://github.com/airbnb/javascript)
- [felixge node style guide](https://github.com/felixge/node-style-guide)
- [jQuery's javascript style guide](http://contribute.jquery.org/style-guide/js/
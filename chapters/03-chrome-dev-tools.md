# Chrome Developer Tools
 Hello, javascript. It's nice to meet you.

```
console.log('hello, javascript. it's nice to meet you');
```

Open up the browser Google Chrome.

> If you don't already have Chrome installed, download and install it now at [google.com/chrome](http://google.com/chrome)

Now, use this keyboard shortcut on a Mac: command + option + j
Or this, for Windows/Linux: control + shift + j

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

That's an error! Note how it shows up in red. Look in the bottom right corner of the browser. You'll see a little red circle with an x in the middle, and a number on its right side. That's a helpful little indicator of errors in your javascript, and any time something is wonky with your code, that red circle will show up.

With most errors you'll also be able to see a line number from your javascript file, which will help you pinpoint the offending code. We'll get into errors and debugging in more detail later in the book.

## More developer tools
The javascript console is just one of the tools available for web development inside of Chrome. For this book, we will focus on using Chrome and its developer tools for two reasons: Chrome has a a set of versatile and powerful tools, and focusing on the tools of one browser helps keep the instructions simple.

Check out the [Chrome Developer Tools documentation](https://developers.google.com/chrome-developer-tools/) to learn more about all that Chrome has to offer for developers working with javascript, html, and css.

It's also good to familiarize yourself with the developer tools in Firefox. Check out the [Mozilla Developer Network documentation for the Firefox developer tools](https://developer.mozilla.org/en-US/docs/Tools).

## Recap! We learned:
- the javascript console and learned that we can type in javascript!
- that we can use code like `console.log()` and `console.error()` to print information to the console
- that Chrome has a lot of useful tools (later in the book, we'll learn how they can help with experimenting with code, auditing the performance of our site, investigating the information sent between the browser and the server, and more!)
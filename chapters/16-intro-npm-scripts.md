# Introduction to npm scripts

As a simple alternative to using more complicated build tools like Gulp or Grunt, you can use npm scripts to run tasks like testing your JavaScript code or running a development server.

First create a package.json file if you don’t have one already:

```
npm init
```

This will ask you a few questions about your project. Answer the questions and you’ll get a package.json file.

It will look similar to this:

```
{
  "name": "example",
  "version": "0.0.0",
  "description": "example project",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "sethvincent",
  "license": "BSD"
}
```

You can revise the `main` property to be whatever makes sense for your project. If this won’t be released on npm, you might not even need `main`.

Now, check out the scripts section. There’s already test, but it needs to have an actual command associated with it. Change the error message to whatever command you use to run tests.

I might change it to something like this:

```
"scripts": {
  "test": "node test.js"
}
```

To run the tests, you run this command:

```
npm test
```

That doesn’t gain a whole lot of simplicity over just running node test.js, but when the command for running tests is more complicated, being able to run npm test instead helps out a lot.

## A development server
Let’s use a simple development server designed to work with [browserify](https://github.com/substack/node-browserify) named [beefy](https://github.com/chrisdickinson/beefy).

Install beefy as a development dependency:

```
npm install beefy --save-dev
```

Add a start script to your package.json:

```
"scripts": {
  "test": "node test.js",
  "start": "beefy index.js:bundle.js --live"
}
```

Now we start to see how npm scripts can be useful. That beefy command is just long enough that it’s useful to have npm start as an alias for our development server.

Just to prove it works, create an index.js file and pop in a short console.log statement:

```
console.log('it works!');
```

Now run npm start, and you’ll see output that looks like this:

```
> example@0.0.0 start /Users/sethvincent/workspace/bookery/tmp
> beefy index.js:bundle.js --live

listening on 9966
```

Now you can go to http://localhost:9966 to see if the console.log statement worked.

You might be saying, “Hey, I don’t have an index.html file. What is this magic?”

If there isn’t an index.html file in the directory you’re in when you run beefy, it’ll serve a really basic index.html file so your javascript can run.

Add another statement to your index.js file:

```
document.write('served.');
```

You’ll see that without reloading the page the string served is now displayed in your index.html file.

## Arbitrary scripts
There are a few default script names you can hook into and run your own scripts using npm aside from test and start. To see a list of them, read the npm-scripts documentation.

You can also run arbitrary scripts. Let’s add a script named +pizza+.

```
"scripts": {
  "test": "node test.js",
  "start": "beefy index.js:bundle.js --live",
  "pizza": "node pizza.js"
}
```

Let’s pretend pizza.js automates the process of ordering a pizza online from your favorite pizza place.

To run the command we prepend our script name with run, like this:

```
npm run pizza
```

You can add whatever scripts you want. You can even set up a master script that runs a bunch of your npm scripts! Chek it out:

```
"scripts": {
  "test": "node test.js",
  "start": "beefy index.js:bundle.js --live",
  "pizza": "node pizza.js",
  "everything": "npm run pizza && npm test && npm start"
}
```

In the terminal execute this command:

```
npm run everything
```

You just ordered pizza, ran tests, and started your development server! That’s pretty good. That easily rivals the most basic grunt.js implementations.

So, that gives you a sense of when to use npm scripts. Use npm scripts when your requirements are simple. You may find it will work for many situations.
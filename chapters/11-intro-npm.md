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

## Finding modules
You can check out [npmjs.org](http://npmjs.org) as well as [npmsearch.com](http://npmsearch.com) to find modules that you can use in your projects.

You can also run the `search` command in the terminal:

```
npm search template
```

This will return a bunch of modules related to templates!


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

Here's an example of an extremely simple module:

Take a string as input, and output that string in all uppercase letters:

```
module.exports = function(someString){
  return someString.toUpperCase();
}
```

Put that module definition in a file called index.js.

Now, create a file named test.js, and enter this text:

```
var upperize = require('./index');

var pizza = upperize('pizza is really awesome!');

console.log(pizza);
```

Run the test by typing this into your terminal:

```
node test.js
```

You should see this output:

```
PIZZA IS REALLY AWESOME!
```

In upcoming sections you'll learn about how to use node modules in the browser with browserify, and learn how to do more useful testing using a node module named tape.


## Publishing modules
Once you've written a module, you can publish it to `npm` super easy:

```
npm publish .
```

Before running the `npm publish` command you'll want to edit your package.json file to make sure that properties like version, author, homepage, and repository are all filled in. You should also first create a useful readme.md file, as that is displayed on a modules project page on [npmjs.org](http://npmjs.org).

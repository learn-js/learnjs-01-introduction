# Getting started with Node.js

Node.js is server-side javascript. It is well-suited to real-time applications and systems that are heavy on input and output. You can use it to create web servers, to manage information in databases, to build real-time communication tools, and more.

## To learn node in detail, read these resources in this order:
- [art of node](https://github.com/maxogden/art-of-node)
- [streams handbook](https://github.com/substack/stream-handbook)

## Install node:

There are a few options for this, and I've put them in my order of preference:

### Use nvm to manage node versions.
This option gives you the most control, allows you to switch between versions of node similar to using rvm or rbenv for Ruby. [Get nvm here](https://github.com/creationix/nvm). This is the method I use, and the one I recommend.

If you're on a Mac you'll need to first install Xcode, Apple's developer tools. You can now do this through the [Mac App Store](https://itunes.apple.com/us/app/xcode/id497799835?mt=12).

You should then install homebrew. Homebrew is a package manager for Macs. You can install it with this command:

```
ruby -e "$(curl -fsSL https://raw.github.com/mxcl/homebrew/go)"
```

### Install using a package manager. 
This is a good option, but sometimes package managers can be out of date. If the node version you'll be using matters for your project, you should make sure that the version in the package manager works for you. [Check out a list of package manager instructions here](https://github.com/joyent/node/wiki/Installing-Node.js-via-package-manager).

### Download an installer from nodejs.org.
[Here's the node.js download page](http://nodejs.org/download).

Installing node gives us the node package manager `npm`. We'll use it to install a wide range of packages, including web frameworks, game dev libraries, and client-side javascript modules. 

> This section of the book is still a work in progress. Make suggestions at [github.com/learn-js/learnjs/issues](http://github.com/learn-js/learnjs/issues).
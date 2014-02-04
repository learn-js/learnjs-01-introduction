# Introduction to grunt.js

Grunt is a tool for managing the javascript, css, and html files of your web project. Grunt is a task manager similar to Ruby's `rake`. You can run any arbitrary tasks you want, and there are a number of grunt plugins that make it easy to set up common tasks. Grunt is useful for running tests or for build steps, including turning sass, stylus, or less files into css, concatenating files, or creating .zip or .tar.gz packages of your project.

### Outline of the steps in this tutorial:

-   Install node.
-   Install grunt-cli.
-   Setup project.
-   Set up package.json.
-   Create Gruntfile.js.
-   Run grunt tasks.
-   Make an awesome project.

### Install node:

You should already have Node.js installed from chapter 4, "In-depth with Node.js". If not, backtrack to that chapter for a guide to installing Node.

### Install grunt-cli

Installing node gives us the node package manager `npm`. We'll use it to install grunt-cli, which is the command-line tool that is used to run grunt tasks. 

**Run this in your terminal after installing node.js:**

~~~~~~~~
npm intall -g grunt-cli
~~~~~~~~

This installs the grunt command-line tool globally on your machine. Now you can run the `grunt `command!

And, it won't do anything.

Bummer. **But it will give you a message like this**:

~~~~~~~~
grunt-cli: The grunt command line interface. (v0.1.6)
  Fatal error: Unable to find local grunt.
  If you're seeing this message, either a Gruntfile wasn't found or grunt hasn't been installed locally to your project. For more information about installing and configuring grunt, please see the Getting Started guide: [http://gruntjs.com/getting-started](http://gruntjs.com/getting-started)
~~~~~~~~

The grunt command looks for a locally installed version of grunt, which you can include in your project as a development dependency in a package.json file.

### Hey, package.json files are cool.

You can use a package.json file for a lot of useful purposes. Primarily, it's used to list your project's dependencies on npm packages, as well as list the name, description, version, and source repository of the project. You can specify the type of license, version of node the project requires, the project's contributors, and more. Check out [this interactive package.json cheatsheet][http://package.json.nodejitsu.com/] for a nice rundown on the basics.

So, our package.json will specify some development dependencies. 

**Some basic requirements:**

- We'll test the javascript with qunit.
- We'll write scss and compile it to css, then minify the css.
- We'll concatenate and uglify our javascript files.
- We'll use the `grunt watch` command to automatically run grunt tasks when files are edited.
- We'll want a little http server to check out our game as we're developing it. 

Some of the above requirements could be perceived as excessive, but they help make this a meaty and useful tutorial, so deal with it.

**So, we'll need to use some grunt plugins. We'll use these ones:**

- [grunt-contrib-qunit][https://github.com/gruntjs/grunt-contrib-qunit]
- [grunt-contrib-jshint][https://github.com/gruntjs/grunt-contrib-jshint]
- [grunt-contrib-connect][https://github.com/gruntjs/grunt-contrib-connect]
- [grunt-contrib-watch][https://github.com/gruntjs/grunt-contrib-watch]


**That means our package.json file will look like this:**

~~~~~~~~
{ 
  "name": "your-project-name", 
  "version": "0.0.1", 
  "author": "Super Big Tree <seth@superbigtree.com>", 
  "description": "A silly game.", 
  "repository": { 
    "type": "git", 
    "url": "https://github.com/your-profile/your-project-name.git" 
  }, 
  "devDependencies": { 
      "grunt": "~0.4.0",
      "grunt-contrib-qunit": "~0.2.0",
      "grunt-contrib-jshint": "~0.1.1",
      "grunt-contrib-connect": "~0.1.2",
      "grunt-contrib-watch": "~0.4.4"
}, 
 "license": "MIT", 
 "engines": { 
 "node": ">=0.8" 
 } 
}
~~~~~~~~

**Go to your terminal. Create a folder that you want to serve as the project's folder:**

~~~~~~~~
cd wherever/you/want/the/project/to/live
mkdir your-project-name
cd your-project-name
~~~~~~~~

Now, create your package.json file:

~~~~~~~~
touch package.json
~~~~~~~~

Copy and paste the above package.json example into your package.json file using your favorite text editor. Save the file. **Now, you can run
this:**

~~~~~~~~
npm install
~~~~~~~~

to install all the dependencies.

If you run the command and get an error like this at the end, then something is not ok:

~~~~~~~~
npm ERR! not ok code 0
~~~~~~~~

There's an error of some kind that will need to be worked out. For me, typically the problem is that I messed up the syntax or put the wrong version number for a dependency, so check things like that first.

### Project setup:

Let's make all our files and folders now!

**This will make all the folders we want:**

~~~~~~~~
> mkdir -p test js css/scss img
~~~~~~~~

**This will make the files we want:**

~~~~~~~~
touch js/player.js js/game.js js/enemies.js js/ui.js \
touch css/scss/main.scss css/scss/reset.scss css/scss/ui.scss \
touch test/player.js test/enemies.js test/game.js test/ui.js
~~~~~~~~

Cool. Did that. **Now we make the Gruntfile:**

~~~~~~~~
touch Gruntfile.js
~~~~~~~~

**Open Gruntfile.js in your favorite editor and paste in this:**

~~~~~~~~
module.exports = function(grunt) {
  grunt.initConfig({
    // and here we do some cool stuff
  });
};
~~~~~~~~

The above code is the required wrapper code to make a Gruntfile work. Now, remember our package.json file. Buds, we can use the values from that file in our Gruntfile.

**Check it out: **Let's say we're making a javascript library and want to put stuff like the name, version, author, source repository, and license of the project in a multi-line comment at the top of the file. It would be a bummer to have to edit that by hand every time the file is compiled for a new release. Instead, we can use values from package.json in our Gruntfile!

First step is to read the contents of package.json by **putting this line in Gruntfile.js**:

~~~~~~~~
pkg: grunt.file.readJSON('package.json');
~~~~~~~~

A package.json file is just JSON, right? Yeah, so it's easy to get at the values to do cool stuff.

For fun, let's see what it takes to run a custom task inside a Gruntfile, and have it log some attributes from the package.json file. Alright? OK.

This is a really simple task that logs the package name and version to the console, shown here as the complete Gruntfile.js:

~~~~~~~~
module.exports = function(grunt) {
  grunt.initConfig({
    // read the json file
    pkg: grunt.file.readJSON('package.json'),

    log: {
      // this is the name of the project in package.json
      name: '<%= pkg.name %>', 

      // the version of the project in package.json
      version: '<%= pkg.version %>' 
    }
  });

  grunt.registerMultiTask('log', 'Log project details.', function() {     
    // because this uses the registerMultiTask function it runs grunt.log.writeln()     
    // for each attribute in the above log: {} object     
    grunt.log.writeln(this.target + ': ' + this.data);   
  });
};
~~~~~~~~

**You can now run your task on the command line!:**

~~~~~~~~
grunt log
~~~~~~~~


**You should get output like this:**

~~~~~~~~
Running 'log:name' (log) task 
name: your-project-name
Running 'log:version' (log) task
version: 0.0.1
Done, without errors.
~~~~~~~~

If you didn't get output like that, check your Gruntfile for typos. If you did get output like that: Awesome! So we've made it pretty far. We've set up a project with a bunch of files and folders, created a package.json file with a list of devDependencies, installed the dependencies, and tried out a simple Gruntfile for running arbitrary tasks.

If this seems like a lot, like it's beating up your brain, don't worry. After a few times of starting a project like this, these initial steps will get faster and easier. Heck, you might even create some kind of base project that you can build on with each new project so that you don't have to write the boilerplate every time. Or you could use a project like yeoman for its code generators. That's up to you, but when first learning this it's a reasonable idea to start from scratch and see how everything works.
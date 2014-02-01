# Introduction to git & GitHub

Developing websites and applications without using git is equivalent to writing in Microsoft Word without ever saving your work.

**Use git.**

Git is a version control system, which means it can track every change you make to your code. This allows you to review and edit past versions if you mess something up. And it allows you to figure out when errors were introduced to the code.

There are many other bonuses to using git, which are mostly out of this book's scope.

The best way to start learning git (and GitHub) is to visit [try.github.com](http://try.github.com). You should also try [githug, a game for learning git](https://github.com/Gazler/githug).

## Here are some basics of using git:

Create a git repository:

~~~~~~~~
cd name-of-folder
git init
~~~~~~~~

Add files:

~~~~~~~~
git add name-of-file

// or add all files in directory:

git add .
~~~~~~~~

When you add files to a git repository they are "staged" and ready to be committed.

Remove files:
~~~~~~~~
git rm name-of-file

// force removal of files:

git rm -rf name-of-file-or-directory
~~~~~~~~

Commit files and add a message using the `-m` option:

~~~~~~~~
git commit -m 'a message describing the commit'
~~~~~~~~

Create a branch:

~~~~~~~~
git branch name-of-branch
~~~~~~~~

Checkout a branch:

~~~~~~~~
git checkout name-of-branch
~~~~~~~~

Shortcut for creating a new branch and checking it out:

~~~~~~~~
git checkout -b name-of-branch
~~~~~~~~

Merge a branch into the master branch:

~~~~~~~~
git checkout master
git merge name-of-branch
~~~~~~~~

Add a remote repository:

~~~~~~~~
git remote add origin git@github.com:yourname/projectname.git
~~~~~~~~

List associated repositories:

~~~~~~~~
git remote -v
~~~~~~~~

Pull changes from a remote repository:

~~~~~~~~
git pull origin master
~~~~~~~~

Push changes to a remote repository

~~~~~~~~
git push origin master
~~~~~~~~

Checkout a remote branch:

~~~~~~~~
git checkout -t origin/haml
~~~~~~~~

## Get on GitHub
If you haven't already, create an account at [github.com](http://github.com).

GitHub is a great place to host your code. Many employers hiring for developer and designer positions will ask for a GitHub profile, and they'll use your GitHub activity as part of the criteria in their decision-making process.

In fact, if you're looking to get a job with a particular company, try to find _their_ GitHub profile and start contributing to their open source projects. This will help you stand out, and they'll already know your technical abilities based on your open source contributions. That's a big win.

GitHub has become the de facto code hosting service for most open source communities.

### With GitHub Pages you can:
- design a website any way you want by having complete control over the html, css, and javascript.
- use simple templates for getting started using GitHub Pages.
- create sites for yourself and all of your projects hosted on GitHub.
- use a custom domain name if you want!

Visit the [help section for GitHub Pages](https://help.github.com/categories/20/articles) to learn more details about hosting sites on GitHub.


## Create a site for yourself using GitHub

GitHub has a useful service called [GitHub Pages](http://pages.github.com) that allows you to host a simple site on their servers for free.

To get started, fork this simple template: [github.com/maxogden/gh-pages-template](https://github.com/maxogden/gh-pages-template).

Visit that github project, make sure you're logged in, and click Fork in the upper right side of the screen.

Fork gh-pages-template to your personal account.

Rename the repository from gh-pages-template to whatever you want by clicking on Settings on the right side of your fork of the repository, and changing the name there. GitHub will warn

That's it! You now have a website hosted through GitHub Pages.

You'll be able to visit your site at __YOUR-USERNAME__.github.com/__YOUR-PROJECT-NAME__.

You'll want to edit the content though, right? Add your cat pictures or resume or pizza recipes? You can do that.

You can create, edit, move, rename, and delete files all through the GitHub website. Check out these blog posts on GitHub for details on how to do those things:
- [Create files](https://github.com/blog/1327-creating-files-on-github)
- [Edit files](https://github.com/blog/143-inline-file-editing)
- [Move and rename files](https://github.com/blog/1436-moving-and-renaming-files-on-github)
- [Delete files](https://github.com/blog/1545-deleting-files-on-github)

You can also clone the project repository onto your computer:

~~~~~~~~
git clone git@github.com:__YOUR-USERNAME__/__YOUR-PROJECT-NAME__.git
~~~~~~~~

You can copy the git url to clone from the right-hand sidebar of your project repository.

After cloning the repository, `cd` into it and make some changes:

~~~~~~~~
cd __YOUR-PROJECT-NAME__
nano index.html
~~~~~~~~

Add a bunch of content to index.html, and change the styles in style.css.

After you've made some changes, add them to the repo and commit the changes:

~~~~~~~~
git add .
git commit -m 'include a brief, clear message about the changes'
~~~~~~~~

Now, push your changes back to GitHub:

~~~~~~~~
git push origin gh-pages
~~~~~~~~

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

There are a few options for this, and I've put them in my order of preference:

**Use nvm to manage node versions** This option gives you the most control, allows you to switch between versions of node similar to using rvm or rbenv for Ruby. [Get nvm here](https://github.com/creationix/nvm).

**Install using a package manager.** This is a good option, but sometimes package managers can be out of date. If the node version you'll be using matters for your project, you should make sure that the version in the package manager works for you. [Check out a list of package manager instructions here][https://github.com/joyent/node/wiki/Installing-Node.js-via-package-manager].

**Download an installer from nodejs.org.
**[Here's the node.js download page][nodejs.org/download].

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


# Package managers for browser code: what should I use?

When should I use npm, bower, or component for managing client-side code?

To start: always use one of them. The old days of downloading js/css libraries one by one and updating them manually are totally over, and that's exciting. Using a package manager for front-end code means we can easily download libraries, keep track of versions, and ease dependency management.

But we still have too many options for how to manage our client-side code. Beyond npm, bower, and component there are still many other options, but those three seem to be settling in as the most widely adopted.

## And all three are quite different:

### npm
npm nominally started out as a package manager for node, but now is used for any javascript, and along with a tool like browserify it's easy to use npm packages and node-style modules in the browser. It's not super useful for css libraries – but it's easy to imagine a tool (built on something like brfs) that could make bundling css npm packages super pleasant.

### bower
bower is a clear hero of client-side code: it's great for both css and javascript. It's easy to manage dependencies – even if those dependencies don't have a config file for bower. You can install a file or git repository as a dependency alongside packages in the bower registry. Bower doesn't make any assumptions about how you build or deploy code, so it is compatible with amd modules.

### component
component is a tool with a more focused and defined goal than npm and bower. It uses common js style modules. Each component may contain javascript, css, fonts, and images. Some javascript-only components can also be used in node.js. See the [Component FAQ](https://github.com/component/component/wiki/F.A.Q) for more details.

## When I use npm for browser code:
Games. There's been a lot of interesting activity in javascript game development in the node.js community using browserify. voxel.js is one of the biggest examples, with a goal of creating minecraft-like games in the browser. See the work of these people for examples:

npm/browserify will also be useful for creating applications that might share javascript code on the server and the browser. This approach also works well when the javascript requirements for the client-side are minimal, or if you prefer to write client-side code in a node style.

## When I use bower for browser code:
When the project requires a front-end framework like backbone, angular, or ember, I use bower as the package manager. It's currently the best way to package arbitrary dependencies of a javascript application. Typically using bower means that I am also using the build tool grunt.

## I don't really use component yet.
I really want to. It seems like there's some great work happening around component. I expect that there will be instances when I'll want to use some of the available components. But when that happens, I'll probably need to figure out a way to integrate component with bower or npm/browserify.

## Use all three at once!
It's possible to use packages from both bower and component while using browserify!

Check out this great guide for using components, bower packages, amd modules, and even global variables with browserify: http://dontkry.com/posts/code/browserify-and-the-universal-module-definition.html
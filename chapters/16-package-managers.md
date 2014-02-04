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
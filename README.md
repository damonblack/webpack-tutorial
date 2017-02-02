Barebones starting point for building a javascript app with Yarn and Webpack

Requirements
  * [Yarn](https://yarnpkg.com/) package manager + [Node.js](https://nodejs.org/) v6.5 or newer


Let's start from the beginning. Here's a very simple webpack project.

- Create a directory for your project and cd to into it.

- `yarn init` and answer some questions. You can edit this information manually later. Yarn is a package manager (like npm) that will help us install and keep track of anything we need to build our project. The default config will offer 'index.js' as the entry point for your app, but I like 'app.js':

- `yarn add -D webpack@beta` Webpack is a module builder that we'll use to bundle our frontend code and its dependencies. 'yarn add' installs it in the node_modules directory (which it will create if it's not there already). The -D option flags webpack as a 'devDependency', something we'll need to facillitate builds but not required for the release bundle. Yarn generates a `yarn.lock` files wich is like snapshot of all the libraries used in the last successful build. We'll want to commit this to our repo.

- Create a `src` directory to keep our source files.

- In the src directory create an app.js file that does something. A simple alert call is a fine proof of concept, but we'll be loading this in an html page, so feel free to monkey with the dom or something fancier.

- Bundle your new 'app' with webpack: `./node_modules/.bin/webpack src/app.js build/app.bundle.js`. This will bundle your app and all it's dendencies and make it available in the build dir. Assuming your file has no dependencies, webpack won't be doing much yet. If we wanted to we could have installed webpack globally, rather than tracking down it's binary in the node_modules folder, but it's better practice to install and use it as a local dependency.

- Now create an html file in the root dir to load your bundled javascript from the build dir.

- Open the html file in a browser and admire your handiwork.

- Lastly, we'll add the build and node_modules to our .gitignore file.

For the next step: [tutorial/step-one](https://github.com/damonblack/webpack-tutorial/tree/tutorial/step-one)

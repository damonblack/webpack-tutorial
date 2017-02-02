##Step Two

We want to live in the future, not the past. So let's pretend the latest ECMAScript spec has been widely adopted and write our code with the shiny new syntax!

As an example, we could add some code to our `app.js` file that won't work in some browsers. The exponentian operator (**) will work in the latest version of Chrome, but not Firefox (51.0.1). Replace your current app.js code with this:

```javascript
alert(`4 squared is ${4 ** 2}`);
```

If you `yarn run build` and then open the `index.html` with Chrome, this will work. If you open it in Firefox v51.0.1 or older, it won't. But we can fix that. We'll use [babel](http://babeljs.io/). Add babel's webpack loader and a preset configuration with:

- `yarn add -D babel-core babel-loader babel-preset-latest`

Babel is a transpiler that let's us write code using next generation javascript syntax, but converts it to older versions of javaacript for browsers that don't yet support the new features.

Add the following to your webpack.config.js file:

```javascript
module.exports = {
  entry: './src/app.js',
  output: {/
    path: './build',
    filename: 'app.bundle.js'
  },
  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: {
          loader: 'babel-loader'
        }
      }
    ]
  }
};
```

This tells webpack to apply the babel-loader to any files imported into our module that have the '.js' extension, except for those in the node modules directory. You can add multiple loaders for a given extension. They'll be chained (the results of one loader are passed to the next as its src) and applied in reverse order.

We'll also need to add some configuration for babel. Create a `.babelrc` file in your project root with the following:

```javacript
{
  "presets": ["latest"]
}
```

If you rebuild your bundle (`yarn run build`) and open your `index.html` file in Firefox, it should now work.

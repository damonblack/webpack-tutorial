##Step One

Let's create a webpack configuration file, and a task to run our build from package.json

- Create a file named weback.config.js file with the following:

```javascript
module.exports = {
  entry: './src/app.js',
  output: {
    path: './build',
    filename: 'app.bundle.js'
  }
};`
```

- Now we can call webpack without the entry and output arguments: `./node_modules/.bin/webpack`

- Open your `package.json` file and add a "scripts" block like so:

```javascript
{
  ...
  "license": "MIT",
  "scripts": {
    "build": "webpack"
  },
  "devDependencies": {
    "webpack": "beta",
  }
}
```

- Now, from the root of your project you can build with `yarn run build`

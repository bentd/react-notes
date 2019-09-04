# Babel


### purpose

- babel compiles new js versions into older, more browser-compatible, js versions via polyfills

- includes source maps that links each compiled code block to the source code block for easy debugging

- babel is made up of a core library and additional plugins

- plugins polyfill older javascript features

- presets are sets of plugins


### presets and plugins for 'webpack+babel' react:

- `env` (preset for previous javascript versions and language features)

- `react` (preset for react specific functions)

- `transform-runtime` (plugin for await and async)


### npm

```bash
$ npm init

$ npm install --save-dev webpack webpack-cli webpack-dev-server @babel/core @babel/cli @babel/preset-env @babel/plugin-transform-runtime @babel/preset-react  @babel/preset-stage-1 babel-loader
# required for build process

$ npm install --save @babel/runtime
# required for runtime
```


### package.json

```json
"scripts":
{
    "dev": "webpack-dev-server --env.dev",
 	"build": "webpack"  
}
```


### index.js

```javascript
document.write("hello world");
```


### index.html

```html
<script src="./bundle.js"></script>
```


### webpack.config.js

```javascript
module.exports = {
  entry: "./index.js",
  output: { filename: "bundle.js" },
  module: {
    rules: [
      {
        test: /.js$/,
        exclude: /node_modules/,
        use: [
          {
            loader: "babel-loader",
            options: { cacheDirectory: true },
          }
        ],
      }
    ],
  }
}      

```

```
{ test: /.js$/ } (loads only js files into babel)

{ loader: "babel-loader" } == "use babel for compilation"

{ options: { cacheDirectory: true } } == "caches to improve perf"
```


### .babelrc

```
{
    "presets": [
        ["@babel/preset-env", { "modules": false }],
        "@babel/preset-react"
    ],

    "plugins": [
        "@babel/plugin-transform-runtime"
    ]
}

```

```
["@babel/preset-env", { "modules": false }] == "allows webpack to optimize for perf"
```


### npm

```bash
$ npm run dev
# localhost:8080

$ npm run build
# bundle.js
```

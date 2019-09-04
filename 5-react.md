# Basic React App


### npm

```bash
$ npm init

$ npm install --save-dev webpack webpack-cli webpack-dev-server @babel/core @babel/cli @babel/preset-env @babel/plugin-transform-runtime @babel/preset-react  @babel/preset-stage-1 babel-loader

$ npm install --save @babel/runtime

$ npm install --save react react-dom
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
import React, { Component } from "react"
import ReactDOM from "react-dom"

const styles = {
    app: {
        paddingTop: 40,
        textAlign: "center" }}

class App extends Component
{
    render() { return (<div style={styles.app}>Welcome to React!</div>) }
}

const root = document.querySelector('#app')
ReactDOM.render(<App />, root)
```


### index.html

```html
<div id="app"></div>
<script src="./bundle.js"></script>
```


### webpack.config.js

```javascript
module.exports = {
  entry: "./index.js",
  output: {
    filename: "bundle.js"
  },
  module: {
    rules: [
      {
        test: /.js$/,
        exclude: /node_modules/,
        use: [
          {
            loader: "babel-loader",
            options: {
              cacheDirectory: true
            },  
          }
        ],
      }
    ]
  }
}

```


### .babelrc

```
{
    "presets":
    [
        ["@babel/preset-env", { "modules": false }],
        "@babel/preset-react"
    ],

    "plugins":
    [
        "@babel/plugin-transform-runtime"
    ]
}

```


### npm

```bash
$ npm run dev
# localhost:8080

$ npm run build
# bundle.js
```

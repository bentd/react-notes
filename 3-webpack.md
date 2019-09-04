# Webpack


### purpose

- allows for more options outside of create-react-app
- condenses client side javascript and dependencies into one file
- index.js + css + etc > bundle.js


### npm

``` bash
$ npm init
$ npm install --save-dev webpack webpack-cli webpack-dev-server
```


### package.json

```json
"scripts":
{
    "dev": "webpack-dev-server --env.dev",
 	"build": "webpack"  
}
```


```
env.dev == { "env": "dev" }

{ "build": "webpack" } == "webpack builds bundle.js"
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
	output: {filename: "bundle.js"}, }
```


### npm

```bash
$ npm run dev
# localhost:8080

$ npm run build
# bundle.js
```

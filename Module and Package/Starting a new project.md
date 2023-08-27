#babel #npmInstall #watchfile #scripts 
`npm init`
Inside the new folder, start with `npm init` so it creates the package.json to store relevant information required for the project

`npm install @babel/core @babel/cli --save-dev`
`--save-dev` makes it a developer dependency, then itll show up in the `package.json` file

```json
{
	"name": "babel_learn",
	"version": "1.0.0",
	"description": "",
	"main": "index.js",
	"scripts": {
	"test": "echo \"Error: no test specified\" && exit 1"
},
"author": "",
"license": "ISC",
"devDependencies": {
	"@babel/cli": "^7.22.9",
	"@babel/core": "^7.22.9"
}
}
```

Installing babel preset
`npm install @babel/preset-env --save-dev`
Go to your source folder, create a new file called `.babelrc`
```babelrc
{
	"presets":["@babel/preset-env"]
}
```

This code will convert your existing before.js file to after.js file, dont 'cd', just run the code
`node_modules/.bin/babel before.js -o after.js `

**Never send or push node_modules folder** 

Folder structure
- bundle.js inside of assets folder (inside of dist, dist stands for distrubution) contains code that are browser compliant that will run in all browser

This is `package.json`
```json
{
	"name": "babel_learn",
	"version": "1.0.0",
	"description": "",
	"main": "index.js",
	"scripts": {
		"babel":"node_modules/.bin/babel src/index.js -w -o dist/assets/bundle.js"
	},
"author": "",
"license": "ISC",
"devDependencies": {
	"@babel/cli": "^7.22.9",
	"@babel/core": "^7.22.9",
	"@babel/preset-env": "^7.22.9"
}
}
```
go to terminal, type `npm run babel` then itll run the script inside `scripts`
The `-w` inside babel means  'watch file'. So everytime when something changes, it'll update it

## Webpack 
#webpack #webpackCli

`webpack.config.js`
```js
const path = require('path');
module.exports = {
	entry:'./src/index.js',
	output: {
	path: path.resolve(__dirname, 'dist/assets'),
	filename: 'bundle.js'
}
};
```
then you need to run `node_modules/.bin/webpack` for the first time 

Dont forget to add to script and set up watch file
```json
"scripts": {
	"babel": "node_modules/.bin/babel src/index.js -o dist/assets/bundle.js",
	"webpack": "node_modules/.bin/webpack -w"
},
```

`npm run webpack`

**Export and Export default **
If you have a js file like that, when you import it in another file, its a little different
`data.js`
```js
const users = [
	{name: 'mario', premium: true},
	{name: 'luigi', premium: false},
	{name: 'yoshit', premium: true}
]
export const getPremUsers = (users) => {
	return users.filter(user => user.premium);
}

export default users;
```

```js
import users, { getPremUsers } from './data';
```
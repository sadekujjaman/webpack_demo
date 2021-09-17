# Webpack
---------------------
Webpack is a static module bundler. It is used to compile JavaScript modules. 

In this project, we create a very basic webpack project by covering the following features: 

* Creating demo webpack project using webpack and webpack-dev-server.
* Creating webpack configuration file(webpack.config.js).
* Configuring dev server and port in webpack configuration file.
* Using webpack configuration file in package.json file.
* Managing css styling in webpack config and index.js file.

<em>N.B: The minimum supported Node.js version to run webpack 5 is 10.13.0 (LTS)</em>

To Run this project follow one of those two ways. 
# Way - 1 -> Custom setup

* Create webpack project with name `webpack_demo` and initialize npm(run the following command one by one): 
```
mkdir webpack_demo
cd webpack_demo
npm init -y
```

* Create the following directory structure and files(Create empty files for now, will update in future):
```
  webpack-demo
  |- package.json
  |- index.html
  |- /src
    |- index.js
    |- style.css
  |- webpack.config.js
  
```

* Now replace the content in the respective file.

# package.json
```
{
  "name": "webpack_demo",
  "version": "1.0.0",
  "description": "",
  "private": "true",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "build": "webpack-dev-server --config webpack.config.js --mode development --hot"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "css-loader": "^6.2.0",
    "style-loader": "^3.2.1",
    "webpack": "^5.53.0",
    "webpack-cli": "^4.8.0",
    "webpack-dev-server": "^4.2.1"
  },
  "dependencies": {
    "lodash": "^4.17.21"
  }
}

```

# webpack.config.js
```
const path = require('path');

module.exports = {
  entry: './src/index.js',
  output: {
    filename: 'bundle.js',
    path: path.resolve(__dirname, 'dist'),
  },
  devServer: {
    static: {
      directory: path.join(__dirname, ''),
    },
    compress: true,
    port: 3000,
  },
  module: {
    rules: [
      {
        test: /\.css$/i,
        use: ['style-loader', 'css-loader'],
      },
    ],
  },

};
```

# style.css
```
.hello {
    color: blue;
    font-weight: bold;
}
```

# index.js
```

import _ from 'lodash'
import './style.css'

function component(){
    const element = document.createElement('div')
    element.innerHTML = _.join(["Hello", "Webpack"], ' ')
    element.classList.add('hello');

    return element;
}

document.body.appendChild(component())

```

# index.html
```
<!DOCTYPE html>
<html>
    <head>
        <title>Webpack Getting Started!</title>
    </head>

    <body>
        <script src="bundle.js"></script>
    </body>
</html>
```


* Build and run
After everyting is setup, to build this project, just run the following command `npm run build`. This command will build the entire project and start the webpack dev server with port number 3000. Then paste the following url in the browser `localhost:3000/`.

* Output
This output will show in the browser: <b>Hello Webpack</b> with blue color.

# Way - 2 -> Clone the repository
This is very simple way to run the project. Simply follow these step one by one.
1. Clone the repo: `git clone https://github.com/sadekujjaman/webpack_demo.git`
2. Goto the project directory: `cd webpack_demo`
3. Initialize NPM(Create node modules): `npm install`
4. Build the project: `npm run build`
5. Open the browser and enter this url: `http://localhost:3000/`
6. Output: <b>Hello Webpack</b> with blue color.




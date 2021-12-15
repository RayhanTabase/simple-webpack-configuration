# simple-webpack-configuration
A simple guide for initial set up of webpack

## 1. To begin a new webpack project run the following npm installations
- npm init -y
- npm install webpack webpack-cli --save-dev
- npm install --save-dev style-loader css-loader
- npm install --save-dev html-webpack-plugin
- npm install --save-dev webpack-dev-server

## 2. Modify your package.json file that has been created
- Remove this -> ```"main": "index.js" ```
- Add this in it's place -> ```"private": true```
- change the scripts key in package.json to look like this ->
  ```
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "webpack serve --open",
    "build": "webpack",
    }, 
  ```
 
 ## 3. Add the webpack config file
 - Add the webpack.config.js file to the project
 -
 - its contents should be ->
 ```
  const path = require('path');
  const HtmlWebpackPlugin = require('html-webpack-plugin');

  module.exports = {
    mode: 'development',
    entry: {
      index: './src/index.js',
    },
    devServer: {
      static: './dist',
    },
    plugins: [
      new HtmlWebpackPlugin({
        template: './src/index.html',
      }),
    ],
    output: {
      filename: '[name].bundle.js',
      path: path.resolve(__dirname, 'dist'),
      clean: true,
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

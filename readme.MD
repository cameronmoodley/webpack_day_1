# What is Webpack?

Webpack is a **modern module bundler**. It is primarily used to bundle JavaScript files however it can perform operations on CSS, HTML and images. Webpack handles most front-end assists.

Webpack is used in all frameworks. Generally, when you create your application the webpack configuration file will be included in the project for you.

You will get a **zero-configuration file**, no extra work will be needed from you.

## Setting up folder structures
The zero-configuration webpack looks for certain starting points or folders inside your application. Webpack will look for a folder called **src** and a file inside the src folder called **index.js.** 

```
myFirstAutomatedProject
|__src
|   |__greeting.js
|   |__index.js
|   |__index.html
|__node_modules (Will be created when you install your plugins)
|__package.json
```


Create a folder on your desktop called **myFirstAutomatedProject** inside the folder you’ve just created, add a folder called **src** and inside the **src** folder create a file called **index.js.**

## Creating and updating the package.json file

Run the **“npm init -Y”** command while you are cd’ed into the **myFirstAutomatedProject.** This allows you to create a **package.json** file without answering any of the questions. The project is **initialized** as well.

### Setting up scripts
In your package.json you can set up **scripts** to execute certain commands. In our case we would like to run webpack. We are going to manually configure webpack to run inside our package.json file.

```json
{
  "name": "myFirstAutomatedProject",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "build": "webpack",
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {

  }
}
```
We have created a **scripts key** and its value is an **object**. Inside this object you can define commands you want to run in your terminal. We have created a build command and we would like to launch the **Webpack CLI**. The CLI provides a **C**ommand **L**ine **I**nterface which allows you to interact with your build.

### Installing packages

Before we use webpack, we need to install it first. We can run the following command:

**npm i -D webpack webpack-cli**

The **-D command** saves **webpack** and **webpack-cli** to our project as **a dev dependency**. 

### Testing 
Create a **greeting.js** file inside the **src folder.**

```javascript
const greeting = (name) => {
    console.log(`Hi ${name}`)
}

export { greeting };
```

Inside the **greeting.js file** create a **function expression** which takes in a **parameter**. Then **export** it as module.

#### index.js
```javascript
import { greeting } from './greeting.js';

greeting('Feu2');
```

Import the **module** into your index.js file, then call the function. 

**The index.html file**
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="index.js"></script>
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```
Import the **index.js** file inside your src folder in your HTML and look at your console. 

![error](error.png)

Your **browser** does not understand what an **import statement** is. It will throw an error.

While you are cd’ed in your folder run the command: **“npm run build”** which we defined inside our package.json file.

A **dist folder** should have been created for you. Link the **main.js** file in your html.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="./../dist/main.js"></script>
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```

If you run the html in your browser, you see **“Hi Feu2”** in your console.



**Webpack** took JavaScript which a browser could not interpret and converted it into **browser friendly code**. You can peek inside the **main.js** file, it is minified, but if you look closely enough towards the end you will be able to see your code.

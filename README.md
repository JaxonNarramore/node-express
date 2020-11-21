# Node

## Creating a package
```text
npm init (more specific) or npm init -y (for basic settings)
```

## Opening in terminal
```text
node index.js
```

## To export a function
```js
module.exports.beBasic = () => "That's so fetch!"
```
or 
```js
module.exports = {
    add,
    subtract
}
```

## To import a function 
```js
const { add, subtract, beBasic } = require('./folderName');
```

## Examples

### Exporting file

```js
module.exports = {
    multiply
}

function multiply(num1, num2) {
    return num1 * num2;
}
```

### Importing file

```js
const { multiply } = require('./folderName');

console.log(multiply(5, 5));
```

## Or you can import/export multiple files


```js
module.exports = {
    multiply,
    divide
}

function multiply(num1, num2) {
    return num1 * num2;
}
function divide(num1, num2) {
    return num1 / num2;
}
```

### Importing file

```js
const { multiply, divide } = require('./folderName');

console.log(multiply(5, 5));
console.log(divide(25, 5));
```

## Adding npm package to project
```text
npm install packageName
```

## Installing package globally
```text
npm install --global packageName
```
or
```text
npm i -g packageName
```

## To start Nodemon auto update in terminal
```text
nodemon index.js
```

## To stop ronning the Nodemon feature
```text
ctrl + c 
```

## Using .gitignore to not show packages
```text 
touch .gitignore
```
```text
inside of the file put the name of the file you are wanting to ignore
```

# Express

## Installing Express

```text
npm i express
```

## Importing Express into file

```js
const express = require('express');
```

## Creating Express app

```js
const app = express();
```

## Creating a home route

```js
app.get('/', (req, res) => {
  res.render("You've reached the home route!");
});
```

## Linking to local server 

```js
app.listen(8000);
```
or

```js
app.listen(8000, () => {
    console.log('Server started');
});
```

## Run nodemon

```text
nodemon
```

## To create multiple routes

```js
app.get('/about', function(req, res) {
    res.render('about');
});
```

## Sending text from server to client
 
```js
app.get('/blog', (req, res) => {
    res.render('Text that you want to send to the client');
})
```

## Sending information through a view template

First you must make a file 'blog-generic.ejs' and then render that in your app.get function and any text you write into the 'blog-generic.ejs' file will appear in that route on the HTML page.
```js
app.get('/blog', (req, res) => {
    res.render('blog-generic.ejs');
})
```

## Refrencing variables in the view template
In the .js file
```js
app.get('/', function(req, res) {
  res.render('index', {name: "Sterling Archer", age: 35});
});
```
in the .ejs file
```html
<html>
  <head>
    <title>Home Page</title>
  </head>
  <body>
    <h1>Hello, <%= name %>!</h1>
  </body>
</html>
```
```html
<html>
  <head>
    <title>Home Page</title>
  </head>
  <body>
    <h1>Hello, <%= name %>!</h1>
    <h2>You are <%= age*7 %> in dog years.</h2>
  </body>
</html>
```

# Sequelize

## Installing Sequelize and Postgres
```text
npm install sequelize
```

```text
npm install pg
```
## Initalizing Sequelize
```text
sequelize init
```

## Creating a database
```text
sequelize db:create
```

## Creating a model
```text
sequelize model:create --name user --attributes firstName:string,lastName:string,age:integer,email:string
```

## Migrate database
```text
sequelize db:migrate
```

## To undo a migration (if you need to update parts of database)
```text
sequelize db:migrate:undo
```

# PSQL

## To connect to the database
```text
\c name_devolpment
```

# CRUD

## Create
```js
db.user.create({
    firstName: 'Haley',
    lastName: 'Narramore',
    age: 21
}).then(createdUser => {
    console.log(createdUser.get());
});
```

## Read
```js
db.user.findOne({
    where: { firstName: 'Haley' }
}).then(foundUser => {
    console.log(foundUser.get());
});

// Find all users

db.user.findAll().then(allUsers => {
    console.log(allUsers);
    console.log(allUsers[0].get());
});
```

## Update
```js
db.user.update({
    lastName: 'Smith'
}, {
    where: { firstName: 'Haley' }
}).then(numRowsChanged => {
    console.log(numRowsChanged);
});
```

## Destory
```js
db.user.destroy({
    where: { lastName: 'Smith' }
}).then(numRowsDeleted => {
    console.log(numRowsDeleted);
});
```

## Using findOrCreate
```js
db.movie.findOrCreate({
    where: { title: 'Godfather'},
    defaults: {
        byline: 'Vincent Canby',
        headline: 'Godfather, Part II',
        date: Date.now(),
        url: 'http://nytimes.com'
    }
}).then(([movie, created]) => {
    console.log(true)
    console.log(movie);
})
```

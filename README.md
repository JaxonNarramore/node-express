# node-express

## Creating a package
npm init (more specific) or npm init -y (for basic settings)

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
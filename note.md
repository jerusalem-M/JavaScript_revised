JavaScript Essentials: Quick Reference1.

Script Loading: async vs deferThese attributes tell the browser how to handle external .js files without blocking HTML parsing.async: Download while parsing, execute immediately upon download. It interrupts the HTML parser. (Use for: Independent scripts like ads or trackers).defer: Download while parsing, execute only after the HTML document is fully parsed. (Use for: Scripts that rely on DOM elements).

2. Variable DeclarationFeaturevarletconstScopeFunctionBlock {}Block {}Re-assignableYesYesNoHoistingYes (as undefined)NoNoJavaScript// Prefer const by default, let if value changes
const userID = 5021; 
let loginAttempts = 0; 

3. Function BasicsModern JS uses three main styles. Arrow functions are the standard for most modern logic.JavaScript// 1. Function Declaration (Hoisted)
function getSquare(n) {
  return n * n;
}

// 2. Function Expression
const getSum = function(a, b) {
  return a + b;
};

// 3. Arrow Function (Concise, no 'this' binding)
const multiply = (a, b) => a * b;

4. CallbacksA callback is a function passed into another function as an argument. It ensures a specific bit of code doesn't run until a task is completed.JavaScript// The "Higher-Order" function
function fetchData(callback) {
  console.log("Fetching data...");
  // Simulating a delay
  setTimeout(() => {
    callback("Data received!");
  }, 1000);
}

// Executing with an anonymous callback
fetchData((message) => {
  console.log(message); 
});


JavaScript Arrow Functions
Arrow functions provide a more concise syntax and, more importantly, a different way of handling the this keyword compared to traditional functions.

1. Syntax Conversion
To convert a traditional function to an arrow function:

Remove the function keyword.

Assign the function to a variable.

Place an arrow => between the parameters and the body.

JavaScript

// Traditional
function sum(a, b) { return a + b }

// Arrow
const sum = (a, b) => { return a + b }
2. Concise Features
Single Parameter: If there is only one parameter, parentheses are optional.

const isPositive = number => { return number >= 0 }

Implicit Return: If the function is a single line, you can remove the return keyword and the curly braces.

const randomNumber = () => Math.random()

Anonymous Functions: Ideal for listeners or callbacks to keep code clean.

document.addEventListener("click", () => console.log("Click"))

3. Scoping of this
This is the most critical difference between traditional and arrow functions:

Traditional Functions: The value of this is determined by how/where the function is called. In many cases (like setTimeout), this loses its connection to the parent object.

Arrow Functions: The value of this is determined by where the function is defined. It inherits this from the surrounding scope (lexical scoping).

Example:
JavaScript

class Person {
  constructor(name) { this.name = name }

  printNameArrow() {
    setTimeout(() => {
      console.log(`Arrow: ${this.name}`) // "this" refers to the Person object
    }, 100)
  }

  printNameFunction() {
    setTimeout(function() {
      console.log(`Function: ${this.name}`) // "this" is undefined/global here
    }, 100)
  }
}


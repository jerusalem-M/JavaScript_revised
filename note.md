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




Hoisting in Simple Terms
Imagine you are reading a book. Usually, you have to meet a character on page 1 before you can understand what they are doing on page 10.

Hoisting is like JavaScript reading the whole book before you do. It finds all the "characters" (functions and variables) and moves them to the "Introduction" (the top of the code) in its own memory. This allows you to call a function on line 1, even if you didn't actually write it until line 50.

The "Short Note" Cheat Sheet
📌 JavaScript Hoisting Quick Reference
1. Function Declarations (The "Full" Hoist)

Behavior: Both the name and the function body are moved to the top.

Result: You can call these functions before they appear in the code.

Example: sayHi(); function sayHi() { console.log("Hi"); } ✅ Works

2. Variable Declarations (var)

Behavior: Only the declaration is hoisted, not the value.

Result: If you use it before defining it, you get undefined.

Example: console.log(x); var x = 5; ➡️ Output: undefined

3. Variables (let & const) and Arrow Functions

Behavior: They are technically hoisted but placed in a "Temporal Dead Zone."

Result: You cannot use them before they are defined.

Example: console.log(y); let y = 10; ❌ Reference Error


The "One-Way Mirror" RuleTo understand all scopes, remember this: You can look out, but you can’t look in.A function can see variables "outside" of itself (in the parent scope).The code "outside" cannot see variables tucked away "inside" a function or block.📌 JavaScript Scope Cheat Sheet1. Global ScopeWhere: Variables defined at the very top of your file (not inside any {}).The Power: They are "Celebrities." Everyone in your entire app (every file, every function) can see and use them.The Risk: Dangerous for big projects because different files might accidentally use the same name and overwrite each other.2. Module ScopeWhere: Only active when you use <script type="module">.The Power: They are "Local Celebrities." Every function inside that one file can see them, but other files cannot.The Use: This is the modern standard. It keeps files from "talking" to each other unless you specifically allow it.3. Block Scope (let and const)Where: Anything inside curly braces { }. This includes if statements, for loops, and even just naked braces.The Power: Variables are "Prisoners" of the block. They cannot escape the { } they were born in.The Use: Keeps your code predictable.4. Function Scope (var)Where: Inside a function () { }.The Power: var is a "Houdini." It can escape if statements and loops, but it cannot escape a function.The Risk: Very confusing. It’s the reason most developers avoid using var entirely.Summary ComparisonScope LevelCreated ByVisible To...Use LevelGlobalTop of fileEntire AppAvoidModuleTop of module fileEverything in that fileHighBlock{ } (if, for, etc.)Only inside those bracesHighFunctionfunctionOnly inside that functionRare (var)One last tip: Variable ShadowingIf you name a variable name in the Global scope and another variable name inside a Function scope, JavaScript will use the one closest to where the code is running. This is called "Shadowing"—the inner variable hides the outer one.



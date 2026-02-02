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


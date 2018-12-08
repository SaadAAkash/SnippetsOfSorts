# SnippetsOfSorts [![GitHub license](https://img.shields.io/badge/license-GLWTPL-blue.svg)](https://github.com/me-shaon/GLWTPL/blob/master/NSFW_LICENSE) [![Coverage Status](https://img.shields.io/badge/coverage-100%25-yellow.svg)]() [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)]() [![first-timers-only Friendly](https://img.shields.io/badge/first--timers--only-friendly-blue.svg)](http://www.firsttimersonly.com/) [![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://github.com/SaadAAkash/Compiler-Linux-GIT-AWS-Essentials/graphs/commit-activity) [![Open Source Love svg1](https://badges.frapsoft.com/os/v1/open-source.svg?v=103)](https://github.com/ellerbrock/open-source-badges/) [![made-with-love](https://img.shields.io/badge/Made%20with-Love-1f425f.svg)](https://saadaakash.bitbucket.io/)
Scripts for boring stuffs. Snippets for teasing brain-cells. That's it.

## JavaScript

#### Short-Circuit Evaluation 

 
  ```
  var a;
  var b = null;
  var c = undefined;
  var d = 4;
  var e = 'five';
  var f = a || b || c || d || e;
  console.log(f);

  //Output: 4 , since the 6 falsy values in JS are false, 0, “” (empty string), null, undefined, NaN (Not A Number)
  ```

#### == vs ===

  ```
  3 === '3' // Output: false (Number compared to String) -> Strict Equality
  3 == '3'  // Outpt: true -> Loose Equality: Allows to convert the values into a common type
  ```

#### null, undefined and NaN

  ```
  null == null
  undefined == undefined
  null == undefined
  //all returns true: null and undefined are only equal to themselves
  NaN == null
  NaN == undefined
  NaN == NaN
  // all returns false: 
  NaN isn’t equivalent to anything (not even itself!):
  ```

#### Function Scoping & Block Scoping (var, let, const)

In short,

<img src="https://cdn-images-1.medium.com/max/1600/1*SntGwD7Wfd2v0S7aPybdzg.png" data-canonical-src="https://cdn-images-1.medium.com/max/1600/1*SntGwD7Wfd2v0S7aPybdzg.png" width="800" height="400" />

Credits: https://medium.com/@mayashavin

 ```
 function testMe(){
   while(true){
      let x = 2;
      break;
   }
   console.log(x); //ReferenceError: x is not defined
}
 ```
 
 ```
 var x = 1;
 {
   let x = 3;
 }
 console.log(x); //Output: 1
 ```
 
 ```
 var x = 5;
 let y = 4;
 console.log(this.x); //5
 console.log(window.x); //5
 console.log(this.y); //let doesn’t create a property on global object
 console.log(window.y); //same reason
 ```
 
####  Hoisting

 * Moves all the declarations to the top of current scope 
 * Hoisting only applies to declarations, not assignments
 * Variable Hoisting doesn’t apply to ```let```, means during compile phase, ```let``` declaration will stay where it is and will not be processed first among other code , will not move to the top of context like ```var```

 ```
 var x = 0;
 y = 1;
 console.log(sumOf(x,y));
 var y;
 function sumOf(a, b){ return a + b; }
 ```
 will be processed as:
 ```
 var x;
 var y;
 function sumOf(a, b){ return a + b; }
 x = 0;
 y = 1;
 console.log(sumOf(x,y));
 ```
 
#### Function Declaration, Function Expression & IIFE (Immediately Invoked Function Expression)

* A small note: A child function can access to its parent function's variables, function & objects
 * Function Declaration:
 ```
 function mult(p1, p2) {
     return p1 * p2;
 }
 alert(mult(4, 3));
 //12
 ```

 * Function Expression:

 ```
 let mult = function(p1, p2){
     return p1 * p2;
 }
 alert(mult(4,3));
 //12
 ```
 
 * Function Expression (using arrow func of ES6):

 ```
 let mult = (p1, p2)=>{
     return p1 * p2;
 }   //OR, let mult = (p1, p2)=> p1 * p2;
 alert(mult(4,3));
 //12
 ```

 * IIFE:
  * A function expression followed by () which tells the JavasScript compiler to invoke or call immediately
  * Any variables declared inside the IIFE are not accessible from the outside world.
  
 ```
 (
 function(p1, p2){
     return p1 * p2;
 }
 )();
 //12
 ```
 
  * IIFE with Arrow ES6:
 
 ```
 (
 ()=> alert(2 * 3)
 )();
 //12
 ```
 
 #### Closure
  
  * A closure is the combination of a function and the lexical environment within which that function was declared
  * In simpler words, a child function can access its parent function's var,func & obj even after parent function has been returned and Closure enables this access. These var, func & obj are stored in a reference to its lexical environment.
  
  ```
  function makeFunc() { // parent function
    var name = 'Mozilla';
    function displayName() {  //child function: uses a parent function variable, name
      alert(name);
    }
    return displayName;
  }

  var myFunc = makeFunc(); //var myFunc is a reference to the instance of function displayName()
  myFunc();
  // this code works since displayName() maintains a reference to its lexical environment, within which the var name exists
  //Ref: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures
  ```

#### Call, Apply, Bind

 * call() and apply() serve the exact same purpose. The only difference: 
   call() : parameters are passed individually
   apply(): parameters are passed as an array
 * bind() method creates a new function, call()/apply() doesn't make a copy of the fucntion, they just execute the function right away with the params
 
 ```
 var pokemon = {
     firstname: 'Pika',
     getPokeName: function() {
         return this.firstname;
     }
 };

 var pokemonName = function(snack, hobby) {
     console.log(this.getPokeName() + 'I choose you!');
     console.log(this.getPokeName() + ' loves ' + snack + ' and ' + hobby);
 };

 var logPokemon = pokemonName.bind(pokemon); // creates new object and binds pokemon. 'this' of pokemon === pokemon now

 logPokemon('sushi', 'algorithms'); // Pika Chu  loves sushi and algorithms

 pokemonName.call(pokemon,'sushi', 'algorithms'); // Pika Chu  loves sushi and algorithms

 pokemonName.apply(pokemon,['sushi', 'algorithms']); // Pika Chu  loves sushi and algorithms
 ```

#### ```this``` is ```new```

 1. If ```apply``` or ```call``` or ```bind``` is used to call a function, ```this``` inside the function is the object that is passed as the argument
 2. If the ```new``` keyword is used to call the function, ```this``` inside the function is a brand new object.
 3. If a function is called on an object, ```this``` inside the function is the object.
 4. If a function was invoked without any of the conditions above, ```this``` is the global object (In a browser, it’s ```window```)
 
 ```
  var obj = {
     siht: "this is siht"
 };

 function myFun() {
     return this // What is `this` here?
 }

 obj.fun = myFun;

 console.log("this is window:", obj.fun() == window); // false
 console.log("this is obj:", obj.fun() == obj); // true
 //rule3
 ```
 
  ```
  function ObjConstructor(name) { 
  this.name = name;
     console.log(this);
 }
 var obj1 = new ObjConstructor('Saad Ahmed Al Jubaer Akash'); // now, this is obj1: rule 02
 ObjConstructor('Saad Ahmed Al Jubaer Akash'); // now, this is window : rule 04
 var obj2 = new ObjConstructor('Saad Ahmed Akash'); // now, this is obj2: rule 02
 //rule2: if new is used, function is a brand new object
 
 Output:
 ObjConstructor {name: "Saad Ahmed Al Jubaer Akash"}
 Window {postMessage: ƒ, blur: ƒ, focus: ƒ, close: ƒ, frames: Window, …}
 ObjConstructor {name: "Saad Ahmed Akash"}
 ```
 
 ```
  function myFun() {
     return this; // What is `this` here?
 }
 var obj = {
     someData: "a string"
 };
 console.log("this is window:", myFun.call(obj) == window); // false
 console.log("this is obj:", myFun.call(obj) == obj); //true
 //rule1
 ```
 
 * Two tricky snippets:
 
 ```
 var obj = {
     myMethod: function () {
         return this; // What is `this` here?
     }
 };
 var myFun = obj.myMethod;
 console.log("this is window:", myFun() == window); // true
 console.log("this is obj:", myFun() == obj); // false
 ```
 Here, ```this``` is the global object (or, window) because myFun/obj.myMethod is not called on an object (rule 4)
 
 ```
  function myFun() {
     return this; // What is `this` here?
 }
 var obj = {
     myMethod: function () {
         eval("myFun()");
     }
 };
 ```
 Here, again ```this``` is the global object (or, window) because myFun is not called on an object (rule 4)




## Python

* [CSV to JSON](https://github.com/Interspeed/CSVtoJSONPy)
* [HTTP Server One Liners](https://gist.github.com/SaadAAkash/d8e9ef3fcdd5040d1ba8981bdf43bab3)
* [YouTube Sentiment Analysis](https://github.com/realpython/python-scripts/blob/master/scripts/31_youtube_sentiment.py)
* [Some more interesting ones](https://github.com/realpython/python-scripts/)

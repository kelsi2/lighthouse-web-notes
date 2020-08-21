# Callbacks

[See lecture notes and code here](https://github.com/tborsa/lectures/blob/master/week1/day4/notes.md)

## Topics Covered
  ### Functions as values
  ### Anonymous functions
  ### Function calling vs. passing (reference to a function)
    * Why they exist
    * Implementing our own forEach and/of our own filter
  ### Arrow functions (and common use for callback functions)
  ### Nested scope and "scope chain"

  1. Functional declaration 
  ```javascript
  function howdy(){
  console.log("hey there pardner");
}
```
  * Can call this before it is declared (hoisted)
    * Not good practice to use things before they are declared, can be confusing to people reading code
    * This is not a practice across other programming languages so can be confusing for those not familiar with javascript
  2. Functional Expression
  ```javascript
  const howdy = function(){
  console.log("hey there pardner");
}
```
  * Not hoisted, must be declared before using
  * Variable which contains an anonymous (unnamed) function
  ```javascript
  function(){
  console.log("you can't call me");
}
```

    * Anonymous function CANNOT be called. A functional expression, even though it contains an anonymous function, is not an anonymous function itself since it can be called with the variable name
      * Anonymous functions are only used if you never need to call them again
  3. Arrow Functions

  ```javascript
  const howdy = () => {
  console.log("hey there pardner");
}
  ```
  * Remove "function" and replace with arrow after params (same as functional expression but using arrow syntax)
  * Not hoisted

### Callbacks
* A function passes as a parameter (object) to another function

```javascript
let classes = [
  {name: 'wizard', primaryAbility: 'intelligence'}, 
  {name: 'barbarian', primaryAbility: 'strength'}, 
  {name: 'bard', primaryAbility: 'charisma'}, 
  {name: 'rogue', primaryAbility: 'dexterity'}, 
  {name: 'druid', primaryAbility: 'wisdom'}
];

let printClassDetials = (class) => {
  console.log(class.name + ' primary ability is ' + class.primaryAbility);
};

classes.forEach(printClassDetails);
```

* Higher order function
  * Higher order functions are any functions which operate on other functions (includes but not limited to functions which take in functions [callbacks] as arguments)
    * Includes built-in functions like forEach, filter, map, etc.
    * Major part of Functional Programming
  * Pass 1 parameter which should be a function (callback, can be called anything)
  * forEach() is a callback function (we are executing a given function for each given parameter)

* Callbacks allow us to adjust functions and how they behave so they become more flexible
  * We can prevent repetition and reuse functions with new behaviour

* process.stdout.write() forces output to print horizontally rather than vertically

* process.argv is always a string so must be converted to number to compare to ocean variable (use == instead of === to do automatic type conversion)
  * To make process.argv not 0 indexed (e.g. 5 displays as 5 instead of 6), write process.argv[2] - 1

### Nested Scope and "Scope Chain"

* Scope = set of variables accessable from function or block of code

```javascript
  let weather = 'sunny';
  let indoorActivity = 'play starcraft';
  let outdoorActivity = 'climb';

  if (weather === 'sunny') {
    // For this code the variables in scope are [weather, indoorActivity, outdoorActivity]
    console.log("you should " + outdoorActivity);
  } else {
    console.log("you should " + indoorActivity);
  }
  ```

* Global variable: Defined in root of document, outside functions, can be accessed by all code in the file
* Local variable: Defined within a function and can be used by any code inside that function

```javascript
  let weather = 'sunny'; // global scope

  const decideWhatToDo = (weather) => {
    let indoorActivity = 'play starcraft'; // local scope
    let outdoorActivity = 'climb'; // local scope
    if (weather === 'sunny') {
      console.log("you should " + outdoorActivity);
    } else {
      console.log("you should " + indoorActivity);
    }
  };

  decideWhatToDo(weather);
  ```

* If an identifier is not found in local scope the search continues up the scope chain through other local scopes it has access to and finally global scope
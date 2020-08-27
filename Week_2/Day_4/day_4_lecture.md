# Promises

## Topics
 ### Intro to Promises
 ### Sequencing of async tasks without "callback waterfall" (callback hell) problem
 ### Error handling with Promises (vs. callbacks)
 ### Optional: Parallelizing async things (Promise.race and Promise.all)
 ### Optional: History of promises in JavaScript

[See notes and code here](https://github.com/tborsa/lectures/tree/master/week2/day4)

* Promises: a way to handle asynchronous things in JS
  * Promises and callbacks are interchangeable

### Callbacks: 
  * Function that is passed as a parameter
  * Helper function you wait to use
  * Can return a value but don't typically (esp. when used asynchronously)
  * Asynchronous
    * Happens simultaneously (JS does one thing at a time, but the OS can make progress on other things)
    * Executes after code has run
    * Anology: Like McDonalds, completed orders can still be delivered while waiting for other orders to be completed (e.g. if a coffee is ordered it can be delivered even through the big meal ordered first hasn't been delivered yet)
    * Non blocking
    * runs code we can complete without waiting for code we can't
  * Advantages
    * Code is more modular
    * Only way to handle async code
  * Disadvantages
    * Confusing to write
    * Susceptible to callback hell
      * Ex. survey (many async things to do in order risks callback hell [nested callback inside nested callback, etc.], forcing synchronous execution)

### Promises
  #### Promise in General
  * a vow that you will do something
  * Something that is intended to be done
  * You can fulfill or break a promise
  * Commitment based on trust (a belief that something will happen)
  * Time element involved (do something in the future, not happening immediately)
  * Agreement between one or more parties
  #### Promises in JS
  * Promises are always asynchronouse, waiting for something to be resolved or rejected
  * Three states:
    * Pending, fulfilled, rejected
      * Always starts pending then moves to either fulfilled or rejected
      * Pending result = undefined
      * Fulfilled result = value (The something that was meant to be done)
      * Rejected result = error (Promise has not been completed or has been failed, so the result is the lack of the promise being fulfilled)
  * Some libraries (like readline) don't use promises. These must be included in the program to be used (check the docs for promises!)
    * Can use readline-promises (a seperate module)
  * Need a listener to see if a promise has been fulfilled or not
    * .then() after the code running a promise
      * Best practice to run .then on a seperate line (either tabbed in or run as const name.then())
      * .then needs to include a callback:
      ```javascript
      .then((result) => {
        console.log('the user inputed ', result);
        rl.close();
      })
      ```
      * result = value of resolved promise
      * still similar to using callbacks!
    * Can also use .catch()
      ```javascript
      prom.catch((error) => {
        console.log("something went wrong)
      })
      ```
    * Can also chain methods (.then()... .catch())
    * .then is only run on success of promise, .catch is only run if promise is rejected/fails or if there is an error in the handlers
  * Second question needs to be run inside the first .then() use return, then can chain another .then
    **SEE CODE EXAMPLES**

* Unlike with nested callbacks, .then will not store values from previous .then blocks
  * One way around this is to push all values to an array that we can then return

* Can return any promise or value from a .then, doesn't need to be the previous/current promise
  * Returning a value makes the chain a bit more complicated because that value will be returned and the flow of promises will be broken (e.g. if we return 5 for question three instead of the next question that will be returned without asking the question, 5 will be added to the array and the next question will automatically be asked)

* If not using .catch and the promise fails we will get an error (the code won't run)

* When using promises with fs: const fs = require("fs").promise
**SEE NOTES FOR PROMISES VS. CALLBACKS**

SUMMARY: 
* Whatever is returned in one .then will be picked up by the next .then...it is a chain!
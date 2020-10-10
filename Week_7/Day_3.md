# Data Fetching & Other Side Effects

## Topics

### Run multiple servers

### Handle component side effects

### Data fetching with React

### Compute values from existing state

[Notes and code here](https://github.com/andydlindsay/aug172020/tree/master/w07d03/use-effect)
[Lecture here](https://us02web.zoom.us/rec/play/J5s7uN96VI4j1GUfVWBLB6EOdeGUrMOsmqdKRFqGts_JJjYtUDEigJFngRNaY9E6cOgZncvzWrR_0V_N.kXHhL4kTeWfklOJQ?startTime=1601482929000&_x_zm_rtaid=ho568h8WTUuvtLfhnMFsdw.1601500046514.324988d4c6953f67a17efc2070b9681e&_x_zm_rhtaid=662)

### Rules for Hooks

1. Can't use them conditionally (have to be top-level)
2. Can only be used in React functions
3. All hooks must start with 'use'

### Pure Functions

- Always returns the same result given the same inputs
- Does not produce side effects

* Not side effects:
  - Return
  - Updating the state

### Side Effects

- An operation that modifies the state of the computer or interacts with something outside of your function/application

- console.log (aka writing to standard out) => Does not need to go in useEffect (only side effect that gets this pass)
- Modifying the DOM directly
- Establishing a socket connection
- Retrieving data
- Setting timers and intervals

* Creating a closure
* useState (does not need to go in useEffect because it is a hook)

- Anything identified as a side effect needs to be INSIDE a useEffect hook

  - document.title goes in a useEffect hook
  - May not always see the problems from not using useEffect hook immediately but this can have an impact we are unaware of
    - Without a useEffect hook some side effects are called more than once which means the page needs to rerender multiple times

  * Can have an unlimited amount of useEffect hooks

* setInterval will run on forever. We need a second cleanup function with clearInterval and return that (needs to be in a function so it doesn't immediately clearInterval before it runs)

* We don't want our interval to be fired every time, this will really slow down our pages, especially if we call an api
  - By default useEffect runs every time a page renders
  - To avoid this we can use a dependency array at the end of useEffect which says only call this useEffect if values in this array change, otherwise ignore it
    - We can also listen for a specific piece of an array or object as well, rather than the whole object

### Data Fetching

- Main use for useEffect
- Use Ajax requests to retrieve data from an API => This is a side effect so needs to go in useEffect!
- Need to import axios and use that to make a get request

  - Start with an empty array in useState so we can use map (cannot use null because it needs to look how the final state will be [array, object, string, etc.])
  - Axios is purely for Ajax (jQuery has a lot of other options so gets bulky, Axios only does one thing)
  - DO NOT USE FETCH => has CORS issues
  - Use .then((response) => {set<value>(response.data)}) within useEffect get request
    - This is an async infinite loop!!
    - Can use an empty dependency array to make sure the useEffect is only called once when the page is loaded, it will never be run again so we are not making multiple api requests
  - Be sure to have keys for each piece of info

- Can use one useEffect group to make all api requests using a promise.all (since they are not dependent on eachother, one does not need to fire first)
  - This way we still only need to return one response with all of the data in an array

### useEffect Flow

- React renders UI => Browser displays UI => Cleanup for previous effects if any => Run effects for current render => Back to beginning of loop
  - e.g. cleanup is not done until after new loop is run and rendered

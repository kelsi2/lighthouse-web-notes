# Immutable Update Patterns

## Topics

### Components and State Management

### Immutable Update Patterns

- Rationale
- Approach
- ES6 Syntax

- State stored in client application === type of cache
  - As interacting with API need to keep cache in synce
  - Using immutable update patterns can change state on client piece by piece
  - Need immutable update patterns for objects and arrays, difference between mutation and cloning of objects
    - Working towards writing reducers (tomorrow)

[Notes and code here](https://github.com/tborsa/lectures/tree/master/week7/day2)

### State (in React)

- State === Data
- Way to track information (hold onto it or remember it)
- Makes components smart not dumb!
- Monitor state to make decisions on when to re-render
- Current state of data
- Passed down as props (can only be passed down, not up)
- Set and retrieve state in reat with HOOKS (useState)
- Remembered information about a system + useState, Reacts confention for tracking state
  - New value of state is created every time component runs and renders
  - Each prop and state is for a particular functional component execution, remain the same throughout that render

### State as a Concept

- Remembered information about a system

### Demo

- If there is no state change the JSX will not be re-rendered even if the value of a component changes

  - useState allows React to know that the state of a component is changing

- State should be declared as a const (best practice)

- Must use set<variableName> to change the actual state value (can't just say +=1 to the value because this won't change the state)
  - We are not changing the actual plantSize value but rather the state of that value that React stores. The original value remains the same regardless of how many times the function is run
  - State is a snapshot/picture of the data at that exact moment, it's not a permanant change BUT the state will always be the same under those exact circumstances (first time function is run, second, third, etc. will always have the same results)

* When you call setState react is comparing the currentState against the newState, if they are the same it doesn't rerender so the function doesn't run again and our state doesn't actually get changed
  - We should never alter the original value directly!!! This will cause the current and new state to be the same, we need to make a true copy and change that
  - This way the copy is different from the original value

### Immutable Update Patterns

- To make a deep copy (that we can edit without changing the original) we can use spread or map
  - Using spread we can do:
  ```javascript
  const newState = [...currentState, "new"];
  ```
  - Now the newState and currentState are different and we can change one without impacting the other
  - We are not mutating the original state

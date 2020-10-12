# Class-based Components

### Classes & OOP
### Class-based components in React
### Syntax
### Important Lifecycle Methods
### Pros and Cons
### Trends with Class-based Components in React

* Import React { Component }, then class xxxxxxx extends Component
  * This allows the class to contain everything the Component object contains (including render)

* Use a constructor, this is the same as passing in props
  * constructor(props { super(props) }) <--this includes props from Component
  * Problem is this is a function so props are outside scope everywhere else
    * Use this.props (accessing global scope) then props is defined

* To track state, include this.state = { likes: 0, dislikes: 0 }
  * To access use this.state.likes

* Writing method so don't need to include "function"
  * Need to use this.handleClick to call it, this will result in undefined
  * Need to bind this in constructor for it to work and change state as we need
    * this.handleClick = this.handleClick.bind(this)

* There is always a function to set state, don't alter it directly
  * this.state.likes = this.state.likes + 1 <-- This is the WRONG way!!
  * this.setState({ likes: this.state.linkes + 1 }) <-- This is better
  * this.setState( prev => { likes: prev.likes + 1 }) <-- The RIGHT way to alter state, same way we do it in functional React
  * React will only alter state for the matching key, the other state will remain the same until altered

* To avoid using bind, use arrow functions
  * This automatically binds like to the function state instead of global state

* Hooks are optional so you can mix hooks with class-based code, don't need to use 100% one or the other

* Lifecycles are like useEffect
  * componentDidMount() {  } <-- This checks if the component rendered once (like useEffect with [] at the end)
  * componentDidUpdate() {  } <-- Checks if the component re-rendered (like useEffect with no [])
  * componentDidUpdate(prevProps, prevState) { if (prevState.dislikes !== this.state.dislikes) {...}} <-- Changes only when the dislikes state is changed (like useEffect that is tracking a specific state like [dislikes])
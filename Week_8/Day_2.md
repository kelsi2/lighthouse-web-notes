# Real World React (Advanced Topics)

## Topics (2-3 will be covered, inspect others alone)

### React Router

### Styled Components

### useContext

### useRef

### Reducers

### Class-based Components (legacy React)

### CI & CD

### Deployment of React Apps (Heroku and Netlify)

### Resources to continue learning React

[Code here](https://github.com/tborsa/react-next-steps/tree/2020oct6/src)
[Bonus repo: Web sockets](https://github.com/tborsa/LighthouseLabs/tree/master/lectures/Week6/Day4/Lecture)

Notes and links from Travis below

## Next Steps for React

- Review Scheduler
  - Make a component diagram (hierarchy, how state is passed)
- Readings (useEffect article)

## New Things

- New React hooks

  - useRef (refs)
  - useReducer (when to use vs. State)
  - useContext (context)

- React libraries (be careful bringing these in and make sure they're supported, the following are very common and well adopted. They should serve a specific purpose, not a lot of purposes because the quality is bad)

  - Redux
  - Styled components
  - Material UI
  - React-Spring
  - React Router
  - Preact

- React CLI

- JSX Linting

- React patterns

  - Lifecycle

- Testing
  - Webdriver

## React Hooks

- useMemo and useCallback don't really have any additional value, not used very often
- useEffect: component => render => useEffect (runs after the first render)

### useReducer

- Not a huge leap from useState to useReducer but makes things more organized and clear
  - Only using a different hook
  - Less logic required
  - Automatically looking at the most recent state, no stale state so no need for setState(prev)...

### useRef

- Attach a handle to a dom element
- DO MORE RESEARCH ON THIS

### useContext

- createContext from react
- Import context into component file to create a context that can be shared between multiple files
- Can override default static value using Provider hook from context file in app.js
  - This allows us to use state to create a dynamic value that can be changed with onClick (or another type of event)
  - When you change the state in one file it will also update the other components using the same context (the state changes in both)

## React Patterns

### Lifecycle

- Deals with class-based components (old React)
  - Not very important now because React is moving towards functional components, this is backwards
- willMount => render => didMount => willUpdate => render => didUpdate
- Don't spend time learning this unless needed, other topics are more important

## React Libraries

### Redux

- Solving same problem as context
- Helps to manage global state
- Existed before functional components and useContext
  - React learned from this library to implement this
  - Redux is far more involved so is still used
- Best to use useContext in most cases so you don't have to increase the project load, you can do it within react

### Styled Components

- Bind component to a css style
- Add css within a jsx file
- Basically creating a variable with styles
- Can pass props to customize the style for that prop

### Material UI

- Library of components you can import (like navbar, dropdown menu, etc.)
  - Good if you just want working components, don't want to spend time on design
- Also Ant Design
- Bootstrap for React, but also includes functionality

### React-Spring

- Animation library

### Preact

- Write components like React but very stripped down and lightweight

### React Router

- Allows us to have front end routes for React
  - SPA like scheduler always defaults to the same part of the page (e.g. Monday)
- React Router allows for loading different content/paths without reloading the page
  - Merge routes with SPA
- Initialize in root component (usually app.js)
  - npm i and import {BrowserRouter as Router, useRouteMatch} react-router-dom
  - Wrap BrowserRouter around project (renamed to Router for ease of use)
    - Anything inside component has access to react router tools (routes, links, swtiches, etc.) -> will error if outside Router
- use <Route path=<path>> to create a page (anything within these tags will only be rendered if it matches the path in URL)
  - Even if there is more to the url after it will still render the same page (can use exact to force it to only load that page on that exact route)

* Can use a <Switch> to load different components under different circumstances (different url paths)
  - Can also create a default load (like 404), like a normal switch statement
* How to link?
  - Normal anchor tags cause problems because it renders the page again (we are trying to avoid refreshing the page)
  - Another component to use to solve this problem: <Link to>
    - Overrides the refresh but still allows navigation between different routes
    - Can use paramaters similar to Express (check for value in component with react-router-dom useParams hook)
      - const <name> = useParams() allows you to use variables in the url
      - Log value of useParams() to find out what is being returned

## React Native

- Build react apps for mobile

----------------------------------
Real World React (Advanced Topics)
----------------------------------

****************
React Next Steps
****************

Hey Everyone,

Today we covered a lot.

Remember the first 'next steps' for you should be to review the
work you have done with react so far and brush up on some of the
concepts you know. Dan Abramov has some great articles on react
in particular this one 
( https://overreacted.io/a-complete-guide-to-useeffect/ ) helped a
lot with my understanding of functional react.

Try to think of the other content we covered in lecture as an
exploration of things possible with react. Less a tutorial on how
to use those things.
The project we made together can be found here 
( https://github.com/tborsa/react-next-steps/tree/2020oct6/src )

Also here Notes and code here 
( https://github.com/tborsa/LighthouseLabs/tree/master/lectures/Week6/Day4/Lecture )
 is a link to the react lecture on websockets I mentioned.

We looked at (links included):

* new hooks 
( https://reactjs.org/docs/hooks-reference.html#usecontext )

* useContext
* useRef

* React Router 
( https://reacttraining.com/react-router/web/guides/quick-start )

* Router
* Params
* History
* Switch

And talked about:

* Redux ( https://redux.js.org/introduction/getting-started )

* React Component Lifecycle 
( https://reactjs.org/docs/state-and-lifecycle.html )
and this 
( https://medium.com/@divyabiyani26/react-useeffect-a-hook-to-introduce-lifecycle-methods-in-functional-components-e7ec52897188 )


Some other things you may find interesting:

* React component libraries/ react libraries

* component libraries for stylized UI
* component libraries for functional specific things
* examples Material UI ( https://material-ui.com/ ), Ant design 
( https://ant.design/ )

* React Native 
( https://facebook.github.io/react-native/docs/tutorial )
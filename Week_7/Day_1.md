# Component-Based UI w/ React

## Topics

### ES6 features (object/array destructuring, spread, property shorthand)

### Convert interface designs to component-based UI

### Create project with Create React App

### Build components in isolation with Storybook

### Using components in an application

[Notes and code here](https://github.com/andydlindsay/aug172020/tree/master/w07d01)
[Lecture here](https://us02web.zoom.us/rec/play/Zj1CE0jGXJGfNjunT4y59DzvNP_g-k1wPgVy2cD8xvImuWWUORqte1-1chVi5C64uPM7_RQJmMBS4K0i.hgK5teFkonyQSlou?startTime=1601310153000&_x_zm_rtaid=fwwCxKlSQeKGK_vKyRtS1A.1601330806831.f91bad428a8455209e9e9ec39f69d6f2&_x_zm_rhtaid=984)

**Learning Functional React NOT class-based React**

- Hooks released in Feb 2019 which can preserve data between function calls

- When a function runs variables are created and everything runs but when it finishes everything is discarded...we get a new i each time it gets run so we can't increment it
  - We need to use a closure. Variable needs to be declared in global scope instead of in the function so it can be incremented

### What is React?

- Library
- Declarative framework - What not how
- Developed by Facebook
- Most popular of top three JS frameworks (Angular, Vue)
- Component-based - small reusable pieces of the DOM

  - One component that can be called anywhere in the application (like one button that can be reused as needed for example)

- npx ensures we get the latest version of the package

  - No need to install globally, only within the project folder, this only needs to be done once

- Will now have more than one server running (front end, back end, etc. We are now professional devs!!! Laptop will always need to be plugged in from now on)

- Public === static components
- The entire app lives inside div id="root (everything in that div belongs to react)
- noscript only runs if JS is turned off (in this case basically says turn on JS)

- StrictMode in react will highlight problems more evidently with good error messages and is invisible when the app is rendered
- In this situation we don't want to import jQuery because it uses too much space when we would only use it once to call root (so we just use vanilla JS, document.getElementById('root'))
- webpack allows us to use import instead of require, import cannot be read by node normally

- Must have only one parent element to wrap everything
  - Use a div for this (We do not want to target body...this is BAD PRACTICE!)
- If using JSX we must import react

- React doesn't care whether we use js or jsx

  - Best to use jsx for components to be clear what is in the file, otherwise use js
  - Andy's personal convention...use whatever employer wants

- Default name of component is capital of whatever file is called
  - All components are functions
- Must export component (use export default so you don't need to import an object destructure)
  - Only one component per file
- Components can be imported and used as many times as we want, they act like function calls

**State === data**

- React is hungry for STATE

  - It needs to know what data is in the application so it knows what to do with it
  - React doesn't know about outside variables so it doesn't know to update it
    - JS could be incrementing but not displaying it because React doesn't know
  - useState will tell React how to handle state (creates a closure react knows about)
    - can import in react statement or do React.useState in functionn
    - Use array destructuring and put in the default value (in this case 0 since we want counter to start at 0, this can also be a string if we want)
    - Value should not be directly reassigned!!! Should not be doing count = count +1
      - We need to use setCount(count + 1) => like a getter and setter in classes!!
  - When React knows about our state it can re-render our component

- Props are state that come from somewhere else, we can call props as a parameter in our function definition

  - Then we call them like an object (props.<keyName>)
  - Can also refer to anything defined between opening and closing tags as props.children

- Fragment can act as a container (parent) that does not output to the Dom like a div does
  - Everything in that fragment is not top level instead of being nested in a div which makes the dom much easier to read
  - Can also use <> </> BUT this does not work in all browsers
  - div can be styled where fragment cannot since it's not actually attached to the dom
  - Best practive varies by team

* Storybook allows for styling seperately from other components
  - Very difficult to style components that are nested in other styles due to inheritance
  - Storybook lets us style just that individual component without inheritance so we know exactly how it will look

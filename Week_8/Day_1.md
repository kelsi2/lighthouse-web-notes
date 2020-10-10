# Unit & Integration Testing

## Topics

### Types of tests

- Static
- Unit
- Integration
- End-to-end

### Choose a test for the code being tested

### Layers of test helper libraries

### API React Testing Library

### Mock functions to isolate components for testing

### Coverage reports to reveal uncovered code when we run tests

### What makes a test asynchronous

[Lecture and notes here](https://web.compass.lighthouselabs.ca/activities/1041/lectures/4088)
[Code here](https://github.com/vasiliy-klimkin/lhl-lectures/tree/master/w08d01-Unit-Integration-Testing)

## Why do we test?

- Gives us more confidence that the code works
- Bugs are EXPENSIVE!
- Want to catch bugs before production so it doesn't crash
- Keeps us on track
- Can sleep at night!! <-- Important!!
  - Never deploy on a Friday! Everything goes bad so your weekend is ruined

## Types of Testing

- Static

  - Linting
  - Syntax
  - Names of variables
  - Code cleanliness
  - Cheap!!

- Unit

  - Test mechanics of a function
  - Cheap

- Integration
- Make sure different parts of the code work together
- Overall component test
- Mid-expensive

- End-to-end
  - Flow of the entire application
  - Does everything work together
  - Expensive+++

## React Testing Library

- For testing DOM nodes, tests components one by one
- import { render } from '@testing-library/react';

* Use prettyDOM to make the console logs readable

## Jest Dom Package

- Jest matchers for React
- We don't have to write these functions, they are provided for us
- import '@testing-library/jest-dom';

* Can create tests to check that the original code is still operating correctly (for example if text should be lower cased, write a test that text is still lower cased)

  - This prevents people from changing the code in ways that it shouldn't be changed

* You can run only one test by including the file path in npm run test

  - Can also press w followed by p to use regex to find the right file name

* Test sad path first, then happy path!

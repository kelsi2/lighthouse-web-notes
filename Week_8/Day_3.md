# End-to-End Testing with Cypress

## Topics
### Jest vs. Cypress
### Install and configure Cypress
### Design End-to-End tests with Cypress
### Write End-to-End tests with Cypress

[Notes and code here](https://github.com/hafbau/lecture_notes/tree/master/w8d3)

## Unit/Integration/End-to-End Testing
* Unit tests: Things work on their owns (one thing in siolation)
* Integration tests: Do the units work together (do kitchen drawers work together [can they all open and close when installed])
* End-to-End: Does the whole app work from start to finish, do all the pieces work together and flow with no errors

## Jest vs. Cypress
### Jest
* Unit/integration testing
* CLI based (terminal)
* Tests located within source code
* Tests are assertion based (expect...)
* Tests should be broken into pieces

### Cypress
* End-to-End or integration testing (can also be used for unit, but not as popular)
* Browser testing (very visual)
* Tests are adjacent (server is running so site can be tested as a user would run it)
* Test any website you want that is online (Google if you want!), don't need access to source code
  * Test user storie (user should be able to...)
* Using the Runs tab you can record your tests for debugging purposes and see exactly how a user would run your app
* Tests should be written in large chunks (each it block creates a new browser, so it's better to have a lot in one test)

* Integration folder has all tests
  * Tests written as .spec.js
* Write script in package.json to make command easier to write (It's ok to do this in a professional environment as well!!)

1. Create file for test category
2. Describe block for tests
3. Write tests using it("should...")
4. npm run cypress (unless already in watch mode, in which case this is automated)

* cy.visit("...") to go to the page you want to test
  * Can manipulate this like a normal web page (this is a fully operational dom)
  * Use inspect if you don't know what aspect to focus on when writing a test
* Can use beforeEach for page visit so you don't need to include this in each test
  * If you are doing the same things before each test you can put them in beforeEach but this is async! So be careful. Can give it an alias (.as("...")) and call the aslias at the beginning of each test instead of typing out the whole test section each time

* Can add delays to tests to simulate a real user (type delay: 150 so the system actually types the words)
* Can create variables in tests to ensure we are always testing consistently
* Can also simulate typos and backspacing! This helps us see what a user actually does when using the app

* Best to use data-...=... to select elements because this is unlikely to change